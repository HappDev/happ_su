# 应用管理

## 应用管理

**应用管理功能**包括两个方向：

* 标准参数，适用于大多数面板。
* 高级参数，需要在订阅中指定 [Provider ID](https://www.happ.su/main/ru/dev-docs/provider-id)。

要启用参数，请传递值 `true` 或 `1`；要禁用，请传递任何其他非空值（例如 `0` 或 `false`）。

### 标准参数

<details>

<summary>订阅自动更新</summary>

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2Fd2xihMt7tB8cpcR1RXZd%2Fimage.png?alt=media&#x26;token=9010f024-545a-48db-80e5-2f5f8ab8451d" alt=""><figcaption></figcaption></figure>

在系统中创建定时任务。根据系统内部优先级，系统会尝试在设定时间启动订阅更新。如果因任何原因未在指定时间间隔内执行更新，则会在下次启动应用时自动执行。时间间隔以小时为单位，必须是 1 小时的倍数。

**该参数配置示例：**

```
profile-update-interval: [int]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-update-interval: 1
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#profile-update-interval: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>订阅名称</summary>

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2F7bgkYeVyXOGKw6QAudYM%2Fimage.png?alt=media&#x26;token=cc9bb7cd-020f-4414-84ab-6b40192914a0" alt=""><figcaption></figcaption></figure>

订阅配置文件名称。可以是纯文本或 base64（UTF-8）。**限制**：最大长度为 25 个字符。

通过订阅内容传递时，在参数前添加 # 符号（例如 #profile-title）

**该参数配置示例：**

```
profile-title: [string]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-title: Name VPN
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#profile-title: Name VPN
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>订阅状态栏（流量、到期日期）</summary>

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2FTU1hir0t04S4hYOxqs0D%2Fimage.png?alt=media&#x26;token=d754d3a1-42f5-4457-a040-e39cdae50725" alt=""><figcaption></figcaption></figure>

显示订阅的余额、已使用流量和有效期。在应用中，刻度尺左侧显示已使用流量（上传 + 下载），右侧显示“/”符号后的总流量。订阅到期日期在 **expire** 参数中指定。**注意**：所有数据在一个标头中传递，并以 **;** 符号分隔。

**该参数配置示例：**

```
subscription-userinfo: [string]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-userinfo: upload=0; download=2153701362; total=0; expire=1790951622
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
№subscription-userinfo: upload=0; download=2153701362; total=0; expire=1790951622
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>支持页面链接</summary>

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2FPGjTQfpKAQlhf1EXWVax%2Fimage.png?alt=media&#x26;token=37bc2b33-45eb-4744-ac25-ce3dac1703f2" alt=""><figcaption></figcaption></figure>

跳转到支持页面的按钮。显示为位于行右侧的蓝色图标。如果链接指向 Telegram，则显示 Telegram 图标；其他情况使用标准链接图标。

**该参数配置示例：**

```
support-url: [string]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
support-url: https://t.me/happ_chat
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#support-url: https://t.me/happ_chat
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>网站页面链接</summary>

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2FBMPDmdzIiV9j7jXuFyO0%2Fimage.png?alt=media&#x26;token=a371b358-e5d6-431b-ae1a-dcc20ea62c44" alt=""><figcaption></figcaption></figure>

跳转到订阅网站页面的按钮。显示为位于行左侧的蓝色图标。如果未设置参数，图标将为灰色。

**该参数配置示例：**

```
profile-web-page-url: [string]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-web-page-url: https://happ.su
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#profile-web-page-url: https://happ.su
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>公告</summary>

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2FZbCR6gfKfxy3pT66DoEg%2Fimage.png?alt=media&#x26;token=2beab1b7-981e-40d5-8458-bef8738dc767" alt=""><figcaption></figcaption></figure>

订阅可以包含以 **纯文本** 或 **Base64** 格式传递的公告文本。**限制**：显示文本的最大长度为 **200 个字符**。

**该参数配置示例：**

```
announce: [string]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
announce: base64:SGFwcCB0aGUgYmVzdCE=
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#announce: base64:SGFwcCB0aGUgYmVzdCE=
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>禁用路由</summary>

用于在应用中禁用路由的全局参数。

**该参数配置示例：**

```
routing-enable: [string]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
routing-enable: 0
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#routing-enable: 0
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>隧道配置（仅适用于桌面版）</summary>

为 sing-box 核心传递自定义隧道配置。

**该参数配置示例：**

```
custom-tunnel-config: [json]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
custom-tunnel-config: {...}
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#custom-tunnel-config: {...}
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

### 高级参数 <a href="#id-rasshirennyifunkcional-opisanieparametrov" id="id-rasshirennyifunkcional-opisanieparametrov"></a>

{% hint style="warning" %}
需要 Provider ID 参数！
{% endhint %}

<details>

<summary>更改订阅 URL</summary>

如果您的域名被提供商屏蔽，而用户只能通过 VPN 连接服务器并更新订阅，则此参数正是为您设计的。在此参数值中设置新的域名，即可确保订阅的所有用户自动替换该域名。

**该参数配置示例：**

```
new-url: [url]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
new-url: https://mynew-domain.com/3J3jrb4jfc
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#new-url https://mynew-domain.com/3J3jrb4jfc
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>更改订阅域名</summary>

更改网站域名而不更改完整 URL，保留地址的其余部分。

**该参数配置示例：**

```
new-domain: [domain]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
new-domain: mynew-domain.com
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#new-domain mynew-domain.com
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Fallback URL</summary>

<figure><img src="../.gitbook/assets/image (3).png" alt="" width="375"><figcaption></figcaption></figure>

如果主 URL 无法访问、返回 300–599 错误或在 9 秒内未响应，应用程序将切换至备用 URL（如果已提供）。

**该参数配置示例：**

```
fallback-url: [url]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
fallback-url: https://mynew-domain.com/3J3jrb4jfc
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#fallback-url https://mynew-domain.com/3J3jrb4jfc
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>订阅中的服务器描述</summary>

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2FoDU5uorhG21AqBg91iwz%2Fimage.png?alt=media&#x26;token=833d487e-b712-4848-ba63-1a1a8a1a4465" alt=""><figcaption></figcaption></figure>

允许设置额外的说明文字，该文字显示在服务器名称下方，代替标准文本（例如 "VMess"、"VLESS"、"Trojan"）。

* 最大长度为 30 个字符。
* 如果无法完整显示在屏幕上，将以省略号截断。
* 在 `title` 之后通过分隔符 `?` 设置。

**示例：**

{% code title="VLESS" %}
```
vless://1fb46fdc-e3e4-35d1-bd46-605d773b5762@5.5.8.9:443?encryption=none&node_id=482&headerType=none&type=tcp&security=reality&sni=booking.com&fp=chrome&pbk=YqHW8a4iAc1SZYpTrFVoOQg1F3yAdX1tWXuROZUCsEU&sid=6ba85179e30d4fc2&flow=xtls-rprx-vision&xtls=2#title?serverDescription=SGFwcCB0aGUgYmVzdA==
```
{% endcode %}

{% code title="VMESS" %}
```
vmess://eyJob3N0IjoiZWxhaG9tZWtpdGNoZW4uY29tIiwicGF0aCI6IiIsInRscyI6IiIsImFkZCI6ImVsYWhvbWVraXRjaGVuLmNvbSIsInBvcnQiOjUwMDAsImFpZCI6MCwibmV0IjoidGNwIiwidHlwZSI6Im5vbmUiLCJ2IjoiMiIsInBzIjoi4piB77iPIDogNTMuM0dCIiwiaWQiOiI4N2ZhN2VmMC1jM2ZjLTNiOTAtYTJkOC01OGZjYjhkZmZmMjYiLCJzZXJ2ZXJEZXNjcmlwdGlvbiI6IkhhcHAgdGhlIGJlc3QifQ==
```
{% endcode %}

{% code title="Trojan" %}
```
trojan://8GXLP3dEzm7T8wP5Jx0Ufg@199.107.164.105:443?security=tls&insecure=1&fragment=3,1,tlshello&type=ws&headerType=&path=%2F&host=quictest.burncommunity.ru&sni=quictest.burncommunity.ru&fp=chrome&alpn=http%2F1.1#title?serverDescription=SGFwcCB0aGUgYmVzdA==
```
{% endcode %}

{% code title="Socks5" %}
```
socks://pkg-private2-country-us-city-new_york_city:w0e20i55uuq6pxqg@quality.proxywing.com:1080#title?serverDescription=SGFwcCB0aGUgYmVzdA==
```
{% endcode %}

{% code title="Shadowsocks" %}
```
ss://YWVzLTI1Ni1jZmI6UzdLd1V1N3lCeTU4UzNHYQ==@80.92.204.106:9042#title?serverDescription=SGFwcCB0aGUgYmVzdA==
```
{% endcode %}

{% code title="Wireguard" %}
```
wireguard://password2key@123.123.123.2:10803?publickey=asd33d223d33&address=dom.ru&allowinsecure=1&mtu=1500&reserved=1,22,33#title?serverDescription=SGFwcCB0aGUgYmVzdA==
```
{% endcode %}

{% code title="JSON" %}
```
{
  "dns": {
  ...
  },
  "inbounds": [
  ...
  ],
  "outbounds": [
  ...
  ],
  "remarks": "🇭🇰 Hong Kong",
  "meta": {
    "serverDescription": "Happ the best"
  }
}
```
{% endcode %}

</details>

<details>

<summary>订阅分片与前置域名</summary>

某些 CDN 支持域名前置。这允许您通过第三方域名连接到您的网站。例如，将连接地址指定为 `visa.com`，而 Host 标头为 `my-domain.com`，提供商将只看到对 `visa.com` 的请求。

此外，您还可以使用 TLSHello 中的数据包分片访问您的域名以获取服务器列表。

默认情况下，所有订阅都启用了分片。用户只能添加一次订阅；如果账户不是高级账户，则不允许更新。

**带参数的 URL 结构**

```
[链接]#标题?[分片参数]&[解析地址]&[主机]&[不安全模式]

前置域名示例：
visa.com/123#MyVPN?resolve-address=visa.com&host=mydomain.com

分片示例：
mydomain.com/123#MyVPN?fragment=80-250,10-100,tlshello
```

分片包含三个参数：`[length]`、`[interval]` 和 `[packets]`。

使用前置域名时，需要首先指定将通过其建立连接的域名 URL。还需要设置 `resolve-address` —— 可以是域名或 IP 地址 —— 以及 `host`，其对应于您所选网络中的主机。

</details>

<details>

<summary>No Limit Mode</summary>

No Limit 模式可用于所有协议类型或仅用于 xhttp。该模式通过增加 xray-core 的内存限制来提高稳定性和性能。

> 重要提示： 此功能目前处于公测阶段。请仅选择一种激活方式（全部协议或仅 xhttp）—— 严禁同时开启两项。

Example of setting this parameter:

```
no-limit-enabled: [true / 1]
no-limit-xhttp-enabled: [true / 1]
```

**Ways to pass it:**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
no-limit-xhttp-enabled: 1
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#no-limit-xhttp-enabled: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>高级分片</summary>

此功能目前正在进行封闭测试，即将推出...

</details>

<details>

<summary>不可禁用的 HWID</summary>

默认情况下，HWID 在所有 Happ 应用中均为启用状态。但如果您希望用户无法在应用设置中禁用此参数的转发，则可以随订阅一起发送此特殊参数。

**该参数配置示例：**

```
subscription-always-hwid-enable: [true / 1]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-always-hwid-enable: 1
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#subscription-always-hwid-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>订阅到期通知</summary>

您可以启用订阅到期的自动通知功能。用户将在订阅到期前 3 天收到提醒：连续三天每天发送一条通知。这有助于用户及时续订订阅。

通知文本：

```
 У вашей подписки [name] скоро истечёт срок действия, не забудьте продлить её.
```

**该参数配置示例：**

```
notification-subs-expire: [true / 1]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
notification-subs-expire: 1
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#notification-subs-expire: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>隐藏订阅中的服务器设置</summary>

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2FtaLP0j0QXiaI459X2UMY%2Fimage.png?alt=media&#x26;token=4cb840e3-8f54-4be3-b6be-2bac7e244952" alt=""><figcaption></figcaption></figure>

禁用订阅用户查看和编辑服务器配置的功能。该设置适用于已添加的订阅以及将来要添加的订阅。

**该参数配置示例：**

```
hide-settings: [true / 1]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
hide-settings: 1
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#hide-settings: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>域名解析</summary>

应用可以在建立连接之前预先解析服务器的域名。您可以指定任何 DoH 服务器，在连接到 Xray 服务器时，域名将被替换为获取的 IP 地址。

如果域名返回多个 IP 地址，应用将自动选择延迟时间（ping）最低的那个。但需要注意的是：如果 IP 地址数量较多，连接可能需要更长时间，因为所有选项都会提前测试。

**该参数配置示例：**

```
server-address-resolve-enable: [true / 1]
server-address-resolve-dns-domain: [url]
server-address-resolve-dns-ip: [ip]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
server-address-resolve-enable: 1
server-address-resolve-dns-domain: https://common.dot.dns.yandex.net/dns-query
server-address-resolve-dns-ip: 77.88.8.8
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#server-address-resolve-enable: 1
#server-address-resolve-dns-domain: https://common.dot.dns.yandex.net/dns-query
#server-address-resolve-dns-ip: 77.88.8.8
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

**应用设置管理**

{% hint style="warning" %}
需要 Provider ID 参数！
{% endhint %}

<details>

<summary>自动连接</summary>

允许在启动应用时自动将用户连接到服务器。此外，可以通过参数 **subscription-autoconnect-type** 指定连接到特定服务器的条件。

**该参数配置示例：**

```
subscription-autoconnect: [true / 1]
subscription-autoconnect-type: [“lastused“/”lowestdelay”]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-autoconnect: 1
subscription-autoconnect-type: lowestdelay
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#subscription-autoconnect: 1
#subscription-autoconnect-type: lastused
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>自动 Ping</summary>

如有必要，在打开应用时自动测试服务器列表。

**该参数配置示例：**

```
subscription-ping-onopen-enabled: [true / 1]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-ping-onopen-enabled: 1
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#subscription-ping-onopen-enabled: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>订阅自动更新</summary>

可以在应用中同时启用或禁用所有订阅的自动更新——此设置会同时应用于所有订阅。如果只需要为特定订阅设置自动更新，请使用“订阅自动更新”功能。禁用全局设置后，每个订阅将独立确定其更新时间。

**该参数配置示例：**

```
subscription-auto-update-enable: [true / 1] 
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-auto-update-enable: 1
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#subscription-auto-update-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>分片</summary>

这是控制所有订阅分片的全局参数。如果只需要为特定订阅或服务器设置分片，请使用免费功能和应用通用文档中的说明。禁用全局设置后，每个订阅将独立确定分片设置。

**该参数配置示例：**

```
fragmentation-enable: [true / 1]
fragmentation-packets: [tlshello,1-2,1-3,1-5]
fragmentation-length: [50-100]
fragmentation-interval: [10-20]
fragmentation-maxsplit: [String]
noises-enable: [true / 1]
noises-type: [rand. str, base64]
noises-packet: [String]
noises-delay: [String]
noises-applyto: [ip,ipv4,ipv6]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
fragmentation-enable: 1
fragmentation-packets: tlshello
fragmentation-length: 50-100
fragmentation-interval: 5
fragmentation-maxsplit: 100-200
noises-enable: 1
noises-type: rand
noises-packet: 10-20
noises-delay: 10-16
noises-applyto: ipv4
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#fragmentation-enable: 1
#fragmentation-packets: tlshello
#fragmentation-length: 50-100
#fragmentation-interval: 5
#fragmentation-maxsplit: 100-200
#noises-enable: 1
#noises-type: rand
#noises-packet: 10-20
#noises-delay: 10-16
#noises-applyto: ipv4
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Ping</summary>

此功能允许选择应用中执行 ping 的方式。提供三个选项："via Proxy"、"TCP" 和 "ICMP"。对于 "via Proxy" 模式，可以额外指定用于 ping 检查的 URL。

**该参数配置示例：**

```
ping-type: ["proxy", "proxy-head', "tcp","icmp"]
check-url-via-proxy: [url]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
ping-type: proxy
check-url-via-proxy: https://cp.cloudflare.com/generate_204
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#ping-type proxy
#check-url-via-proxy: https://cp.cloudflare.com/generate_204
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>User-Agent</summary>

此功能允许更改获取订阅时标头中使用的 User-Agent。在提供商屏蔽非标准或不合适标头的请求时非常有用。

**该参数配置示例：**

```
change-user-agent: [String] 
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
change-user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/135.0.0.0 Safari/537.36
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#change-user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/135.0.0.0 Safari/537.36
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>应用自动启动</summary>

允许在设备开机时自动启动应用。目前仅在 Android 上可用。

**该参数配置示例：**

```
app-auto-start: [String] 
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
app-auto-start: 1
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#app-auto-start: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>应用启动时更新订阅</summary>

此功能会在每次打开应用时自动更新应用中的所有订阅。

**该参数配置示例：**

```
subscription-auto-update-open-enable: [String] 
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-auto-update-open-enable: 1
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#subscription-auto-update-open-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>选定应用的代理（Android）</summary>

可以在此参数中指定应使用 VPN 或绕过 VPN 的应用列表。如果应用尚未安装在设备上但已在列表中指定，则在首次安装后连接到 VPN 时会自动将其计入。

**该参数配置示例：**

```
per-app-proxy-mode: [off/on/bypass] \\请从三个参数中选择一个
per-app-proxy-list: [com.google.chrome,com.meta.instagram] \\以 ',' 分隔的 appID 列表
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
per-app-proxy-mode: on
per-app-proxy-list: com.google.chrome,com.meta.instagram
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#per-app-proxy-mode: on
#per-app-proxy-list: com.google.chrome,com.meta.instagram
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>数据包分析（Sniffing）</summary>

xray-core 中的 sniffing 用于分析连接的前几个数据包，并自动确定**协议**（HTTP、TLS、BitTorrent 等）和**域名**（SNI/Host）。可能会影响微信应用中的媒体加载。默认已启用。\\

**该参数配置示例：**

```
sniffing-enable: [String] 
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
sniffing-enable: 1
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#sniffing-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>禁止折叠订阅</summary>

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2FLg7CkkHrYquuQ9vFarVb%2Fimage.png?alt=media&#x26;token=a3be4696-2140-419e-8dff-80e549aad507" alt=""><figcaption></figcaption></figure>

此功能禁用折叠订阅的能力：服务器列表始终以完全展开的方式显示。\\

**该参数配置示例：**

```
subscriptions-collapse: [false / 0] 
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscriptions-collapse: 0
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#subscriptions-collapse: 0
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Ping 显示模式</summary>

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2F1F3qDFUQfJqGYEDQrETt%2Fimage.png?alt=media&#x26;token=e3921af0-ea18-42ce-bd0c-b3422dc765a1" alt=""><figcaption></figcaption></figure>

允许显示图标而不是时间值\\

**该参数配置示例：**

```
ping-result: [time,icon]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
ping-result: icon
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#ping-result: icon
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Mux</summary>

Mux 在 xray-core 中是多路复用（multiplexing）功能，允许通过单个物理 TCP 连接传输多个虚拟 TCP 连接的数据。旨在降低 TCP 握手的延迟，而不是提高带宽（甚至可能减慢大量下载）。在出站配置中设置，参数包括 enabled 和 concurrency（最小 -1，最大 1024）。

**该参数配置示例：**

```
mux-enable: [true / 1]
mux-tcp-connections: [String]
mux-xudp-connections: [String]
mux-quic: [String]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
mux-enable: 1
mux-tcp-connections: 100
mux-xudp-connections: 200
mux-quic: skip
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#mux-enable: 1
#mux-tcp-connections: 100
#mux-xudp-connections: 200
#mux-quic: skip
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>代理 \ TUN 模式（仅适用于桌面版）</summary>

必须**仅使用**以下两个参数之一！这些参数在添加/更新订阅时确定连接类型。

**该参数配置示例：**

```
proxy-enable: [true / 1]
tun-enable: [true / 1]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
proxy-enable: 1
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#proxy-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>TUN 模式（仅适用于桌面版）</summary>

确定 TUN 连接使用的模式。

* **`system`** — 使用操作系统的系统网络栈。\
  快速高效，但依赖于路由和防火墙的正确配置。
* **`gvisor`** — 使用 gVisor 的用户空间栈（userspace）。\
  减少对内核规则及 iptables/nftables/Docker 冲突的依赖，隔离性更好；可能存在轻微的性能损失。

**该参数配置示例：**

```
tun-mode: [system,gvisor]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
tun-mode: gvisor
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#tun-mode: gvisor
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>选择隧道核心（仅适用于桌面版）</summary>

确定将用于 TUN 连接的核心。可选择 [sing-box](https://github.com/SagerNet/sing-box)、[tun2proxy](https://github.com/tun2proxy/tun2proxy)

**该参数配置示例：**

```
tun-type: [singbox, tun2proxy]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
tun-type: tun2proxy
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#tun-type: tun2proxy
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>排除路由</summary>

定义不应通过隧道传输流量的子网和 IP 地址列表。地址在同一行中指定，以空格和逗号分隔。

**该参数配置示例：**

```
exclude-routes: [String]
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
exclude-routes: 192.169.1.0/24, 10.0.0.0/8
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#exclude-routes: 192.169.1.0/24, 10.0.0.0/8
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>主题（仅限 iOS）</summary>

<figure><img src="../.gitbook/assets/image.png" alt="" width="375"><figcaption></figcaption></figure>

允许您将配色主题自定义为个人风格。您可以在编辑器中创建自己的主题——长按“外观主题”标签即可打开菜单。创建的主题可以导出到剪贴板，也可以从剪贴板、.happ 文件中导入，或通过订阅进行分享。

{% code title="VIOLET Theme" overflow="wrap" expandable="true" %}
```json
{
  "backgroundGradientRotationAngle" : 37.1,
  "serverRowBackgroundColor" : "#21003D67",
  "subsHeaderColor" : "#42296DFF",
  "profileWebPageIconColor" : "#A2B8FFFF",
  "selectedServerRowColor" : "#3E2F62B5",
  "disclosureSubHeaderTextColor" : "#C1C2E2FF",
  "buttonTextColor" : "#FFFFFFFF",
  "buttonTimerColor" : "#FFFFFFFF",
  "subscriptionInfoBackgroundColor" : "#21003CFF",
  "backgroundColors" : [
    "#3D2A7DFF",
    "#6557BAFF",
    "#9377FF7F"
  ],
  "disclosureHeaderTextColor" : "#FFFFFFFF",
  "backgroundGradientColorIntensity" : 1,
  "additionalOptionsButtonColor" : "#FFFFFFFF",
  "buttonImageType" : "light",
  "serverRowSubTitleTextColor" : "#C1C2E2FF",
  "supportIconColor" : "#FFFFFFFF",
  "topBarButtonsColor" : "#FFFFFFFF",
  "subscriptionTrafficBackgroundColor" : "#533EA7FF",
  "subHeaderButtonColor" : "#FFFFFFFF",
  "buttonColor" : "#9377FFFF",
  "powerIconColor" : "#3D2A7DFF",
  "subscriptionInfoTextColor" : "#FFFFFFFF",
  "serverRowTitleTextColor" : "#FFFFFFFF",
  "backgroundImageType" : "system",
  "elipseColors" : [
    "#00B460FF",
    "#CF72FFE0",
    "#FFDD00FF"
  ],
  "serverRowChevronColor" : "#FFFFFFFF"
}
```
{% endcode %}

{% code title="Turquoise Theme" overflow="wrap" expandable="true" %}
```json
{
  "backgroundGradientRotationAngle" : 39.21265661716461,
  "serverRowChevronColor" : "#F3FFFDFF",
  "buttonImageType" : "light",
  "buttonTimerColor" : "#3B3C3DFF",
  "subscriptionTrafficBackgroundColor" : "#00343BFF",
  "subscriptionInfoBackgroundColor" : "#006B7AFF",
  "serverRowTitleTextColor" : "#D0FFF3FF",
  "serverRowBackgroundColor" : "#02424DFF",
  "powerIconColor" : "#05525ACA",
  "supportIconColor" : "#F3FFF9FF",
  "profileWebPageIconColor" : "#F5FFF9FF",
  "selectedServerRowColor" : "#006B7BFF",
  "disclosureHeaderTextColor" : "#D0FFF3FF",
  "subsHeaderColor" : "#007982FF",
  "elipseColors" : [
    "#4DFF00CC",
    "#E2FF00FF",
    "#FF6000FF"
  ],
  "subscriptionInfoTextColor" : "#E5FFF7FF",
  "buttonColor" : "#8FFFFEFF",
  "serverRowSubTitleTextColor" : "#ADD3CBFF",
  "topBarButtonsColor" : "#FFFFFFD8",
  "settingsControlsTintColor" : "#00C3C1FF",
  "backgroundGradientColorIntensity" : 1,
  "disclosureSubHeaderTextColor" : "#A4FFE599",
  "additionalOptionsButtonColor" : "#FBFFFF99",
  "backgroundImageType" : "light",
  "backgroundColors" : [
    "#003740FF",
    "#003740FF",
    "#005255FF",
    "#00A6A1FF",
    "#00C9DDFF"
  ],
  "subHeaderButtonColor" : "#BAD7CFFF",
  "buttonTextColor" : "#000000FF"
}
```
{% endcode %}

**该参数配置示例：**

```
color-profile: [String] //base64 or plainString
color-profile: resetcolors // full reset
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
color-profile: {"backgroundGradientRotationAngle":37.1,"serverRowBackgroundColor":"#21003D67","subsHeaderColor":"#42296DFF","profileWebPageIconColor":"#A2B8FFFF","selectedServerRowColor":"#3E2F62B5","disclosureSubHeaderTextColor":"#C1C2E2FF","buttonTextColor":"#FFFFFFFF","buttonTimerColor":"#FFFFFFFF","subscriptionInfoBackgroundColor":"#21003CFF","backgroundColors":["#3D2A7DFF","#6557BAFF","#9377FF7F"],"disclosureHeaderTextColor":"#FFFFFFFF","backgroundGradientColorIntensity":1,"additionalOptionsButtonColor":"#FFFFFFFF","buttonImageType":"light","serverRowSubTitleTextColor":"#C1C2E2FF","supportIconColor":"#FFFFFFFF","topBarButtonsColor":"#FFFFFFFF","subscriptionTrafficBackgroundColor":"#533EA7FF","subHeaderButtonColor":"#FFFFFFFF","buttonColor":"#9377FFFF","powerIconColor":"#3D2A7DFF","subscriptionInfoTextColor":"#FFFFFFFF","serverRowTitleTextColor":"#FFFFFFFF","backgroundImageType":"system","elipseColors":["#00B460FF","#CF72FFE0","#FFDD00FF"],"serverRowChevronColor":"#FFFFFFFF"}
```
{% endcode %}

{% code title="通过订阅内容：" %}
```
#color-profile: {"backgroundGradientRotationAngle":37.1,"serverRowBackgroundColor":"#21003D67","subsHeaderColor":"#42296DFF","profileWebPageIconColor":"#A2B8FFFF","selectedServerRowColor":"#3E2F62B5","disclosureSubHeaderTextColor":"#C1C2E2FF","buttonTextColor":"#FFFFFFFF","buttonTimerColor":"#FFFFFFFF","subscriptionInfoBackgroundColor":"#21003CFF","backgroundColors":["#3D2A7DFF","#6557BAFF","#9377FF7F"],"disclosureHeaderTextColor":"#FFFFFFFF","backgroundGradientColorIntensity":1,"additionalOptionsButtonColor":"#FFFFFFFF","buttonImageType":"light","serverRowSubTitleTextColor":"#C1C2E2FF","supportIconColor":"#FFFFFFFF","topBarButtonsColor":"#FFFFFFFF","subscriptionTrafficBackgroundColor":"#533EA7FF","subHeaderButtonColor":"#FFFFFFFF","buttonColor":"#9377FFFF","powerIconColor":"#3D2A7DFF","subscriptionInfoTextColor":"#FFFFFFFF","serverRowTitleTextColor":"#FFFFFFFF","backgroundImageType":"system","elipseColors":["#00B460FF","#CF72FFE0","#FFDD00FF"],"serverRowChevronColor":"#FFFFFFFF"}
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>
