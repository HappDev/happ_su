---
description: Manage app settings through the subscription
---

# App Management

**App management functionality** includes two directions:

* [Standard parameters](app-management.md#standartnye-parametry) that work for most panels.
* [Advanced parameters](app-management.md#id-rasshirennyifunkcional-opisanieparametrov) that require specifying a [Provider ID](provider-id.md) in the subscription.

To enable a parameter, pass `true` or `1`; to disable it, pass any other non-empty value (for example, `0` or `false`).

## Standard parameters

<details>

<summary>Subscription auto-refresh</summary>

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

A task is created in the system to run the operation at a given interval. Depending on internal priorities, the system attempts to refresh the subscription at the scheduled time.
If for any reason the refresh is not executed within the specified interval, it will happen automatically the next time the app is launched.
The interval is set in hours and must be a multiple of one hour.

**Example:**

```
profile-update-interval: [int]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Subscription name</summary>

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

The subscription profile name. Can be passed as plain text or Base64 (UTF-8). **Limit:** Maximum length — 25 characters.

Pass it in the subscription body by prefixing the parameter with # (for example, #profile-title)

**Example:**

```
profile-title: [string]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Subscription status string (traffic, expiration date)</summary>

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Shows balance, used traffic volume, and subscription validity period.
In the app, the left side of the bar shows the amount of traffic used (upload + download), and the right side — the total volume after the “/” symbol.
The subscription end date is provided in the **expire** parameter.
**Note:** all data is passed in a single header and separated by **;**.

**Example:**

```
subscription-userinfo: [string]
```

**Ways to pass:**

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
№subscription-userinfo: upload=0; download=2153701362; total=0; expire=1790951622
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Support page link</summary>

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

A button to go to the support page.
Displayed as a blue icon on the right side of the row.
If the link is to Telegram, a Telegram icon is shown; otherwise a standard link icon is used.

**Example:**

```
support-url: [string]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Website link</summary>

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

A button to go to the subscription website.
Displayed as a blue icon on the left side of the row.
If the parameter is not set, the icon will be gray.

**Example:**

```
profile-web-page-url: [string]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Announcement</summary>

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

A subscription can include an announcement text, passed as **plain text** or **Base64**.
**Limit:** maximum displayed length — **200 characters**.

**Example:**

```
announce: [string]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Disable routing</summary>

A global parameter to disable routing in the app.

**Example:**

```
routing-enable: [string]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Tunnel configuration (Desktop only)</summary>

Pass your own tunnel configuration for the sing-box engine.

**Example:**

```
custom-tunnel-config: [json]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

## Advanced parameters <a href="#id-rasshirennyifunkcional-opisanieparametrov" id="id-rasshirennyifunkcional-opisanieparametrov"></a>

{% hint style="warning" %}
The [Provider ID](provider-id.md) parameter is required!
{% endhint %}

<details>

<summary>Change subscription URL</summary>

If your domain is blocked by your ISP and users can connect to servers and refresh the subscription only via VPN, this parameter is for you. By specifying a new domain name as the parameter value, it will be automatically replaced for all users of the subscription.

**Example:**

```
new-url: [url]
```

**Ways to pass:**

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
#new-url https://mynew-domain.com/3J3jrb4jfc
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Change subscription domain</summary>

Change the site domain without changing the full URL, keeping the rest of the address intact.

**Example:**

```
new-domain: [domain]
```

**Ways to pass:**

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
#new-domain mynew-domain.com
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Server description in subscription</summary>

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

Allows you to set an additional caption displayed under the server name instead of the standard text (e.g., "VMess", "VLESS", "Trojan").

* Maximum length — 30 characters.
* If it does not fit on the screen, it will be truncated with an ellipsis.
* Set after `title` using the `?` separator.

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

<summary>Subscription fragmentation & fronting</summary>

Some CDNs support domain fronting. This allows you to connect to your site through a third-party domain.

For example, by specifying the connection address `visa.com` and setting the Host header to `my-domain.com`, the ISP will only see a request to `visa.com`.

You can also request your domain for the server list while using packet fragmentation in SNI TLSHello.

By default, fragmentation is enabled for all subscriptions. A user can add a subscription only once; on repeat attempts, if the account is not premium, an update will not be allowed.

#### URL scheme with parameters

```
[link]#title?[fragment]&[resolve-address]&[host]&[insecure]

Fronting:
visa.com/123#MyVPN?resolve-address=visa.com&host=mydomain.com

Fragmentation:
mydomain.com/123#MyVPN?fragment=80-250,10-100,tlshello
```

Fragmentation contains three parameters: `[length]`, `[interval]`, and `[packets]`.

When using fronting, you must first specify the URL with the domain through which the connection will be made. You also need to set `resolve-address` — this can be a domain or an IP address — and `host` corresponding to your host within the chosen provider’s network.

</details>

<details>

<summary>Advanced fragmentation</summary>

This feature is currently in closed testing and will be available soon...

</details>

<details>

<summary>Non-disablable HWID</summary>

By default, HWID is enabled in all Happ apps. If you want to prevent the user from turning off sending this parameter in the app settings, you can send a special parameter together with the subscription.

**Example:**

```
subscription-always-hwid-enable: [true / 1]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Subscription expiration notification</summary>

You can enable automatic notifications about subscription expiration.
The user will receive reminders 3 days before expiration: the app will send one notification per day for three days. This helps the user remember to renew on time.

Notification text:

```
 Your subscription [name] is about to expire — don’t forget to renew it.
```

**Example:**

```
notification-subs-expire: [true / 1]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Hide server settings in subscription</summary>

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

Disable the ability for users of your subscription to view and edit server configurations. The setting applies both to subscriptions already added and those added in the future.

**Example:**

```
hide-settings: [true / 1]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Domain resolving</summary>

The app can pre-resolve server domains even before a connection is established.
You can specify any DoH server, and when connecting to an Xray server the domain name will be replaced with the obtained IP address.

If multiple IP addresses are returned for a domain, the app will automatically choose the one with the lowest latency (ping).
However, keep in mind: with a large number of IPs, connecting may take longer because all options will be tested in advance.

**Example:**

```
server-address-resolve-enable: [true / 1]
server-address-resolve-dns-domain: [url]
server-address-resolve-dns-ip: [ip]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

#### App settings management <a href="#upravlenie-nastroikami-prilozheniya" id="upravlenie-nastroikami-prilozheniya"></a>

{% hint style="warning" %}
The [Provider ID](provider-id.md) parameter is required!
{% endhint %}

<details>

<summary>Auto-connect</summary>

Automatically connects the user to servers when the app starts. Additionally, with **subscription-autoconnect** you can specify a criterion for choosing which server to connect to.

**Example:**

```
subscription-autoconnect: [true / 1]
subscription-autoconnect-type: [“lastused“/”lowestdelay”]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Auto-ping</summary>

Run automatic server list tests when opening the app if needed.

**Example:**

```
subscription-ping-onopen-enabled: [true / 1]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Auto-update subscriptions</summary>

You can enable or disable auto-update for all subscriptions at once — this setting applies to all subscriptions simultaneously. If you need to set auto-update only for a specific subscription, use the Subscription auto-refresh feature. When the global setting is disabled, each subscription determines its own refresh time.

**Example:**

```
subscription-auto-update-enable: [true / 1] 
```

**Ways to pass:**

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
#new-url: https:/mynew-domain.com/3J3jrb4jfc
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Fragmentation</summary>

This is a global fragmentation control parameter for all subscriptions. If you need to set fragmentation only for a specific subscription or server, use the free functionality and instructions in the general app documentation. When the global setting is disabled, each subscription determines its own fragmentation settings.

**Example:**

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

**Ways to pass:**

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
noises-enable: 1
noises-type: rand
noises-packet: 10-20
noises-delay: 10-16
noises-applyto: ipv4
```

{% endcode %}

{% code title="Via subscription body:" %}

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

This feature lets you choose how ping is performed in the app. Three options are available: “via Proxy”, “TCP”, and “ICMP”. For “via Proxy”, you can additionally specify a URL to check ping.

**Example:**

```
ping-type: ["proxy", "proxy-head', "tcp","icmp"]
check-url-via-proxy: [url]
```

**Ways to pass:**

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
#ping-type proxy
#check-url-via-proxy: https://cp.cloudflare.com/generate_204
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>User-Agent</summary>

This feature allows changing the User-Agent used in headers when fetching the subscription. Useful when a provider blocks requests with non-standard or unsuitable headers.

**Example:**

```
change-user-agent: [String] 
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>App auto-start</summary>

Automatically launch the app when the device powers on. Currently available on Android only. 

**Example:**

```
app-auto-start: [String] 
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Update subscriptions on app launch</summary>

Automatically refresh all subscriptions each time the app is opened.

**Example:**

```
subscription-auto-update-open-enable: [String] 
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Per-app proxy (Android)</summary>

Specify a list of apps that should use the VPN, or bypass it. If an app is not yet installed on the device but is listed here, it will be automatically accounted for on the first VPN connection after installation.

**Example:**

```
per-app-proxy-mode: [off/on/bypass] \\Specify one of the three options
per-app-proxy-list: [com.google.chrome,com.meta.instagram] \\app IDs separated by ','
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Packet inspection (Sniffing)</summary>

In **xray-core**, sniffing analyzes the first packets of a connection to automatically detect the **protocol** (HTTP, TLS, BitTorrent, etc.) and **domain** (SNI/Host).
May affect media loading in WeChat. Enabled by default.\

**Example:**

```
sniffing-enable: [String] 
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Disable subscription collapsing</summary>

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

This feature disables the ability to collapse a subscription: the server list is always shown fully expanded.\

**Example:**

```
subscriptions-collapse: [String] 
```

**Ways to pass:**

{% code title="Via HTTP Headers:" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscriptions-collapse: 1
```

{% endcode %}

{% code title="Via subscription body:" %}

```
#subscriptions-collapse: 1
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Ping display mode</summary>

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

Allows showing icons instead of time values\

**Example:**

```
ping-result: [time,icon]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Mux</summary>

Mux in xray-core is a multiplexing feature that allows data from multiple virtual TCP connections to be sent over a single physical TCP connection. It’s designed to reduce delays from TCP handshakes, not to increase throughput (it may even slow large downloads). Configured in the outbound with parameters like enabled and concurrency (min -1, max 1024).

**Example:**

```
mux-enable: [true / 1]
mux-tcp-connections: [String]
mux-xudp-connections: [String]
mux-quic: [String]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Proxy \ TUN mode (Desktop only)</summary>

You must <mark style="color:$warning;">**use only one**</mark> of the two parameters below! These parameters determine the connection type when adding/updating a subscription.

**Example:**

```
proxy-enable: [true / 1]
tun-enable: [true / 1]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>TUN mode (Desktop only)</summary>

Determines which mode will be used for the TUN connection.

* **`system`** — uses the OS’s system network stack.
  Fast and efficient, but depends on correct routing and firewall configuration.
* **`gvisor`** — gVisor userspace stack.
  Fewer dependencies on kernel rules and conflicts with iptables/nftables/Docker, better isolation; may have a slight performance penalty.

**Example:**

```
tun-mode: [system,gvisor]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Select tunnel engine (Desktop only)</summary>

Determines which engine will be used for the TUN connection. Available options: [sing-box](https://github.com/SagerNet/sing-box), [tun2proxy](https://github.com/tun2proxy/tun2proxy)

**Example:**

```
tun-type: [singbox, tun2proxy]
```

**Ways to pass:**

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
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>

<details>

<summary>Exclude routes</summary>

Defines subnets and IP addresses whose traffic should not pass through the tunnel.
Addresses are specified on a single line, separated by spaces and commas.

**Example:**

```
exclude-routes: [String]
```

**Ways to pass:**

{% code title="Via HTTP Headers:" %}

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
exclude-routes: 192.169.1.0/24, 10.0.0.0/8
```

{% endcode %}

{% code title="Via subscription body:" %}

```
#exclude-routes: 192.169.1.0/24, 10.0.0.0/8
vless://70cc48c5-b2f4…
vmess://zkIAU1JitkI…
```

{% endcode %}

</details>
