# 应用管理

## 应用管理

**应用管理功能** 包括两个方向：

* 标准参数，适用于大多数面板。
* 高级参数，需要传递 [Provider ID](provide-id.md) 和订阅。

要激活参数，请传递值 `true` 或 `1`；要禁用 — 任何其他非空值（例如，`0` 或 `false`）。

### 标准参数

<details>

<summary>订阅自动更新</summary>

系统创建任务以指定的间隔执行操作。根据内部优先级，系统尝试在设定的时间启动订阅更新。\
如果由于某种原因未在指定间隔内执行更新，它将在下次应用启动时自动发生。\
间隔以小时为单位，必须是 1 小时的倍数。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#profile-update-interval: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>订阅名称</summary>

订阅配置文件的名称。可以作为纯文本或 base64 (UTF-8) 传递。**限制**：最大长度 — 25 个字符。

通过订阅主体，在参数前添加 # 符号（例如 #profile-title）

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#profile-title: Name VPN
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>订阅状态字符串（流量、到期日期）</summary>

显示有关余额、已用流量量和订阅到期日期的信息。\
在应用中，刻度的左侧显示已消耗流量量（upload + download），右侧 — 总容量 (total) 在 “/” 符号后。\
订阅到期日期在 **expire** 参数中指定。\
**注意：** 所有数据在一个标头中传递，并用 **;** 符号分隔。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#subscription-userinfo: upload=0; download=2153701362; total=0; expire=1790951622
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>支持页面链接</summary>

转到支持页面的按钮。\
显示为位于行右侧的蓝色图标。\
如果链接指向 Telegram，则显示 Telegram 图标；在其他情况下，使用标准链接图标。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#support-url: https://t.me/happ_chat
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>网站页面链接</summary>

转到订阅网站页面的按钮。\
显示为位于行左侧的蓝色图标。\
如果未设置参数，图标将为灰色。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#profile-web-page-url: https://happ.su
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>公告</summary>

订阅可以包含公告文本，以 **纯文本** 或 **Base64** 格式传递。\
**限制：** 最大显示文本长度 — **200 个字符**。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#announce: base64:SGFwcCB0aGUgYmVzdCE=
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>隧道配置（仅限桌面版）</summary>

为 sing-box 内核传递自己的隧道配置。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#announce: base64:SGFwcCB0aGUgYmVzdCE=
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

### 高级参数 <a href="#id-rasshirennyifunkcional-opisanieparametrov" id="id-rasshirennyifunkcional-opisanieparametrov"></a>

{% hint style="warning" %}
需要 [Provider ID](provide-id.md) 参数！
{% endhint %}

<details>

<summary>更改订阅 URL</summary>

如果域被您的提供商阻止，并且用户只能通过 VPN 连接到服务器并更新订阅，此参数适合您。通过在此参数的值中设置新域名，您将确保所有订阅用户自动替换它。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#new-url https://mynew-domain.com/3J3jrb4jfc
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>更改订阅域</summary>

更改网站域而不更改完整 URL，保留地址的其余部分。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#new-domain mynew-domain.com
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>订阅中的服务器描述</summary>

允许设置附加标题，显示在服务器名称下而不是标准文本（例如，“VMess”、“VLESS”、“Trojan”）。

* 最大长度 — 30 个字符。
* 如果不适合屏幕，将用省略号缩短。
* 通过 `?` 分隔符在 `title` 后设置。

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

<summary>订阅的分段和前端</summary>

某些 CDN 支持域前端。这允许通过第三方域连接到您的站点。

例如，通过指定连接地址 `visa.com`，并在 Host 标头中指定 `my-domain.com`，提供商只会看到对 `visa.com` 的请求。

您还可以使用 SNI TLSHello 中的数据包分段访问您的域以获取服务器列表。

默认情况下，所有订阅都启用分段。用户只能添加订阅一次；在重复尝试时，如果帐户不是高级帐户，则不允许更新。

**带参数的 URL 方案**

```
[link]#title?[fragment]&[resolve-address]&[host]&[insecure]

前端：
visa.com/123#MyVPN?resolve-address=visa.com&host=mydomain.com

分段：
mydomain.com/123#MyVPN?fragment=80-250,10-100,tlshello
```

分段包含三个参数：`[length]`、`[interval]` 和 `[packets]`。

使用前端时，必须首先指定通过其进行连接的域的 URL。您还需要设置 `resolve-address` — 这可以是域或 IP 地址 — 和 `host`，对应于所选提供商网络中的主机。

</details>

<details>

<summary>高级分段</summary>

此功能目前正在进行封闭测试，并将很快可用...

</details>

<details>

<summary>不可禁用的 HWID</summary>

默认情况下，所有 Happ 应用都启用 HWID。但如果您希望用户无法通过在应用设置中关闭它来禁用此参数的转发，您可以与订阅一起发送特殊参数。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#subscription-always-hwid-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>订阅到期通知</summary>

