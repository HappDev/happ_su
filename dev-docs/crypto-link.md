# Crypto link

The application supports encrypted links. A link can be encrypted using RSA-4096. It is now recommended to use only RSA-4096, which is referred to as `happ://crypt3/`.\
Link encryption is designed to hide the subscription address from the user. After adding an encrypted subscription, the user cannot edit, view, or share the server configurations contained in the subscription. The encryption keys themselves are securely embedded in the application, ensuring the protection of subscription data.

***

You can encrypt a link in three ways:

1. Using this [web page](https://crypto.happ.su)
2. Using the [API](crypto-link.md#api-instructions)
3. Using [RSA key](crypto-link.md#rsa-key-rsa-4096)

#### API Instructions

To use the API, you need to send a request to the following address: `https://crypto.happ.su/api.php`

**Example:**

```bash
curl -X POST -H "Content-Type: application/json" -d '{"url":"https://your_url.com"}' "https://crypto.happ.su/api.php"
```

The result will return an encrypted version of your link, which can then be used in the application.

#### **RSA Key (RSA-4096):**

```
-----BEGIN PUBLIC KEY-----
MIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEAlBetA0wjbaj+h7oJ/d/h
pNrXvAcuhOdFGEFcfCxSWyLzWk4SAQ05gtaEGZyetTax2uqagi9HT6lapUSUe2S8
nMLJf5K+LEs9TYrhhBdx/B0BGahA+lPJa7nUwp7WfUmSF4hir+xka5ApHjzkAQn6
cdG6FKtSPgq1rYRPd1jRf2maEHwiP/e/jqdXLPP0SFBjWTMt/joUDgE7v/IGGB0L
Q7mGPAlgmxwUHVqP4bJnZ//5sNLxWMjtYHOYjaV+lixNSfhFM3MdBndjpkmgSfmg
D5uYQYDL29TDk6Eu+xetUEqry8ySPjUbNWdDXCglQWMxDGjaqYXMWgxBA1UKjUBW
wbgr5yKTJ7mTqhlYEC9D5V/LOnKd6pTSvaMxkHXwk8hBWvUNWAxzAf5JZ7EVE3jt
0j682+/hnmL/hymUE44yMG1gCcWvSpB3BTlKoMnl4yrTakmdkbASeFRkN3iMRewa
IenvMhzJh1fq7xwX94otdd5eLB2vRFavrnhOcN2JJAkKTnx9dwQwFpGEkg+8U613
+Tfm/f82l56fFeoFN98dD2mUFLFZoeJ5CG81ZeXrH83niI0joX7rtoAZIPWzq3Y1
Zb/Zq+kK2hSIhphY172Uvs8X2Qp2ac9UoTPM71tURsA9IvPNvUwSIo/aKlX5KE3I
VE0tje7twWXL5Gb1sfcXRzsCAwEAAQ==
-----END PUBLIC KEY-----
```

