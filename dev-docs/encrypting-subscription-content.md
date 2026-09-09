---
hidden: true
---

# Subscription Content Encryption

Happ supports receiving encrypted subscription content. This allows providers to avoid transmitting server configurations in plain text between the backend and the application.

The **AES-128-GCM** algorithm is used for encryption.

#### General Workflow

When a subscription is requested, the backend must:

1. Retrieve the original subscription content.
2. Encrypt it using **AES-128-GCM**.
3. Return the encrypted content in the HTTP response body.
4. Return the GCM authentication tag in the `encrypt-tag` HTTP header.
5. Specify the identifier of the encryption key in the subscription URL using the `key` parameter.

Example URL:

```
https://vpn.com/sub/kjdsfkWr5jewk3rjew?key=key02
```

After receiving such a subscription, Happ determines which key should be used based on the value of the `key` parameter and decrypts the content.

***

#### AES-128-GCM Parameters

**Algorithm**

Use:

```
AES-128-GCM
```

The AES-128 key must be exactly **16 bytes** long.

**IV**

Use the following IV:

```
kkkkkkkkkkkk
```

The IV length is **12 bytes**.

The IV must be passed to AES-GCM exactly as the UTF-8/ASCII byte sequence of the string shown above.

**Authentication Tag**

AES-GCM encryption produces an authentication tag in addition to the ciphertext.

The authentication tag must be returned separately in the following HTTP header:

```http
encrypt-tag: <Base64 authentication tag>
```

The authentication tag must be encoded in **Base64** before being sent.

Example:

```http
HTTP/1.1 200 OK
Content-Type: text/plain
encrypt-tag: YWJjZGVmZ2hpamtsbW5vcA==

<Base64 encrypted subscription>
```

> The value above is provided only as an example of the expected format and is not a valid authentication tag.

***

### Key Identifier

The `key` parameter in the URL **does not contain the AES encryption key itself**.

It contains only the key identifier that Happ uses to determine which key should be used to decrypt the subscription.

For example:

```
?key=key02
```

***

### Temporary Test Key

You can use the Happ test key to verify your implementation.

**Key ID:**

```
key02
```

**AES key:**

```
key02:+]%4ij#P"/
```

This key has the required AES-128 length of **16 bytes**.

Therefore, the backend should perform encryption using the following parameters:

```
Algorithm: AES-128-GCM
Key:       key02:+]%4ij#P"/
IV:        kkkkkkkkkkkk
```

At the same time, the subscription URL must contain:

```
?key=key02
```

For example:

```
https://vpn.com/sub/kjdsfkWr5jewk3rjew?key=key02
```

***

### Backend Response Format

The backend must return the encrypted subscription and the authentication tag.

Example request:

```http
GET /sub/kjdsfkWr5jewk3rjew?key=key02 HTTP/1.1
Host: vpn.com
```

Response:

```http
HTTP/1.1 200 OK
Content-Type: text/plain
encrypt-tag: <Base64 authentication tag>

<Base64 encrypted subscription>
```

In other words:

```
Original subscription
        │
        ▼
   AES-128-GCM
        │
        ├── Ciphertext ──────────────► HTTP response body
        │
        └── Authentication Tag ─────► encrypt-tag header
```

***

### Testing the Implementation

To test your encryption and decryption implementation, you can use the Happ test page:

[https://crypto.happ.su/aes.php](https://crypto.happ.su/aes.php)

For testing, use:

```
Key:
key02:+]%4ij#P"/

IV:
kkkkkkkkkkkk
```

Encrypt some test subscription content and compare the result with your backend implementation.

For decryption, you will need:

* the encrypted subscription content encoded in Base64;
* the AES key;
* the IV;
* the authentication tag encoded in Base64.

***

### Important Notes

When implementing encryption, make sure the following requirements are met:

* the algorithm must be exactly `AES-128-GCM`;
* the key must be 16 bytes long;
* the IV must be `kkkkkkkkkkkk`;
* the authentication tag must be returned separately;
* the authentication tag must be Base64-encoded;
* the HTTP header containing the authentication tag must be `encrypt-tag`;
* the `key` parameter contains the **key ID**, not the AES encryption key itself;
* when using the test key, the URL must contain `key=key02`;
* do not append the authentication tag to the ciphertext if your encryption library does this automatically — Happ expects the authentication tag to be provided separately in the HTTP header.
