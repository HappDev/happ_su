---
description: 通过订阅管理应用设置
---

# 应用管理

**应用管理功能** 包含两个方向：

* 适用于大多数面板的 [标准参数](app-management.md#standartnye-parametry)。
* 需要在订阅中指定 [Provider ID](provider-id.md) 的 [高级参数](app-management.md#id-rasshirennyifunkcional-opisanieparametrov)。

要启用某个参数，请传递 `true` 或 `1`；要禁用，请传递任何其他**非空**值（例如 `0` 或 `false`）。

## 标准参数

<details>

<summary>订阅自动刷新</summary>

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

系统会创建一个按给定间隔运行操作的任务。根据内部优先级，系统会尽量在计划时间刷新订阅。
如果由于某种原因未能在指定间隔内完成刷新，则会在下次启动应用时自动执行。
间隔以小时为单位设置，且必须为 1 小时的整数倍。

**示例：**

```
profile-update-interval: [int]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-update-interval: 1
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#profile-update-interval: 1
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>订阅名称</summary>

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

订阅档案名。可用纯文本或 Base64（UTF-8）传递。**限制：** 最长 **25** 个字符。

在订阅正文中，在参数前加井号 #（例如 #profile-title）。

**示例：**

```
profile-title: [string]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-title: Name VPN
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#profile-title: Name VPN
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>订阅状态字符串（流量、到期日期）</summary>

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

显示余额、已用流量以及订阅有效期。
在应用中，进度条左侧显示已使用的流量（upload + download），右侧在 “/” 符号后显示总量。
订阅结束时间通过 **expire** 参数提供。
**注意：** 所有数据通过一个响应头传递，并以 **;** 分隔。

**示例：**

```
subscription-userinfo: [string]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-userinfo: upload=0; download=2153701362; total=0; expire=1790951622
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
№subscription-userinfo: upload=0; download=2153701362; total=0; expire=1790951622
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>支持页面链接</summary>

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

用于跳转到支持页面的按钮。
在行的右侧显示为蓝色图标。
如果链接指向 Telegram，则显示 Telegram 图标；否则显示标准链接图标。

**示例：**

```
support-url: [string]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
support-url: https://t.me/happ_chat
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#support-url: https://t.me/happ_chat
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>网站链接</summary>

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

用于跳转到订阅网站的按钮。
在行的左侧显示为蓝色图标。
如果未设置该参数，图标将显示为灰色。

**示例：**

```
profile-web-page-url: [string]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-web-page-url: https://happ.su
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#profile-web-page-url: https://happ.su
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>公告</summary>

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

订阅可包含公告文本，可用 **纯文本** 或 **Base64** 传递。
**限制：** 最大显示长度为 **200 个字符**。

**示例：**

```
announce: [string]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
announce: base64:SGFwcCB0aGUgYmVzdCE=
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#announce: base64:SGFwcCB0aGUgYmVzdCE=
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>禁用路由</summary>

在应用内全局禁用路由的参数。

**示例：**

```
routing-enable: [string]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
routing-enable: 0
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#routing-enable: 0
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>隧道配置（仅限 Desktop）</summary>

为 sing-box 引擎传递自定义隧道配置。

**示例：**

```
custom-tunnel-config: [json]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
custom-tunnel-config: {...}
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#custom-tunnel-config: {...}
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

## 高级参数 <a href="#id-rasshirennyifunkcional-opisanieparametrov" id="id-rasshirennyifunkcional-opisanieparametrov"></a>

{% hint style="warning" %}
需要提供 [Provider ID](provider-id.md) 参数！
{% endhint %}

<details>

<summary>更改订阅 URL</summary>

如果你的域名被运营商屏蔽，用户只能在挂 VPN 时连接服务器并刷新订阅，那么该参数适用。将新域名作为参数值指定后，所有该订阅的用户都会自动替换为新地址。

**示例：**

```
new-url: [url]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
new-url: https://mynew-domain.com/3J3jrb4jfc
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#new-url https://mynew-domain.com/3J3jrb4jfc
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>更改订阅域名</summary>

在不改变完整 URL 的情况下，仅更换站点域名，保留其余地址部分。

**示例：**

```
new-domain: [domain]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
new-domain: mynew-domain.com
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#new-domain mynew-domain.com
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>订阅中的服务器描述</summary>

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

允许设置显示在服务器名称下方的附加字幕，用于替代标准文本（例如 “VMess”、“VLESS”、“Trojan”）。

* 最长 **30** 个字符。
* 如果超出屏幕宽度，会以省略号截断。
* 在 `title` 之后使用分隔符 `?` 设置。

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

<summary>订阅的分片与前置（Fronting）</summary>

部分 CDN 支持域名前置。这样可以通过第三方域名连接到你的网站。

例如，将连接地址设置为 `visa.com`，并把 Host 头设置为 `my-domain.com`，则运营商只会看到对 `visa.com` 的请求。

你也可以在使用 SNI TLSHello 包分片的同时，请求你自己的域名以获取服务器列表。

默认情况下，所有订阅均启用分片。用户只能添加一次订阅；若再次尝试且账户非高级（premium），则不允许更新。

#### 携带参数的 URL 方案

```
[link]#title?[fragment]&[resolve-address]&[host]&[insecure]

Fronting:
visa.com/123#MyVPN?resolve-address=visa.com&host=mydomain.com

Fragmentation:
mydomain.com/123#MyVPN?fragment=80-250,10-100,tlshello
```

分片包含三个参数：`[length]`、`[interval]` 和 `[packets]`。

使用前置时，需先指定用于发起连接的域名所在的 URL。同时还需设置 `resolve-address`（可为域名或 IP）以及 `host`，其应与所选服务商网络中的你的主机相匹配。

</details>

<details>

<summary>高级分片</summary>

该功能目前处于封闭测试中，稍后将开放……

</details>

<details>

<summary>不可关闭的 HWID</summary>

默认情况下，所有 Happ 应用均启用 HWID。如果你希望用户无法在应用设置中关闭该参数的发送，可在订阅中一并下发特殊参数。

**示例：**

```
subscription-always-hwid-enable: [true / 1]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-always-hwid-enable: 1
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#subscription-always-hwid-enable: 1
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>订阅到期通知</summary>

你可以启用订阅到期的自动通知。
到期前 3 天，应用会每天发送 1 条提醒，共 3 天，帮助用户及时续订。

通知文本：

```
 您的订阅 [name] 即将到期，请及时续费。
```

**示例：**

```
notification-subs-expire: [true / 1]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
notification-subs-expire: 1
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#notification-subs-expire: 1
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>隐藏订阅内的服务器设置</summary>

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

禁用订阅用户查看和编辑服务器配置的能力。该设置对已添加和将来添加的订阅均生效。

**示例：**

```
hide-settings: [true / 1]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
hide-settings: 1
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#hide-settings: 1
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>域名解析</summary>

应用可以在建立连接之前，预先解析服务器域名。
你可以指定任意 DoH 服务器；连接到 Xray 服务器时，域名会被替换为解析得到的 IP 地址。

若某域名返回多个 IP，应用会自动选择延迟（ping）最低的那个。
但请注意：若 IP 数量较多，连接可能会更耗时，因为会预先测试所有候选 IP。

**示例：**

```
server-address-resolve-enable: [true / 1]
server-address-resolve-dns-domain: [url]
server-address-resolve-dns-ip: [ip]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

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

{% code title="通过订阅正文：" %}

```
#server-address-resolve-enable: 1
#server-address-resolve-dns-domain: https://common.dot.dns.yandex.net/dns-query
#server-address-resolve-dns-ip: 77.88.8.8
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

#### 应用设置管理 <a href="#upravlenie-nastroikami-prilozheniya" id="upravlenie-nastroikami-prilozheniya"></a>

{% hint style="warning" %}
需要提供 [Provider ID](provider-id.md) 参数！
{% endhint %}

<details>

<summary>自动连接</summary>

在应用启动时自动将用户连接到服务器。并且可以通过 **subscription-autoconnect** 指定选择连接服务器的依据。

**示例：**

```
subscription-autoconnect: [true / 1]
subscription-autoconnect-type: [“lastused“/”lowestdelay”]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

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

{% code title="通过订阅正文：" %}

```
#subscription-autoconnect: 1
#subscription-autoconnect-type: lastused
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>自动 Ping</summary>

在需要时，于打开应用时自动测试服务器列表。

**示例：**

```
subscription-ping-onopen-enabled: [true / 1]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-ping-onopen-enabled: 1
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#subscription-ping-onopen-enabled: 1
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>订阅自动更新</summary>

你可以一次性为所有订阅开启或关闭自动更新——该设置会同时应用到所有订阅。若仅需对某一订阅设置自动更新，请使用“订阅自动刷新”功能。关闭全局设置后，各订阅将独立决定其刷新时间。

**示例：**

```
subscription-auto-update-enable: [true / 1] 
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-auto-update-enable: 1
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#new-url: https:/mynew-domain.com/3J3jrb4jfc
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>分片（Fragmentation）</summary>

这是针对所有订阅的全局分片控制参数。若只需为某个订阅或服务器设置分片，请参考应用通用文档中的免费功能与说明。关闭全局设置后，各订阅将独立决定其分片设置。

**示例：**

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

{% code title="通过 HTTP 头：" %}

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

{% code title="通过订阅正文：" %}

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Ping</summary>

该功能允许选择应用内执行 Ping 的方式。可选三种：**via Proxy**、**TCP** 和 **ICMP**。在 “via Proxy” 模式下，还可额外指定用于检测的 URL。

**示例：**

```
ping-type: ["proxy", "proxy-head', "tcp","icmp"]
check-url-via-proxy: [url]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

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

{% code title="通过订阅正文：" %}

```
#ping-type proxy
#check-url-via-proxy: https://cp.cloudflare.com/generate_204
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>User-Agent</summary>

允许更改获取订阅时请求头中使用的 User-Agent。当运营商屏蔽携带非常规或不合规请求头的请求时，这会很有用。

**示例：**

```
change-user-agent: [String] 
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
change-user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/135.0.0.0 Safari/537.36
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#change-user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/135.0.0.0 Safari/537.36
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>应用自启动</summary>

设备开机后自动启动应用。目前仅在 Android 可用。 

**示例：**

```
app-auto-start: [String] 
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
app-auto-start: 1
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#app-auto-start: 1
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>打开应用时更新订阅</summary>

每次打开应用时，自动刷新所有订阅。

**示例：**

```
subscription-auto-update-open-enable: [String] 
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-auto-update-open-enable: 1
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#subscription-auto-update-open-enable: 1
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>按应用代理（Android）</summary>

可指定需要使用 VPN 的应用列表，或指定绕过 VPN 的应用。如果某个应用尚未安装但已在列表中，则其在首次安装后进行 VPN 连接时会被自动纳入控制范围。

**示例：**

```
per-app-proxy-mode: [off/on/bypass] \\指定三者之一
per-app-proxy-list: [com.google.chrome,com.meta.instagram] \\以 ',' 分隔的应用 ID 列表
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

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

{% code title="通过订阅正文：" %}

```
#per-app-proxy-mode: on
#per-app-proxy-list: com.google.chrome,com.meta.instagram
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>数据包嗅探（Sniffing）</summary>

在 **xray-core** 中，嗅探会分析连接的首批数据包，以自动识别 **协议**（HTTP、TLS、BitTorrent 等）和 **域名**（SNI/Host）。
可能影响 WeChat 的媒体加载。默认开启。\

**示例：**

```
sniffing-enable: [String] 
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
sniffing-enable: 1
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#sniffing-enable: 1
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>禁止折叠订阅</summary>

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

该功能会禁用折叠订阅的能力：服务器列表始终以展开状态完整显示。\

**示例：**

```
subscriptions-collapse: [String] 
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscriptions-collapse: 1
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#subscriptions-collapse: 1
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Ping 展示模式</summary>

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

允许以图标代替时间数值显示。\

**示例：**

```
ping-result: [time,icon]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
ping-result: icon
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#ping-result: icon
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Mux</summary>

xray-core 中的 Mux 是一种复用功能，可将多个虚拟 TCP 连接的数据通过单个物理 TCP 连接传输。其目的是减少 TCP 握手带来的延迟，并非提升吞吐量（大文件下载甚至可能变慢）。在出站（outbound）中配置，常用参数如 enabled 与 concurrency（最小 -1，最大 1024）。

**示例：**

```
mux-enable: [true / 1]
mux-tcp-connections: [String]
mux-xudp-connections: [String]
mux-quic: [String]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

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

{% code title="通过订阅正文：" %}

```
#mux-enable: 1
#mux-tcp-connections: 100
#mux-xudp-connections: 200
#mux-quic: skip
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Proxy \ TUN 模式（仅限 Desktop）</summary>

必须 <mark style="color:$warning;">**二选一**</mark>！这两个参数决定添加/更新订阅时的连接类型。

**示例：**

```
proxy-enable: [true / 1]
tun-enable: [true / 1]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
proxy-enable: 1
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#proxy-enable: 1
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>TUN 模式（仅限 Desktop）</summary>

决定 TUN 连接所使用的模式。

* **`system`** —— 使用操作系统的系统网络栈。
  速度快、效率高，但依赖于正确的路由与防火墙配置。
* **`gvisor`** —— gVisor 用户态网络栈。
  更少依赖内核规则，与 iptables/nftables/Docker 冲突更少，隔离性更好；性能可能略有下降。

**示例：**

```
tun-mode: [system,gvisor]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
tun-mode: gvisor
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#tun-mode: gvisor
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>选择隧道内核（仅限 Desktop）</summary>

决定 TUN 连接所使用的内核。可选：[sing-box](https://github.com/SagerNet/sing-box)、[tun2proxy](https://github.com/tun2proxy/tun2proxy)

**示例：**

```
tun-type: [singbox, tun2proxy]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
tun-type: tun2proxy
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#tun-type: tun2proxy
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Exclude routes</summary>

定义不应通过隧道转发的子网与 IP 地址。
地址需写在同一行，使用空格与逗号分隔。

**示例：**

```
exclude-routes: [String]
```

**传递方式：**

{% code title="通过 HTTP 头：" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
exclude-routes: 192.169.1.0/24, 10.0.0.0/8
```

{% endcode %}

{% code title="通过订阅正文：" %}

```
#exclude-routes: 192.169.1.0/24, 10.0.0.0/8
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>
