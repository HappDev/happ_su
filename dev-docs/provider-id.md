# Provider ID

Provider ID is a unique identifier that links your subscription to an account on the website [happ-proxy.com](https://happ-proxy.com/). It provides access to advanced application usage statistics and allows accurate tracking of the number of active devices.

***

#### Where to Get Provider ID?

To obtain the Provider ID, you need to register on the website [https://happ-proxy.com](https://happ-proxy.com/)

After registration, you will be able to see it in the upper right part of the screen or in the user profile.

#### **How It Works**

Once a day, the application sends a GET request to:

```
https://check.happ-proxy.com/provider?id={ProviderID}
```

The request includes:

* **providerid** — your unique identifier;
* **domain hash**, from which the subscription is loaded;
* **HWID** of the device;
* **name and version** of the operating system.

The domain hash ensures that the ProviderID is tied to a specific subscription domain and prevents its use on other sites or in third-party subscriptions.

***

#### **Ways to Transmit ProviderID**

You can add ProviderID to the subscription in three ways:

1.  **In URL** (query parameter)

    ```
    https://your-domain.com/sub/123#?providerid={ProviderID}
    ```
2.  **In the Subscription Body** (comment)

    ```
    #providerid {ProviderID}
    vless://70cc48c5‑b2f4…
    vmess://zkIAU1JitkI…
    ```
3.  **In the HTTP Header** of the Response

    ```
    HTTP/2 200 OK
    date: Wed, 14 Apr 2025 10:00:00 GMT
    content-type: application/json
    content-length: 3798
    content-disposition: attachment; filename="213"
    providerid: {ProviderID}
    ```
