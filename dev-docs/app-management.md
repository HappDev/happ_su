---
description: 通过订阅管理应用程序设置
---

# 应用管理

**应用程序管理功能**包括两个部分:

* [标准参数](app-management.md#standartnye-parametry) — 适用于大多数面板的管理参数。
* [高级参数](app-management.md#id-rasshirennyifunkcional-opisanieparametrov) — 需要在订阅中指定 [Provider ID](provider-id.md) 才能使用。

若要启用参数,请传入值 `true` 或 `1`;若要禁用参数,请传入任意其他非空值(例如 `0` 或 `false`)。

## 标准参数

<details>

<summary>订阅自动更新</summary>

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

系统将创建一个任务,按指定的时间间隔执行该操作。根据内部优先级,系统会尝试在指定时间启动订阅更新。\
如果由于某种原因在指定时间间隔内未执行更新,则会在下次启动应用程序时自动进行。\
时间间隔以小时为单位设置,且必须为整小时的倍数。

**该参数的配置示例:**

```
profile-update-interval: [int]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-update-interval: 1
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#profile-update-interval: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>订阅名称</summary>

订阅配置文件的名称。可以以纯文本形式或 base64(UTF-8)形式传递。**限制**:最大长度 — 25 个字符。

通过订阅正文传递时,需在参数前加 `#` 符号(例如 `#profile-title`)。

**该参数的配置示例:**

```
profile-title: [string]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-title: Name VPN
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#profile-title: Name VPN
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>订阅状态栏(流量、到期日期)</summary>

显示余额、已用流量和订阅到期日期的信息。\
在应用程序中,状态栏左侧显示已用流量(上传 + 下载),右侧在 "/" 符号后显示总流量(total)。\
订阅到期日期在 **expire** 参数中指定。\
\*\*注意:\*\*所有数据通过一个 header 传输,并以 **;** 符号分隔。

**该参数的配置示例:**

```
subscription-userinfo: [string]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-userinfo: upload=0; download=2153701362; total=0; expire=1790951622
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#subscription-userinfo: upload=0; download=2153701362; total=0; expire=1790951622
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>支持页面链接</summary>

跳转到支持页面的按钮。\
以位于状态栏右侧的蓝色图标显示。\
如果链接指向 Telegram,则显示 Telegram 图标;其他情况下使用标准链接图标。

**该参数的配置示例:**

```
support-url: [string]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
support-url: https://t.me/happ_chat
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#support-url: https://t.me/happ_chat
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>网站页面链接</summary>

跳转到订阅网站页面的按钮。\
以位于状态栏左侧的蓝色图标显示。\
如果未设置该参数,图标将显示为灰色。

**该参数的配置示例:**

```
profile-web-page-url: [string]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-web-page-url: https://happ.su
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#profile-web-page-url: https://happ.su
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>公告</summary>

订阅可以包含公告文本,以 **plain text** 或 **Base64** 格式传递。\
\*\*限制:\*\*显示文本的最大长度 — **200 个字符**。

**该参数的配置示例:**

```
announce: [string]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
announce: base64:SGFwcCB0aGUgYmVzdCE=
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#announce: base64:SGFwcCB0aGUgYmVzdCE=
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>禁用路由</summary>

用于在应用程序中全局禁用路由的参数。

**该参数的配置示例:**

```
routing-enable: [string]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
routing-enable: 0
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#routing-enable: 0
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>隧道配置(仅限 Desktop)</summary>

为 sing-box 核心传递您自己的隧道配置。

**该参数的配置示例:**

```
custom-tunnel-config: [json]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
custom-tunnel-config: {...}
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#custom-tunnel-config: {...}
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>SOCKS Inbound 认证</summary>

定义本地 SOCKS 代理的工作模式和凭据。\\

* **auto** — 自动生成并将数据注入到配置和隧道中。
* **manual** — 使用在设置中设定的用户名和密码。
* **from-json** — 从 JSON 配置中获取设置。对于 URL 配置,此选项在此情景下等同于 auto 模式。
* **disable** — 禁用认证。

**参数:**

```
socks-auth-mode: [auto, manual, from-json, disable]
socks-auth-user: [String] — 登录名(用于 manual 模式)。
socks-auth-password: [String] — 密码(用于 manual 模式)。
```

**配置示例:**

```
socks-auth-mode: manual
socks-auth-user: myuser
socks-auth-password: mypassword
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
socks-auth-mode: manual
socks-auth-user: myuser
socks-auth-password: mypassword
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#socks-auth-mode: manual
#socks-auth-user: myuser
#socks-auth-password: mypassword
```
{% endcode %}

</details>

<details>

<summary>HTTP Inbound 认证</summary>

定义本地 HTTP 代理的工作模式和凭据。\\

* **auto** — 自动生成并将数据注入到配置和隧道中。
* **manual** — 使用在设置中设定的用户名和密码。
* **from-json** — 从 JSON 配置中获取设置。对于 URL 配置,此选项在此情景下等同于 auto 模式。
* **disable** — 禁用认证。

**参数:**

```
http-auth-mode: [auto, manual, from-json, disable]
http-auth-user: [String] — 登录名(用于 manual 模式)。
http-auth-password: [String] — 密码(用于 manual 模式)。
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
http-auth-mode: manual
http-auth-user: user1
http-auth-password: pass1
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#http-auth-mode: manual
#http-auth-user: user1
#http-auth-password: pass1
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

## 高级参数 <a href="#id-rasshirennyifunkcional-opisanieparametrov" id="id-rasshirennyifunkcional-opisanieparametrov"></a>

{% hint style="warning" %}
[Provider ID](provider-id.md) 参数为必填项!
{% endhint %}

<details>

<summary>更改订阅 URL</summary>

如果域名被您的提供商封锁,用户只能通过 VPN 才能连接服务器和更新订阅,则此参数正是为您准备的。通过在此参数值中指定一个新的域名,您将确保它自动替换为所有订阅用户使用。

**该参数的配置示例:**

```
new-url: [url]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
new-url: https://mynew-domain.com/3J3jrb4jfc
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#new-url: https://mynew-domain.com/3J3jrb4jfc
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>更改订阅域名</summary>

在不更改完整 URL 的情况下更改站点域名,保留地址的其余部分。

**该参数的配置示例:**

```
new-domain: [domain]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
new-domain: mynew-domain.com
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#new-domain: mynew-domain.com
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Fallback URL(备用订阅 URL)</summary>

如果主 URL 不可用、返回 300–599 错误或 9 秒内未响应,应用程序将切换到 Fallback URL(如果可用)。

**该参数的配置示例:**

```
fallback-url: [url]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
fallback-url: https://mynew-domain.com/3J3jrb4jfc
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#fallback-url: https://mynew-domain.com/3J3jrb4jfc
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>订阅中的服务器描述</summary>

允许您设置一个附加说明文字,显示在服务器名称下方,代替默认文本(例如 "VMess"、"VLESS"、"Trojan")。

* 最大长度 — 30 个字符。
* 如果屏幕上显示不下,将以省略号截断。
* 在 `title` 之后,使用 `?` 分隔符进行设置。

**示例:**

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

<summary>高级公告</summary>

更加醒目的公告。分为两种类型:任意的信息文本(`sub-info`)和订阅到期的系统通知(`sub-expire`)。

订阅到期通知具有优先级,会在到期前 3 天或到期后自动显示。信息块仅在没有正在显示的 expire 消息时才显示。

{% hint style="info" %}
要禁用通过 HTTP 标头或推送激活的公告，请发送值 0。
{% endhint %}

| META PARAM KEY         | 类型      | 必填  | 限制 / 取值                 | 描述                                           |
| ---------------------- | ------- | --- | ----------------------- | -------------------------------------------- |
| sub-info-color         | String  | 否   | red、blue、green(默认 blue) | 信息块的颜色                                       |
| sub-info-text          | String  | 是\* | 最长 200 个字符              | 信息块的主文本。没有此参数时,块不显示。或向该参数传 0 时也不显示。空字符串会禁用显示 |
| sub-info-button-text   | String  | 否   | 最长 25 个字符               | 按钮文字。如果缺失 — 不显示按钮                            |
| sub-info-button-link   | String  | 否   | 任意字符串(URL / deeplink)   | 按钮链接。在浏览器中打开,不做校验                            |
| sub-expire             | Boolean | 否   | true \| 1 = 启用          | 启用订阅到期信息显示机制                                 |
| sub-expire-button-link | String  | 否   | 任意字符串(URL / deeplink)   | "续订"按钮的链接。没有链接则不显示按钮                         |

#### 显示逻辑(摘要)

| 条件                              | 结果                   |
| ------------------------------- | -------------------- |
| sub-expire = true 且订阅在 ≤ 3 天内到期 | 显示消息"您的订阅将在 N 天后到期。" |
| sub-expire = true 且订阅已到期        | 显示消息"订阅已到期!"         |
| sub-expire = true 且天数 > 3       | 到期消息被隐藏              |
| 没有到期日期                          | 不显示到期信息              |
| 存在正在显示的 expire 消息               | sub-info 块不显示        |
| 没有 expire 消息且存在 sub-info-text   | 显示 sub-info 块        |
| sub-info-text = 0               | sub-info 块被禁用        |
| sub-expire ≠ true \| 1          | expire 机制被禁用         |

#### 说明

| 说明                            |
| ----------------------------- |
| 这些参数仅对传入它们的订阅生效               |
| 如果参数是通过推送传入且未被显式禁用,它们将无限期保持激活 |
| expire 按钮的文字始终为"Renew(续订)"    |
| 天数(N)按完整天数计算,最大为 3            |

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
sub-expire: 1
sub-expire-button-link: https://t.me/generate
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#sub-expire: 1
#sub-expire-button-link: https://t.me/generate
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>订阅分片与 Fronting</summary>

部分 CDN 支持 domain fronting。这允许通过第三方域名连接到您的站点。

例如,指定连接地址为 `visa.com`,并在 Host header 中设置 `my-domain.com`,提供商只会看到对 `visa.com` 的请求。

您还可以通过 SNI TLSHello 中的数据包分片(fragmentation)访问您的域名以获取服务器列表。

默认情况下,所有订阅均启用分片。

#### 带参数的 URL 方案

```
[link]#title?[fragment]&[resolve-address]&[host]&[insecure]

Fronting:
visa.com/123#MyVPN?resolve-address=visa.com&host=mydomain.com

Fragmentation:
mydomain.com/123#MyVPN?fragment=80-250,10-100,tlshello
```

Fragmentation 包含三个参数:`[length]`、`[interval]` 和 `[packets]`。

使用 fronting 时,必须先指定通过其进行连接的 URL 域名。还必须设置 `resolve-address` — 可以是域名或 IP 地址 — 以及 `host`,需要与所选提供商网络中的主机匹配。

</details>

<details>

<summary>No Limit 模式</summary>

No Limit 模式可用于所有类型的协议,或仅用于 xhttp。提高 xray-core 的 RAM 限制,从而提高稳定性和性能。

> 重要:该功能处于 beta 测试阶段。仅使用其中一种启用选项(全部启用或仅 xhttp 启用)— 不允许同时启用两者。

**该参数的配置示例:**

```
no-limit-enabled: [true / 1]
no-limit-xhttp-enabled: [true / 1]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
no-limit-xhttp-enabled: 1
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#no-limit-xhttp-enabled: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>高级分片</summary>

此功能目前处于封闭测试阶段,即将推出……

</details>

<details>

<summary>不可关闭的 HWID</summary>

默认情况下,所有 Happ 应用程序都启用了 HWID。但如果您希望用户无法通过在应用程序设置中关闭该参数来停止转发,可以在订阅中一并传递一个特殊参数。

**该参数的配置示例:**

```
subscription-always-hwid-enable: [true / 1]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-always-hwid-enable: 1
```
{% endcode %}

{% code title="通过订阅正文:" %}
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
用户将在订阅到期前 3 天收到提醒:应用程序将在三天内每天发送一条通知。这有助于用户及时续订。

通知文本:

```
Your subscription [name] is about to expire, don't forget to renew it.
```

**该参数的配置示例:**

```
notification-subs-expire: [true / 1]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
notification-subs-expire: 1
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#notification-subs-expire: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>隐藏订阅中的服务器设置</summary>

禁止订阅用户查看和编辑服务器配置。该设置同时适用于已添加的订阅以及将来添加的订阅。

**该参数的配置示例:**

```
hide-settings: [true / 1]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
hide-settings: 1
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#hide-settings: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>域名解析</summary>

应用程序可以在建立连接之前预先解析服务器域名。\
您可以指定任意 DoH 服务器,连接到 Xray 服务器时,域名将被替换为获取到的 IP 地址。

如果某个域名返回多个 IP 地址,应用程序会自动选择响应时间(ping)最短的那个。\
不过请注意:当 IP 地址数量较多时,连接可能需要更长时间,因为会预先测试所有选项。

**该参数的配置示例:**

```
server-address-resolve-enable: [true / 1]
server-address-resolve-dns-domain: [url]
server-address-resolve-dns-ip: [ip]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
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

{% code title="通过订阅正文:" %}
```
#server-address-resolve-enable: 1
#server-address-resolve-dns-domain: https://common.dot.dns.yandex.net/dns-query
#server-address-resolve-dns-ip: 77.88.8.8
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

## 应用程序设置管理 <a href="#upravlenie-nastroikami-prilozheniya" id="upravlenie-nastroikami-prilozheniya"></a>

{% hint style="warning" %}
[Provider ID](provider-id.md) 参数为必填项!
{% endhint %}

<details>

<summary>自动连接</summary>

允许在应用程序启动时自动连接到服务器。\
此外,通过 **subscription-autoconnect-type** 参数,您可以指定连接到特定服务器的准则。

**该参数的配置示例:**

```
subscription-autoconnect: [true / 1]
subscription-autoconnect-type: [lastused/lowestdelay/random]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
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

{% code title="通过订阅正文:" %}
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

在打开应用程序时(如有必要)自动对服务器列表进行测试。

**该参数的配置示例:**

```
subscription-ping-onopen-enabled: [true / 1]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-ping-onopen-enabled: 1
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#subscription-ping-onopen-enabled: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>所有订阅自动更新</summary>

在应用程序中,您可以一次性启用或禁用所有订阅的自动更新 — 该设置同时应用于所有订阅。如果只需要为特定订阅设置自动更新,请使用"订阅自动更新"功能。当全局设置被禁用时,每个订阅自行决定更新时间。

**该参数的配置示例:**

```
subscription-auto-update-enable: [true / 1] 
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-auto-update-enable: 1
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#subscription-auto-update-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>分片与噪声</summary>

这是所有订阅的全局分片管理参数。如果只需要为特定订阅或服务器分配分片,请使用免费功能和应用程序的通用文档说明。当全局设置被禁用时,每个订阅自行决定其分片设置。

**该参数的配置示例:**

```
fragmentation-enable: [true / 1]
fragmentation-packets: [tlshello,1-2,1-3,1-5]
fragmentation-length: [50-100]
fragmentation-interval: [10-20]
fragmentation-maxsplit: [String]
noises-enable: [true / 1] — 启用/禁用噪声。
noises-packet-type: [array, str, hex, base64] — 传输的数据类型(默认:array)。
noises-packet: [String] — 噪声的固定数据。以逗号分隔的字符串列表。
noises-delay: [String] — 发送噪声信号之间的延迟(毫秒)。
noises-rand: [String] — 添加随机字节或设置其长度(例如 "1-8192")。
noises-rand-range: [String] — 随机字节值范围(默认:"0-255")。
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
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
noises-enable: true
noises-packet-type: base64
noises-packet: 7nQBAAABAAAAAAAABnQtcmluZwZtc2VkZ2UDbmV0AAABAAE=
noises-delay: 50
noises-rand: 1-1024
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#fragmentation-enable: 1
#fragmentation-packets: tlshello
#fragmentation-length: 50-100
#fragmentation-interval: 5
#fragmentation-maxsplit: 100-200
#noises-enable: true
#noises-packet-type: base64
#noises-packet: 7nQBAAABAAAAAAAABnQtcmluZwZtc2VkZ2UDbmV0AAABAAE=
#noises-delay: 50
#noises-rand: 1-1024
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Ping</summary>

此功能允许您选择应用程序中执行 ping 的方式。\
有四个可用选项:

* **via Proxy - GET**
* **via Proxy - HEAD**
* **TCP**
* **ICMP** 对于"via Proxy"模式,您还可以额外指定用于 ping 检查的 URL。

**该参数的配置示例:**

```
ping-type: [proxy, proxy-head, tcp, icmp]
check-url-via-proxy: [url]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
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

{% code title="通过订阅正文:" %}
```
#ping-type: proxy
#check-url-via-proxy: https://cp.cloudflare.com/generate_204
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>User-Agent</summary>

此功能允许您更改获取订阅时在 headers 中使用的 User-Agent。适用于提供商屏蔽带有非标准或不合适 headers 请求的情况。

**该参数的配置示例:**

```
change-user-agent: [String] 
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
change-user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/135.0.0.0 Safari/537.36
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#change-user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/135.0.0.0 Safari/537.36
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>应用程序自启动</summary>

此功能允许在设备开机时自动启动应用程序。目前仅在 Android 上可用。

**该参数的配置示例:**

```
app-auto-start: [String] 
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
app-auto-start: 1
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#app-auto-start: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>启动应用程序时更新订阅</summary>

此功能在每次打开应用程序时自动更新所有订阅。

**该参数的配置示例:**

```
subscription-auto-update-open-enable: [String] 
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-auto-update-open-enable: 1
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#subscription-auto-update-open-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>指定应用程序的代理(Android)</summary>

在此参数中,您可以指定应使用 VPN 或相反绕过 VPN 的应用程序列表。如果列出的应用程序尚未安装到设备上,则会在首次安装后的 VPN 连接时自动纳入考虑。

**该参数的配置示例:**

```
per-app-proxy-mode: [off/on/bypass] \\指定这三个参数之一
per-app-proxy-list: [com.google.chrome,com.meta.instagram] \\以 ',' 分隔的 appID 列表
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
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

{% code title="通过订阅正文:" %}
```
#per-app-proxy-mode: on
#per-app-proxy-list: com.google.chrome,com.meta.instagram
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>指定应用程序的代理(反选,Android)</summary>

在此参数中,您可以指定应使用 VPN 或相反绕过 VPN 的应用程序列表。\
**选中除列表中指定之外的所有应用程序。**

**该参数的配置示例:**

```
per-app-proxy-mode: [off/on/bypass] \\指定这三个参数之一
per-app-proxy-list-invert: [com.google.chrome,com.meta.instagram] \\以 ',' 分隔的 appID 列表
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
per-app-proxy-mode: on
per-app-proxy-list-invert: com.google.chrome,com.meta.instagram
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#per-app-proxy-mode: on
#per-app-proxy-list-invert: com.google.chrome,com.meta.instagram
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>指定应用程序的代理(覆盖设置,Android)</summary>

在此参数中,您可以指定应使用 VPN 或相反绕过 VPN 的应用程序列表。\
**清除当前所有已选的应用程序,然后仅从指定列表中选择应用程序。**

**该参数的配置示例:**

```
per-app-proxy-mode: [off/on/bypass] \\指定这三个参数之一
per-app-proxy-list-set: [com.google.chrome,com.meta.instagram] \\以 ',' 分隔的 appID 列表
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
per-app-proxy-mode: on
per-app-proxy-list-set: com.google.chrome,com.meta.instagram
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#per-app-proxy-mode: on
#per-app-proxy-list-set: com.google.chrome,com.meta.instagram
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>数据包分析(Sniffing)</summary>

在 **xray-core** 中,sniffing 用于分析连接的前几个数据包,并自动识别**协议**(HTTP、TLS、BitTorrent 等)和**域名**(SNI/Host)。\
它可能会影响 WeChat 应用中的媒体加载。默认已启用。<br>

**该参数的配置示例:**

```
sniffing-enable: [String] 
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
sniffing-enable: 1
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#sniffing-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>禁用订阅折叠</summary>

此功能禁用订阅折叠能力:服务器列表始终完整显示,处于展开视图。<br>

**该参数的配置示例:**

```
subscriptions-collapse: [false / 0]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscriptions-collapse: 0
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#subscriptions-collapse: 0
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>强制展开订阅</summary>

通过订阅更新接收到此参数时,如果订阅处于折叠状态,应用程序将强制将其展开。值 `false` 会被忽略:此参数仅用于展开,不能用它来折叠订阅。

**该参数的配置示例:**

```
subscriptions-expand-now: [true / 1]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscriptions-expand-now: 1
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#subscriptions-expand-now: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Ping 显示模式</summary>

允许使用图标代替时间值进行显示。<br>

**该参数的配置示例:**

```
ping-result: [time,icon]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
ping-result: icon
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#ping-result: icon
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Mux</summary>

xray-core 中的 Mux 是一项多路复用功能,允许将来自多个虚拟 TCP 连接的数据通过单个物理 TCP 连接传输。其设计目的是减少 TCP 握手的延迟,而不是提高吞吐量(甚至可能降低大文件下载的速度)。在 outbound 配置中进行设置,包含 enabled 和 concurrency(最小 -1,最大 1024)等参数。

**该参数的配置示例:**

```
mux-enable: [true / 1]
mux-tcp-connections: [String]
mux-xudp-connections: [String]
mux-quic: [String]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
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

{% code title="通过订阅正文:" %}
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

<summary>Proxy \ TUN 模式(仅限 Desktop)</summary>

必须<mark style="color:$warning;">**只使用**</mark>这两个参数中的其中之一!这些参数决定添加/更新订阅时的连接类型。

**该参数的配置示例:**

```
proxy-enable: [true / 1]
tun-enable: [true / 1]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
proxy-enable: 1
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#proxy-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>TUN 模式(仅限 Desktop)</summary>

决定 TUN 连接使用哪种模式。

* **`system`** — 使用操作系统的系统网络栈。\
  快速高效,但依赖于路由和防火墙的正确配置。
* **`gvisor`** — 用户空间的 gVisor 栈。\
  对内核规则以及与 iptables/nftables/Docker 冲突的依赖更少,具有更好的隔离性;可能略有性能下降。

**该参数的配置示例:**

```
tun-mode: [system,gvisor]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
tun-mode: gvisor
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#tun-mode: gvisor
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>隧道核心选择(仅限 Desktop)</summary>

决定 TUN 连接使用哪种核心。可用选项:\\

* [sing-box](https://github.com/SagerNet/sing-box)
* [tun2proxy](https://github.com/tun2proxy/tun2proxy)
* default(Happ TUN)— 我们自己实现的隧道

**该参数的配置示例:**

```
tun-type: [singbox, tun2proxy, default]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
tun-type: tun2proxy
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#tun-type: tun2proxy
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Exclude Routes(排除的路由)</summary>

定义一组子网和 IP 地址,这些地址的流量不得通过隧道传输。\
地址以单行指定,使用空格和逗号分隔。

**该参数的配置示例:**

```
exclude-routes: [String]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
exclude-routes: 192.168.1.0/24, 10.0.0.0/8
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#exclude-routes: 192.169.1.0/24, 10.0.0.0/8
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Exclude Routes Set(设置排除的路由)</summary>

定义一组子网和 IP 地址,这些地址的流量不得通过隧道传输。\
地址以单行指定,使用空格和逗号分隔。\
**设置之前会清空当前列表。**

**该参数的配置示例:**

```
exclude-routes-set: [String]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
exclude-routes-set: 192.169.1.0/24, 10.0.0.0/8
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#exclude-routes-set: 192.169.1.0/24, 10.0.0.0/8
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>主题(仅限 iOS)</summary>

允许您将配色主题更改为个性化主题。您可以在编辑器中创建自己的主题 — 长按"Appearance theme(外观主题)"标签以打开菜单。创建的主题可以导出到剪贴板,也可以从剪贴板、`.happ` 文件或通过订阅导入。

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

**该参数的配置示例:**

```
color-profile: [String] //base64 或 plainString
color-profile: resetcolors // 完全重置
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
color-profile: {"backgroundGradientRotationAngle":37.1,"serverRowBackgroundColor":"#21003D67","subsHeaderColor":"#42296DFF","profileWebPageIconColor":"#A2B8FFFF","selectedServerRowColor":"#3E2F62B5","disclosureSubHeaderTextColor":"#C1C2E2FF","buttonTextColor":"#FFFFFFFF","buttonTimerColor":"#FFFFFFFF","subscriptionInfoBackgroundColor":"#21003CFF","backgroundColors":["#3D2A7DFF","#6557BAFF","#9377FF7F"],"disclosureHeaderTextColor":"#FFFFFFFF","backgroundGradientColorIntensity":1,"additionalOptionsButtonColor":"#FFFFFFFF","buttonImageType":"light","serverRowSubTitleTextColor":"#C1C2E2FF","supportIconColor":"#FFFFFFFF","topBarButtonsColor":"#FFFFFFFF","subscriptionTrafficBackgroundColor":"#533EA7FF","subHeaderButtonColor":"#FFFFFFFF","buttonColor":"#9377FFFF","powerIconColor":"#3D2A7DFF","subscriptionInfoTextColor":"#FFFFFFFF","serverRowTitleTextColor":"#FFFFFFFF","backgroundImageType":"system","elipseColors":["#00B460FF","#CF72FFE0","#FFDD00FF"],"serverRowChevronColor":"#FFFFFFFF"}
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#color-profile: {"backgroundGradientRotationAngle":37.1,"serverRowBackgroundColor":"#21003D67","subsHeaderColor":"#42296DFF","profileWebPageIconColor":"#A2B8FFFF","selectedServerRowColor":"#3E2F62B5","disclosureSubHeaderTextColor":"#C1C2E2FF","buttonTextColor":"#FFFFFFFF","buttonTimerColor":"#FFFFFFFF","subscriptionInfoBackgroundColor":"#21003CFF","backgroundColors":["#3D2A7DFF","#6557BAFF","#9377FF7F"],"disclosureHeaderTextColor":"#FFFFFFFF","backgroundGradientColorIntensity":1,"additionalOptionsButtonColor":"#FFFFFFFF","buttonImageType":"light","serverRowSubTitleTextColor":"#C1C2E2FF","supportIconColor":"#FFFFFFFF","topBarButtonsColor":"#FFFFFFFF","subscriptionTrafficBackgroundColor":"#533EA7FF","subHeaderButtonColor":"#FFFFFFFF","buttonColor":"#9377FFFF","powerIconColor":"#3D2A7DFF","subscriptionInfoTextColor":"#FFFFFFFF","serverRowTitleTextColor":"#FFFFFFFF","backgroundImageType":"system","elipseColors":["#00B460FF","#CF72FFE0","#FFDD00FF"],"serverRowChevronColor":"#FFFFFFFF"}
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>包含所有网络(仅限 iOS)</summary>

在隧道(NetworkExtension)中启用所有网络的使用。该功能从 iOS 16.4 开始提供。\
在更低 iOS 版本的设备上,此参数将不产生任何效果,DevSettings 中也不会出现相应的开关。

**该参数的配置示例:**

```
include-all-networks-enable: [true / 1]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
include-all-networks-enable: true
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#include-all-networks-enable: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>排除本地网络(仅限 iOS)</summary>

如果启用了"包含所有网络"选项,此参数允许从隧道(NetworkExtension)中排除本地网络。\
本地网络流量将直连。适用于 iOS 16.4+。

**该参数的配置示例:**

```
exclude-local-networks-enable: [true / 1]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
exclude-local-networks-enable: true
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#exclude-local-networks-enable: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>排除 APNS(仅限 iOS)</summary>

如果启用了"包含所有网络"选项,此参数允许从隧道中排除 Apple Push Notification Service(APNS)。\
所有 Apple 通知 IP 范围将直连。适用于 iOS 16.4+。

**该参数的配置示例:**

```
exclude-apns-enable: [true / 1]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
exclude-apns-enable: true
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#exclude-apns-enable: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>不使用服务器列表过滤</summary>

Premium 订阅中默认启用自动过滤:\\

* 如果服务器名称包含"only WiFi" — 仅在通过 Wi-Fi 连接时可见。
* 如果名称包含"only Mobile" — 仅在移动网络时可见。 此选项禁用该行为。

**该参数的配置示例:**

```
dont-use-filter: [true / 1]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
dont-use-filter: true
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#dont-use-filter: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>置顶当前订阅</summary>

允许在总列表中置顶(Pin)或取消置顶订阅。\\

* true — 将订阅置顶。
* false — 取消置顶。

**该参数的配置示例:**

```
subscription-pin: [true / 1]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
subscription-pin: true
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#subscription-pin: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>阻止更改 User-Agent</summary>

阻止用户通过应用程序界面手动更改 **User-Agent**。\
但提供商仍然可以通过 **change-user-agent** 参数远程更改它。

**该参数的配置示例:**

```
manual-block-user-agent: [true / 1]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
manual-block-user-agent: true
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#manual-block-user-agent: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>更改订阅内的服务器排序</summary>

决定订阅内服务器的显示顺序:

* **without** — 不排序(按照后端的传递顺序)。
* **ping** — 按延迟排序(ping 低的服务器显示在前,不可用的显示在最后)。
* **alphabet** — 按字母顺序。

**该参数的配置示例:**

```
subscriptions-sort-type: [without, ping, alphabet]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
subscriptions-sort-type: ping
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#subscriptions-sort-type: ping
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>从 JSON 获取隧道 DNS</summary>

仅当同时满足以下所有条件时,该逻辑才会生效:使用 JSON 配置、\
没有路由配置文件,并且在设置中启用了该开关。\
系统会从 JSON 中 `dns.servers` 的第一个服务器获取。

选择算法:

* **直接 IP**:如果指定了 IPv4/IPv6,将其设置为隧道的 DOU DNS。
* **DoH**:如果指定了 URL(https://),则在 `dns.hosts` 中查找 IP。
  * iOS:配置完整的 DoH 请求。
  * Android / Desktop:使用 hosts 中的 IP(DOU)。
* **对象**:从 `address` 字段中提取值,与上述描述类似。
* **Fallback DNS**:\
  如果主服务器无效,则使用默认值:
  * Android / Desktop:1.1.1.1(DOU)。
  * iOS:Cloudflare DoH(https://cloudflare-dns.com/dns-query)。

**该参数的配置示例:**

```
dns-from-json-enable: [true / 1]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
HTTP/2 200 
dns-from-json-enable: true
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#dns-from-json-enable: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>下载 geo 文件的 User-Agent</summary>

允许在下载 Geo-IP 和 Geo-Site 文件时更改 User-Agent 头的值。

**可用值:**

* **safari-mac**
* **chrome-win**
* **safari-ios**
* **firefox-win**
* **chrome-android**

**配置示例:**

```
user-agent-geo-files: safari-mac
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
user-agent-geo-files: chrome-win
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#user-agent-geo-files: chrome-win
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>代理 ping 超时(仅限 iOS)</summary>

设置通过代理服务器检查可用性(ping)时的超时时间(秒)。\
允许范围:**5 – 15** 秒。\
超出范围的值将被忽略,并使用默认值 7。

**配置示例:**

```
proxy-ping-timeout: 10
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
proxy-ping-timeout: 10
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#proxy-ping-timeout: 10
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>隐藏 VPN 图标(Hide Proxy Icon)</summary>

控制系统状态栏中 VPN 图标的显示。\
该开关会对排除路由列表(excluded-routes)中是否同时存在这两条路由(::/128 和 0.0.0.0/8)做出反应。\
启用该选项时,这两条路由会被自动添加到排除列表中;禁用时,它们会被移除。

**配置示例:**

```
hide-vpn-icon: [true / 1]
```

**传递方式:**

{% code title="通过 HTTP Headers:" %}
```
hide-vpn-icon: true
```
{% endcode %}

{% code title="通过订阅正文:" %}
```
#hide-vpn-icon: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>