您可以启用自动订阅到期通知功能。\
用户将在订阅结束前 3 天收到提醒：应用将在三天内每天发送一个通知。这将帮助用户及时续订订阅。

通知文本：

```
您的订阅 [name] 即将到期，别忘了续订它。
```

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#notification-subs-expire: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>在订阅中隐藏服务器设置</summary>

禁用您的订阅用户查看和编辑服务器配置的功能。该设置适用于已添加的订阅以及将来添加的订阅。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#hide-settings: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>域解析</summary>

应用可以在建立连接之前执行服务器域的初步解析。\
您可以指定任何 DoH 服务器，并在连接到 Xray 服务器时，域名将被替换为接收到的 IP 地址。

如果域返回多个 IP 地址，应用将自动选择响应时间 (ping) 最小的地址。\
但是请注意：如果 IP 地址数量较多，连接可能需要更长时间，因为所有选项都会提前测试。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#server-address-resolve-enable: 1
#server-address-resolve-dns-domain: https://common.dot.dns.yandex.net/dns-query
#server-address-resolve-dns-ip: 77.88.8.8
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

**管理应用设置**

{% hint style="warning" %}
需要 [Provider ID](provide-id.md) 参数！
{% endhint %}

<details>

<summary>自动连接</summary>

允许在启动应用时自动将用户连接到服务器。此外，使用 **subscription-autoconnect** 参数，可以指定连接到特定服务器的标准。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#subscription-autoconnect: 1
#subscription-autoconnect-type: lastused
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>自动 ping</summary>

如果需要，在打开应用时启动服务器列表的自动测试。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#subscription-ping-onopen-enabled: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>自动更新订阅</summary>

在应用中，可以一次性启用或禁用所有订阅的自动更新 — 此设置同时适用于所有订阅。如果需要仅为特定订阅设置自动更新，请使用订阅自动更新功能。禁用全局设置时，每个订阅独立确定其更新时间。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#new-url: https:/mynew-domain.com/3J3jrb4jfc
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>分段</summary>

这是所有订阅的分段管理的全局参数。如果需要仅为特定订阅或服务器分配分段，请使用免费功能和应用通用文档中的说明。禁用全局设置时，每个订阅独立确定分段设置。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
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

此函数允许您选择应用中的 ping 方法。有三种选项：“via Proxy”、“TCP” 和 “ICMP”。对于 “via Proxy” 模式，您可以额外指定用于 ping 检查的 URL。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
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

此函数允许更改在接收订阅时标头中使用的 User-Agent。在提供商阻止具有非标准或不合适标头的请求的情况下很有用。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#change-user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/135.0.0.0 Safari/537.36
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>应用自动启动</summary>

此函数允许在设备开启时自动启动应用。目前仅适用于 Android。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#app-auto-start: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>应用启动时更新订阅</summary>

此函数在每次打开应用时自动更新应用中的所有订阅。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#subscription-auto-update-open-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>选定应用的代理 (Android)</summary>

在此参数中，您可以指定应使用 VPN 或相反绕过它的应用列表。如果应用尚未安装在设备上但在列表中，则在安装后第一次连接到 VPN 时将自动考虑它。

**设置此参数的示例：**

```
per-app-proxy-mode: [off/on/bypass] \\指定三个参数之一
per-app-proxy-list: [com.google.chrome,com.meta.instagram] \\通过 ',' 分隔的 appID 列表
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

{% code title="通过订阅主体：" %}
```
#per-app-proxy-mode: on
#per-app-proxy-list: com.google.chrome,com.meta.instagram
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>数据包分析 (Sniffing)</summary>

在 **xray-core** 中，sniffing 需要分析第一个连接数据包并自动确定 **协议** (HTTP, TLS, BitTorrent 等) 和 **域** (SNI/Host)。\
可能影响 WeChat 应用中的媒体加载。默认启用。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#sniffing-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>禁止折叠订阅</summary>

此函数禁用折叠订阅的功能：服务器列表始终以完整、展开视图显示。

**设置此参数的示例：**

```
subscriptions-collapse: [String] 
```

**传递方式：**

{% code title="通过 HTTP 标头：" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscriptions-collapse: 1
```
{% endcode %}

{% code title="通过订阅主体：" %}
```
#subscriptions-collapse: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Ping 显示模式</summary>

允许显示图标而不是时间值。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
```
#ping-result: icon
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Mux</summary>

xray-core 中的 Mux 是多路复用功能，允许通过一个物理 TCP 连接传输多个虚拟 TCP 连接的数据。它旨在减少 TCP-handshake 的延迟，但不是为了增加带宽（甚至可能减慢大下载）。在 outbound 配置中配置，具有 enabled 和 concurrency 等参数 (min -1 max 1024)。

**设置此参数的示例：**

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

{% code title="通过订阅主体：" %}
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
