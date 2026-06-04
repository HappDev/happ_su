---
description: Manage application settings through the subscription
---

# App management

**The app management feature** includes two areas:

* [Standard parameters](app-management.md#standartnye-parametry) for management, which work for most panels.
* [Advanced parameters](app-management.md#id-rasshirennyifunkcional-opisanieparametrov) that require a [Provider ID](provider-id.md) to be specified in the subscription.

To enable a parameter, pass the value `true` or `1`; to disable it, pass any other non-empty value (for example, `0` or `false`).

## Standard parameters

<details>

<summary>Subscription auto-update</summary>

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

The system creates a task to perform the operation at a given interval. Depending on internal priorities, the system tries to start the subscription update at the specified time.\
If for some reason the update was not performed within the specified interval, it will happen automatically on the next application launch.\
The interval is set in hours and must be a multiple of one hour.

**Example of configuring this parameter:**

```
profile-update-interval: [int]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-update-interval: 1
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#profile-update-interval: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Subscription name</summary>

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

The name of the subscription profile. It can be passed as plain text or in base64 (UTF-8). **Restriction**: maximum length — 25 characters.

Via the subscription body, by specifying the `#` sign before the parameter (for example, `#profile-title`).

**Example of configuring this parameter:**

```
profile-title: [string]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-title: Name VPN
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#profile-title: Name VPN
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Subscription status line (traffic, expiration date)</summary>

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Displays information about the balance, used traffic volume, and subscription expiration date.\
In the app, the left side of the bar shows the amount of used traffic (upload + download), and the right side — the total volume (total) after the "/" symbol.\
The subscription expiration date is specified in the **expire** parameter.\
**Note:** all data is transmitted in a single header and separated by the **;** symbol.

**Example of configuring this parameter:**

```
subscription-userinfo: [string]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-userinfo: upload=0; download=2153701362; total=0; expire=1790951622
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#subscription-userinfo: upload=0; download=2153701362; total=0; expire=1790951622
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Link to the support page</summary>

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

Button to go to the support page.\
Displayed as a blue icon located on the right side of the bar.\
If the link leads to Telegram, the Telegram icon is displayed; in other cases, the standard link icon is used.

**Example of configuring this parameter:**

```
support-url: [string]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
support-url: https://t.me/happ_chat
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#support-url: https://t.me/happ_chat
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Link to the website page</summary>

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Button to go to the subscription website page.\
Displayed as a blue icon located on the left side of the bar.\
If the parameter is not set, the icon will be gray.

**Example of configuring this parameter:**

```
profile-web-page-url: [string]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-web-page-url: https://happ.su
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#profile-web-page-url: https://happ.su
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Announcement</summary>

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

The subscription can contain announcement text, passed in **plain text** or **Base64** format.\
**Restriction:** maximum length of displayed text — **200 characters**.

**Example of configuring this parameter:**

```
announce: [string]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
announce: base64:SGFwcCB0aGUgYmVzdCE=
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#announce: base64:SGFwcCB0aGUgYmVzdCE=
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Disable routing</summary>

A global parameter for disabling routing in the application.

**Example of configuring this parameter:**

```
routing-enable: [string]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
routing-enable: 0
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#routing-enable: 0
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Tunnel configuration (Desktop only)</summary>

Pass your own tunnel configuration for the sing-box core.

**Example of configuring this parameter:**

```
custom-tunnel-config: [json]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
custom-tunnel-config: {...}
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#custom-tunnel-config: {...}
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>SOCKS Inbound authentication</summary>

Defines the operating mode and credentials for the local SOCKS proxy.\\

* **auto** — automatic generation and injection of data into configs and the tunnel.
* **manual** — uses the user and password set in the settings.
* **from-json** — takes settings from the JSON configuration. For URL configs, it works as auto mode in this selection.
* **disable** — disables authentication.

**Parameters:**

```
socks-auth-mode: [auto, manual, from-json, disable]
socks-auth-user: [String] — login (for manual mode).
socks-auth-password: [String] — password (for manual mode).
```

**Example configuration:**

```
socks-auth-mode: manual
socks-auth-user: myuser
socks-auth-password: mypassword
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
socks-auth-mode: manual
socks-auth-user: myuser
socks-auth-password: mypassword
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#socks-auth-mode: manual
#socks-auth-user: myuser
#socks-auth-password: mypassword
```
{% endcode %}

</details>

<details>

<summary>HTTP Inbound authentication</summary>

Defines the operating mode and credentials for the local HTTP proxy.\\

* **auto** — automatic generation and injection of data into configs and the tunnel.
* **manual** — uses the user and password set in the settings.
* **from-json** — takes settings from the JSON configuration. For URL configs, it works as auto mode in this selection.
* **disable** — disables authentication.

**Parameters:**

```
http-auth-mode: [auto, manual, from-json, disable]
http-auth-user: [String] — login (for manual mode).
http-auth-password: [String] — password (for manual mode).
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
http-auth-mode: manual
http-auth-user: user1
http-auth-password: pass1
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#http-auth-mode: manual
#http-auth-user: user1
#http-auth-password: pass1
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

## Advanced parameters <a href="#id-rasshirennyifunkcional-opisanieparametrov" id="id-rasshirennyifunkcional-opisanieparametrov"></a>

{% hint style="warning" %}
The [Provider ID](provider-id.md) parameter is required!
{% endhint %}

<details>

<summary>Changing the subscription URL</summary>

If the domain is blocked by your provider, and users can connect to servers and update their subscription only via VPN, this parameter is exactly for you. By specifying a new domain name in the value of this parameter, you will ensure its automatic replacement for all subscription users.

**Example of configuring this parameter:**

```
new-url: [url]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
new-url: https://mynew-domain.com/3J3jrb4jfc
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#new-url: https://mynew-domain.com/3J3jrb4jfc
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Changing the subscription domain</summary>

Change the site domain without changing the full URL, preserving the rest of the address.

**Example of configuring this parameter:**

```
new-domain: [domain]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
new-domain: mynew-domain.com
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#new-domain: mynew-domain.com
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Fallback URL (backup subscription URL)</summary>

<figure><img src="../.gitbook/assets/image.png" alt="" width="375"><figcaption></figcaption></figure>

If the main URL is unavailable, returned an error 300–599, or did not respond within 9 seconds, the application will switch to the Fallback URL (if available).

**Example of configuring this parameter:**

```
fallback-url: [url]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
fallback-url: https://mynew-domain.com/3J3jrb4jfc
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#fallback-url: https://mynew-domain.com/3J3jrb4jfc
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Server description in the subscription</summary>

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

Allows you to set an additional caption that is displayed under the server name instead of the default text (for example, "VMess", "VLESS", "Trojan").

* Maximum length — 30 characters.
* If it does not fit on the screen, it will be truncated with an ellipsis.
* It is set after `title` using the `?` separator.

**Examples:**

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

<summary>Advanced announcements</summary>

<div><figure><img src="../.gitbook/assets/5526.png" alt="" width="188"><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/5528.png" alt="" width="188"><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/5527.png" alt="" width="188"><figcaption></figcaption></figure></div>

More prominent announcements. Split into two types: arbitrary informational text (`sub-info`) and a system notification about subscription expiration (`sub-expire`).

Subscription expiration notifications have priority and are displayed automatically 3 days before expiration or after it has expired. The info block is shown only when there is no active expire message.

{% hint style="info" %}
To disable an announcement activated via an HTTP header or push, send the value 0.
{% endhint %}

| META PARAM KEY         | TYPE    | REQUIRED | LIMITS / VALUES                 | DESCRIPTION                                                                                                                                             |
| ---------------------- | ------- | -------- | ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| sub-info-color         | String  | No       | red, blue, green (default blue) | Color of the info block                                                                                                                                 |
| sub-info-text          | String  | Yes\*    | max 200 chars                   | Main text of the info block. Without this parameter, the block is not displayed. Or if 0 is sent to the parameter. An empty string disables the display |
| sub-info-button-text   | String  | No       | max 25 chars                    | Button text. If missing — the button is not shown                                                                                                       |
| sub-info-button-link   | String  | No       | any string (URL / deeplink)     | Button link. Opens in a browser, without validation                                                                                                     |
| sub-expire             | Boolean | No       | true \| 1 = enabled             | Enables the mechanism for displaying subscription expiration info                                                                                       |
| sub-expire-button-link | String  | No       | any string (URL / deeplink)     | Link for the "Renew" button. Without a link, the button is not shown                                                                                    |

#### Display logic (summary)

| CONDITION                                              | RESULT                                                  |
| ------------------------------------------------------ | ------------------------------------------------------- |
| sub-expire = true and subscription expires in ≤ 3 days | Show the message "Your subscription expires in N days." |
| sub-expire = true and the subscription has expired     | Show the message "Subscription has expired!"            |
| sub-expire = true and days > 3                         | The expiration message is hidden                        |
| No expiration date                                     | Expiration info is not displayed                        |
| There is an active expire message                      | The sub-info block is not displayed                     |
| No expire message and sub-info-text exists             | Show the sub-info block                                 |
| sub-info-text = 0                                      | The sub-info block is disabled                          |
| sub-expire ≠ true \| 1                                 | The expire mechanism is disabled                        |

#### Notes

| NOTE                                                                                              |
| ------------------------------------------------------------------------------------------------- |
| The parameters apply only to the subscription for which they were passed                          |
| If the parameters came via push and were not explicitly disabled, they remain active indefinitely |
| The expire button always has the text "Renew"                                                     |
| The number of days (N) is counted as full days, maximum 3                                         |

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
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

{% code title="Via subscription body:" %}
```
#sub-expire: 1
#sub-expire-button-link: https://t.me/generate
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Subscription fragmentation and fronting</summary>

Some CDNs support domain fronting. This allows connecting to your site through a third-party domain.

For example, by specifying the connection address `visa.com`, and in the Host header — `my-domain.com`, the provider will only see the request to `visa.com`.

You can also access your domain to retrieve the server list using packet fragmentation in the SNI TLSHello.

By default, fragmentation is enabled for all subscriptions.

#### URL scheme with parameters

```
[link]#title?[fragment]&[resolve-address]&[host]&[insecure]

Fronting:
visa.com/123#MyVPN?resolve-address=visa.com&host=mydomain.com

Fragmentation:
mydomain.com/123#MyVPN?fragment=80-250,10-100,tlshello
```

Fragmentation contains three parameters: `[length]`, `[interval]`, and `[packets]`.

When using fronting, you must first specify the URL with the domain through which the connection will be made. You must also set `resolve-address` — this can be a domain or an IP address — and `host`, matching your host in the selected provider's network.

</details>

<details>

<summary>No Limit Mode</summary>

No Limit Mode can be used for all types of protocols or only for xhttp. Increases the RAM limit for xray-core, improving stability and performance.

> Important: The feature is in beta testing. Use only one of the activation options (for all or only for xhttp) — enabling both simultaneously is not allowed.

**Example of configuring this parameter:**

```
no-limit-enabled: [true / 1]
no-limit-xhttp-enabled: [true / 1]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
no-limit-xhttp-enabled: 1
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#no-limit-xhttp-enabled: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Advanced fragmentation</summary>

This feature is currently in closed testing and will be available soon...

</details>

<details>

<summary>Non-disableable HWID</summary>

By default, HWID is enabled on all Happ applications. But if you want the user to be unable to disable forwarding of this parameter by turning it off in the app settings, you can send a special parameter along with the subscription.

**Example of configuring this parameter:**

```
subscription-always-hwid-enable: [true / 1]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-always-hwid-enable: 1
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#subscription-always-hwid-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Subscription expiration notification</summary>

You can enable the automatic subscription expiration notifications feature.\
The user will receive reminders 3 days before the subscription expires: the app will send one notification per day for three days. This will help the user remember to renew the subscription on time.

Notification text:

```
Your subscription [name] is about to expire, don't forget to renew it.
```

**Example of configuring this parameter:**

```
notification-subs-expire: [true / 1]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
notification-subs-expire: 1
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#notification-subs-expire: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Hide server settings in the subscription</summary>

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

Disable the ability to view and edit server configurations for users of your subscription. The setting applies both to already added subscriptions and to those that will be added in the future.

**Example of configuring this parameter:**

```
hide-settings: [true / 1]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
hide-settings: 1
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#hide-settings: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Domain resolving</summary>

The app can pre-resolve server domains before establishing a connection.\
You can specify any DoH server, and when connecting to the Xray server, the domain name will be replaced with the received IP address.

If multiple IP addresses are returned for a domain, the app will automatically select the one with the minimum response time (ping).\
However, keep in mind: with a large number of IP addresses, the connection may take longer, as all options will be tested in advance.

**Example of configuring this parameter:**

```
server-address-resolve-enable: [true / 1]
server-address-resolve-dns-domain: [url]
server-address-resolve-dns-ip: [ip]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
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

{% code title="Via subscription body:" %}
```
#server-address-resolve-enable: 1
#server-address-resolve-dns-domain: https://common.dot.dns.yandex.net/dns-query
#server-address-resolve-dns-ip: 77.88.8.8
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

## Managing app settings <a href="#upravlenie-nastroikami-prilozheniya" id="upravlenie-nastroikami-prilozheniya"></a>

{% hint style="warning" %}
The [Provider ID](provider-id.md) parameter is required!
{% endhint %}

<details>

<summary>Auto-connect</summary>

Allows the user to be automatically connected to servers when the app is launched.\
Additionally, using the **subscription-autoconnect-type** parameter, you can specify a criterion for connecting to a particular server.

**Example of configuring this parameter:**

```
subscription-autoconnect: [true / 1]
subscription-autoconnect-type: [lastused/lowestdelay/random]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
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

{% code title="Via subscription body:" %}
```
#subscription-autoconnect: 1
#subscription-autoconnect-type: lastused
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Auto-ping</summary>

Run automatic testing of the server list when the app is opened, if necessary.

**Example of configuring this parameter:**

```
subscription-ping-onopen-enabled: [true / 1]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-ping-onopen-enabled: 1
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#subscription-ping-onopen-enabled: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Subscriptions auto-update</summary>

In the app, you can enable or disable auto-update for all subscriptions at once — this setting applies to all subscriptions simultaneously. If you need to set auto-update only for a specific subscription, use the Subscription auto-update feature. When the global setting is disabled, each subscription determines its own update time.

**Example of configuring this parameter:**

```
subscription-auto-update-enable: [true / 1] 
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-auto-update-enable: 1
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#subscription-auto-update-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Fragmentation and noises</summary>

This is a global fragmentation management parameter for all subscriptions. If you need to assign fragmentation only for a specific subscription or server, use the free functionality and the general documentation instructions for the app. When the global setting is disabled, each subscription determines its own fragmentation settings.

**Example of configuring this parameter:**

```
fragmentation-enable: [true / 1]
fragmentation-packets: [tlshello,1-2,1-3,1-5]
fragmentation-length: [50-100]
fragmentation-interval: [10-20]
fragmentation-maxsplit: [String]
noises-enable: [true / 1] — enable/disable noises.
noises-packet-type: [array, str, hex, base64] — type of data transmitted (default: array).
noises-packet: [String] — fixed data for the noise. A list of strings separated by commas.
noises-delay: [String] — delay between sending noise signals in milliseconds.
noises-rand: [String] — adds random bytes or sets their length (e.g., "1-8192").
noises-rand-range: [String] — range of random byte values (default: "0-255").
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
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

{% code title="Via subscription body:" %}
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

This feature allows you to choose how ping is performed in the app.\
Four options are available:

* **via Proxy - GET**
* **via Proxy - HEAD**
* **TCP**
* **ICMP** For the "via Proxy" mode, you can additionally specify a URL for the ping check.

**Example of configuring this parameter:**

```
ping-type: [proxy, proxy-head, tcp, icmp]
check-url-via-proxy: [url]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
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

{% code title="Via subscription body:" %}
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

This feature allows you to change the User-Agent used in headers when receiving the subscription. Useful in cases where the provider blocks requests with non-standard or inappropriate headers.

**Example of configuring this parameter:**

```
change-user-agent: [String] 
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
change-user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/135.0.0.0 Safari/537.36
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#change-user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/135.0.0.0 Safari/537.36
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>App autostart</summary>

This feature allows the app to start automatically when the device is turned on. Currently available only on Android.

**Example of configuring this parameter:**

```
app-auto-start: [String] 
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
app-auto-start: 1
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#app-auto-start: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Update subscription on app launch</summary>

This feature automatically updates all subscriptions in the app every time the app is opened.

**Example of configuring this parameter:**

```
subscription-auto-update-open-enable: [String] 
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-auto-update-open-enable: 1
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#subscription-auto-update-open-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Proxy for selected apps (Android)</summary>

In this parameter, you can specify a list of apps that should use the VPN or, conversely, bypass it. If the app is not yet installed on the device but is listed, it will be automatically taken into account on the first VPN connection after installation.

**Example of configuring this parameter:**

```
per-app-proxy-mode: [off/on/bypass] \\Specify one of the three parameters
per-app-proxy-list: [com.google.chrome,com.meta.instagram] \\list of appIDs separated by ','
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
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

{% code title="Via subscription body:" %}
```
#per-app-proxy-mode: on
#per-app-proxy-list: com.google.chrome,com.meta.instagram
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Proxy for selected apps Invert (Android)</summary>

In this parameter, you can specify a list of apps that should use the VPN or, conversely, bypass it.\
**Selects all apps except those specified in the list.**

**Example of configuring this parameter:**

```
per-app-proxy-mode: [off/on/bypass] \\Specify one of the three parameters
per-app-proxy-list-invert: [com.google.chrome,com.meta.instagram] \\list of appIDs separated by ','
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
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

{% code title="Via subscription body:" %}
```
#per-app-proxy-mode: on
#per-app-proxy-list-invert: com.google.chrome,com.meta.instagram
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Proxy for selected apps Set (Android)</summary>

In this parameter, you can specify a list of apps that should use the VPN or, conversely, bypass it.\
**Clears all currently selected apps, and only then selects the apps from the specified list.**

**Example of configuring this parameter:**

```
per-app-proxy-mode: [off/on/bypass] \\Specify one of the three parameters
per-app-proxy-list-set: [com.google.chrome,com.meta.instagram] \\list of appIDs separated by ','
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
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

{% code title="Via subscription body:" %}
```
#per-app-proxy-mode: on
#per-app-proxy-list-set: com.google.chrome,com.meta.instagram
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Packet analysis (Sniffing)</summary>

In **xray-core**, sniffing is needed to analyze the first packets of a connection and automatically detect the **protocol** (HTTP, TLS, BitTorrent, etc.) and the **domain** (SNI/Host).\
It may affect media loading in the WeChat app. Enabled by default.<br>

**Example of configuring this parameter:**

```
sniffing-enable: [String] 
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
sniffing-enable: 1
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#sniffing-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Disable subscription collapse</summary>

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

This feature disables the ability to collapse a subscription: the list of servers is always displayed in full, in the expanded view.<br>

**Example of configuring this parameter:**

```
subscriptions-collapse: [false / 0]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscriptions-collapse: 0
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#subscriptions-collapse: 0
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Force-expand subscription</summary>

When receiving this parameter via a subscription update, the app will forcibly expand the subscription if it is collapsed. The value `false` is ignored: the parameter is only used for expanding; you cannot collapse a subscription with it.

**Example of configuring this parameter:**

```
subscriptions-expand-now: [true / 1]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscriptions-expand-now: 1
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#subscriptions-expand-now: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Ping display mode</summary>

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

Allows displaying icons instead of time values.<br>

**Example of configuring this parameter:**

```
ping-result: [time,icon]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
ping-result: icon
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#ping-result: icon
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Mux</summary>

Mux in xray-core is a multiplexing feature that allows data from multiple virtual TCP connections to be transmitted over a single physical TCP connection. It is designed to reduce latency from the TCP handshake, but not to increase throughput (it can even slow down large downloads). Configured in the outbound configuration with parameters such as enabled and concurrency (min -1, max 1024).

**Example of configuring this parameter:**

```
mux-enable: [true / 1]
mux-tcp-connections: [String]
mux-xudp-connections: [String]
mux-quic: [String]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
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

{% code title="Via subscription body:" %}
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

<summary>Proxy \ TUN mode (Desktop only)</summary>

You must <mark style="color:$warning;">**use only one**</mark> of the two listed parameters! These parameters determine the connection type when adding/updating the subscription.

**Example of configuring this parameter:**

```
proxy-enable: [true / 1]
tun-enable: [true / 1]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
proxy-enable: 1
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#proxy-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>TUN mode (Desktop only)</summary>

Determines which mode will be used for the TUN connection.

* **`system`** — uses the OS's system network stack.\
  Fast and efficient, but depends on correct configuration of routes and firewall.
* **`gvisor`** — user-space gVisor stack.\
  Fewer dependencies on kernel rules and conflicts with iptables/nftables/Docker, better isolation; possibly a small performance downside.

**Example of configuring this parameter:**

```
tun-mode: [system,gvisor]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
tun-mode: gvisor
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#tun-mode: gvisor
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Tunnel core selection (Desktop only)</summary>

Determines which core will be used for the TUN connection. Available choices:\\

* [sing-box](https://github.com/SagerNet/sing-box)
* [tun2proxy](https://github.com/tun2proxy/tun2proxy)
* default (Happ TUN) — our own tunnel implementation

**Example of configuring this parameter:**

```
tun-type: [singbox, tun2proxy, default]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
tun-type: tun2proxy
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#tun-type: tun2proxy
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Exclude Routes</summary>

Defines a list of subnets and IP addresses whose traffic must not pass through the tunnel.\
Addresses are specified in a single line, separated by spaces and commas.

**Example of configuring this parameter:**

```
exclude-routes: [String]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
exclude-routes: 192.168.1.0/24, 10.0.0.0/8
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#exclude-routes: 192.169.1.0/24, 10.0.0.0/8
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Exclude Routes Set</summary>

Defines a list of subnets and IP addresses whose traffic must not pass through the tunnel.\
Addresses are specified in a single line, separated by spaces and commas.\
**Before installation, the current list is cleared.**

**Example of configuring this parameter:**

```
exclude-routes-set: [String]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
exclude-routes-set: 192.169.1.0/24, 10.0.0.0/8
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#exclude-routes-set: 192.169.1.0/24, 10.0.0.0/8
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Themes (iOS only)</summary>

Allows you to change the color theme to a personal one. You can create your own theme in the editor — press and hold the "Appearance theme" label to open the menu. A created theme can be exported to the clipboard, as well as imported from the clipboard, from a `.happ` file, or transferred via a subscription.

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

**Example of configuring this parameter:**

```
color-profile: [String] //base64 or plainString
color-profile: resetcolors // full reset
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
color-profile: {"backgroundGradientRotationAngle":37.1,"serverRowBackgroundColor":"#21003D67","subsHeaderColor":"#42296DFF","profileWebPageIconColor":"#A2B8FFFF","selectedServerRowColor":"#3E2F62B5","disclosureSubHeaderTextColor":"#C1C2E2FF","buttonTextColor":"#FFFFFFFF","buttonTimerColor":"#FFFFFFFF","subscriptionInfoBackgroundColor":"#21003CFF","backgroundColors":["#3D2A7DFF","#6557BAFF","#9377FF7F"],"disclosureHeaderTextColor":"#FFFFFFFF","backgroundGradientColorIntensity":1,"additionalOptionsButtonColor":"#FFFFFFFF","buttonImageType":"light","serverRowSubTitleTextColor":"#C1C2E2FF","supportIconColor":"#FFFFFFFF","topBarButtonsColor":"#FFFFFFFF","subscriptionTrafficBackgroundColor":"#533EA7FF","subHeaderButtonColor":"#FFFFFFFF","buttonColor":"#9377FFFF","powerIconColor":"#3D2A7DFF","subscriptionInfoTextColor":"#FFFFFFFF","serverRowTitleTextColor":"#FFFFFFFF","backgroundImageType":"system","elipseColors":["#00B460FF","#CF72FFE0","#FFDD00FF"],"serverRowChevronColor":"#FFFFFFFF"}
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#color-profile: {"backgroundGradientRotationAngle":37.1,"serverRowBackgroundColor":"#21003D67","subsHeaderColor":"#42296DFF","profileWebPageIconColor":"#A2B8FFFF","selectedServerRowColor":"#3E2F62B5","disclosureSubHeaderTextColor":"#C1C2E2FF","buttonTextColor":"#FFFFFFFF","buttonTimerColor":"#FFFFFFFF","subscriptionInfoBackgroundColor":"#21003CFF","backgroundColors":["#3D2A7DFF","#6557BAFF","#9377FF7F"],"disclosureHeaderTextColor":"#FFFFFFFF","backgroundGradientColorIntensity":1,"additionalOptionsButtonColor":"#FFFFFFFF","buttonImageType":"light","serverRowSubTitleTextColor":"#C1C2E2FF","supportIconColor":"#FFFFFFFF","topBarButtonsColor":"#FFFFFFFF","subscriptionTrafficBackgroundColor":"#533EA7FF","subHeaderButtonColor":"#FFFFFFFF","buttonColor":"#9377FFFF","powerIconColor":"#3D2A7DFF","subscriptionInfoTextColor":"#FFFFFFFF","serverRowTitleTextColor":"#FFFFFFFF","backgroundImageType":"system","elipseColors":["#00B460FF","#CF72FFE0","#FFDD00FF"],"serverRowChevronColor":"#FFFFFFFF"}
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Include all networks (iOS only)</summary>

Enables the use of all networks in the tunnel (NetworkExtension). The feature is available in iOS starting from 16.4.\
On devices with an older iOS version, the parameter will have no effect, and the corresponding switches in DevSettings will not appear.

**Example of configuring this parameter:**

```
include-all-networks-enable: [true / 1]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
include-all-networks-enable: true
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#include-all-networks-enable: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>Exclude local networks (iOS only)</summary>

If the "Include all networks" option is enabled, this parameter allows local networks to be excluded from the tunnel (NetworkExtension).\
Local network traffic will go directly. Available for iOS 16.4+.

**Example of configuring this parameter:**

```
exclude-local-networks-enable: [true / 1]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
exclude-local-networks-enable: true
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#exclude-local-networks-enable: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>Exclude APNS (iOS only)</summary>

If the "Include all networks" option is enabled, this parameter allows the Apple Push Notification Service (APNS) to be excluded from the tunnel.\
All Apple notification IP ranges will go directly. Available for iOS 16.4+.

**Example of configuring this parameter:**

```
exclude-apns-enable: [true / 1]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
exclude-apns-enable: true
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#exclude-apns-enable: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>Do not use server list filtering</summary>

By default, automatic filtering works in Premium subscriptions:\\

* If the server name contains "only WiFi" — it is visible only when connected via Wi-Fi.
* If the name contains "only Mobile" — it is visible only on mobile internet. This option disables this behavior.

**Example of configuring this parameter:**

```
dont-use-filter: [true / 1]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
dont-use-filter: true
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#dont-use-filter: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>Pin the current subscription</summary>

Allows a subscription to be pinned (Pin) or unpinned in the general list.\\

* true — pins the subscription to the top.
* false — unpins.

**Example of configuring this parameter:**

```
subscription-pin: [true / 1]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
subscription-pin: true
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#subscription-pin: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>Block User-Agent changes</summary>

Blocks the user from manually changing the **User-Agent** through the application interface.\
However, the provider can still change it remotely via the **change-user-agent** parameter.

**Example of configuring this parameter:**

```
manual-block-user-agent: [true / 1]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
manual-block-user-agent: true
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#manual-block-user-agent: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>Change server sorting within the subscription</summary>

Determines the display order of servers within the subscription:

* **without** — no sorting (as delivered from the backend).
* **ping** — by latency (servers with lower ping are displayed higher, unavailable ones — at the end).
* **alphabet** — alphabetical.

**Example of configuring this parameter:**

```
subscriptions-sort-type: [without, ping, alphabet]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
subscriptions-sort-type: ping
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#subscriptions-sort-type: ping
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>Take tunnel DNS from JSON</summary>

The logic applies only when all the following conditions are met: a JSON configuration is used,\
there is no routing profile, and the toggle is enabled in the settings.\
The system takes the first server from `dns.servers` in the JSON.

Selection algorithm:

* **Direct IP**: If IPv4/IPv6 is specified, it is set as the DOU DNS of the tunnel.
* **DoH**: If a URL (https://) is specified, the IP is looked up in `dns.hosts`.
  * iOS: A full-fledged DoH request is configured.
  * Android / Desktop: The IP from hosts (DOU) is used.
* **Object**: The value is extracted from the `address` field, similar to the description above.
* **Fallback DNS**:\
  If the main server is invalid, the default is used:
  * Android / Desktop: 1.1.1.1 (DOU).
  * iOS: Cloudflare DoH (https://cloudflare-dns.com/dns-query).

**Example of configuring this parameter:**

```
dns-from-json-enable: [true / 1]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
HTTP/2 200 
dns-from-json-enable: true
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#dns-from-json-enable: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>User-Agent for downloading geo files</summary>

Allows you to change the User-Agent header value when downloading Geo-IP and Geo-Site files.

**Available values:**

* **safari-mac**
* **chrome-win**
* **safari-ios**
* **firefox-win**
* **chrome-android**

**Example configuration:**

```
user-agent-geo-files: safari-mac
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
user-agent-geo-files: chrome-win
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#user-agent-geo-files: chrome-win
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>Proxy ping timeout (iOS only)</summary>

Sets the timeout (in seconds) when checking availability (ping) through a proxy server.\
Allowed range: **5 – 15** seconds.\
Values outside the range are ignored, and the default value of 7 is used.

**Example configuration:**

```
proxy-ping-timeout: 10
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
proxy-ping-timeout: 10
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#proxy-ping-timeout: 10
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>Hide VPN icon (Hide Proxy Icon)</summary>

Controls the display of the VPN icon in the system status bar.\
The toggle reacts to the presence of both routes (::/128 and 0.0.0.0/8) in the excluded routes list (excluded-routes).\
When the option is enabled, these routes are automatically added to the excluded list; when disabled, they are removed.

**Example configuration:**

```
hide-vpn-icon: [true / 1]
```

**Delivery methods:**

{% code title="Via HTTP Headers:" %}
```
hide-vpn-icon: true
```
{% endcode %}

{% code title="Via subscription body:" %}
```
#hide-vpn-icon: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>
