# Limited Links

<figure><img src="https://2249226147-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FpCCfn32zsHHBJZqih6C0%2Fuploads%2FJWfkSDtKT5VPOtKIqyit%2F3245.png?alt=media&#x26;token=1f64b54e-6441-4107-bff9-e39c84b71469" alt="" width="188"><figcaption></figcaption></figure>

Limited links is a feature that allows you to restrict the number of devices that can add a subscription (link) to the application.\
In your personal account on the `happ-proxy.com` website, you specify your subscription URL, set the maximum number of devices, and click "Generate link."\
The resulting link can be shared with a user, and you can be confident that the subscription can only be installed on the specified number of devices — exceeding the limit is impossible.

You can create limited links both through the web interface and via API.

**Creating via Website**

1. On the creation page, specify the **unencrypted URL** of your subscription.
2. Set the **installation limit** (maximum number of devices).
3. After generation:
   * The **InstallID** parameter is automatically added to the URL.
   * The link domain is stored in the database as a **SHA-256 hash** (raw domains are not stored to enhance security).

You will receive an **encrypted link** with the InstallID parameter.

***

**Creating via API**

Send a GET request to:

```
https://api.happ-proxy.com/api/add-install?
  provider_code={provider_code}&
  auth_key={auth_key}&
  install_limit={install_limit}
```

* **{provider\_code}** — your provider code (in your profile)
* **{auth\_key}** — authorization key (in your profile)
* **{install\_limit}** — maximum number of devices

**API Response**

*   **Success**

    ```json
    {
      "rc": 1,
      "msg": "Ok",
      "install_code": "6P0hVao1fG5e"
    }
    ```
*   **Error**

    ```json
    {
      "rc": 0,
      "msg": "Error description"
    }
    ```

Add the received **install\_code** to the link as the **InstallID** parameter.

***

**Example**

*   Original URL:

    ```
    https://url.com/sub
    ```
*   Final link:

    ```
    https://url.com/sub#Your_TITLE?installid=Abcd1234
    ```

> **Tip:** Encrypt the link so users cannot remove the InstallID parameter.

***

**How It Works**

When adding a link, the application calculates the SHA-256 hash of the domain and sends a request to:

```
https://check.happ-proxy.com/install?id={domain_hash}&installid={InstallID}
```

The response returns `ProviderID` and link status.

If the request fails to send (e.g., due to website blocking), the application will automatically retry after establishing a VPN connection.

The `happ-proxy.com` server receives the device's `HWID` and responds positively if the installation limit for the link has not been exceeded. If the limit is exceeded, the server returns a refusal and the application displays the message:\
\&#xNAN;**"The subscription administrator has restricted access. Please contact technical support."**
