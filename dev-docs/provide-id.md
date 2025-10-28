# Provide ID

Provider ID 是唯一标识符，用于将您的订阅与 [happ-proxy.com](https://happ-proxy.com/) 网站上的账户关联。它提供对应用程序使用高级统计数据的访问，并允许准确统计活跃设备数量。

***

#### 从哪里获取 Provider ID？

要获取 Provider ID，您需要在网站 [https://happ-proxy.com](https://happ-proxy.com/) 上注册。

注册后，您可以在屏幕右上角或用户资料中看到它。

#### **工作原理**

应用程序每天一次发送 GET 请求到：

```
https://check.happ-proxy.com/provider?id={ProviderID}
```

请求中包括：

* **providerid** — 您的唯一标识符；
* **域名哈希**，从中加载订阅；
* **设备 HWID**；
* **操作系统名称和版本**。

域名哈希确保 ProviderID 绑定到特定订阅域名，并防止其在其他网站或第三方订阅中使用。

***

#### **传输 ProviderID 的方式**

您可以通过三种方式将 ProviderID 添加到订阅中：

1.  **在 URL 中** (查询参数)

    ```
    https://your-domain.com/sub/123#?providerid={ProviderID}
    ```
2.  **在订阅主体中** (注释)

    ```
    #providerid {ProviderID}
    vless://70cc48c5‑b2f4…
    vmess://zkIAU1JitkI…
    ```
3.  **在响应 HTTP 标头中**

    ```
    HTTP/2 200 OK
    date: Wed, 14 Apr 2025 10:00:00 GMT
    content-type: application/json
    content-length: 3798
    content-disposition: attachment; filename="213"
    providerid: {ProviderID}
    ```
