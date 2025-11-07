# App management

## App Management

**App management functionality** includes two directions:

* [Standard parameters](app-management.md#standard-parameters) that work for most panels.
* [Advanced parameters](app-management.md#id-rasshirennyifunkcional-opisanieparametrov) for which it is necessary to pass [Provider ID](provider-id.md) with the subscription.

To activate a parameter, pass the value `true` or `1`; to disable it — any other non-empty value (for example, `0` or `false`).

### Standard Parameters

<details>

<summary>Subscription Auto-Update</summary>

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

The system creates a task to perform the operation at a specified interval. Depending on internal priorities, the system tries to start the subscription update at the set time.\
If for any reason the update was not performed within the specified interval, it will occur automatically on the next app launch.\
The interval is set in hours and must be a multiple of one hour.

**Example of setting this parameter:**

```
profile-update-interval: [int]
```

**Transmission methods:**

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

<summary>Subscription Name</summary>

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

The name of the subscription profile. Can be passed as plain text or in base64 (UTF-8). **Limit**: Maximum length — 25 characters.

Via the subscription body, by adding a # sign before the parameter (for example, #profile-title)

**Example of setting this parameter:**

```
profile-title: [string]
```

**Transmission methods:**

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

<summary>Subscription Status String (traffic, expiration date)</summary>

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Displays information about the balance, amount of used traffic, and subscription expiration date.\
In the app, the left part of the scale shows the amount of spent traffic (upload + download), and the right part — the total volume (total) after the "/" symbol.\
The subscription expiration date is specified in the **expire** parameter.\
**Note:** all data is passed in one header and separated by the **;** symbol.

**Example of setting this parameter:**

```
subscription-userinfo: [string]
```

**Transmission methods:**

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

<summary>Support Page Link</summary>

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

Button to go to the support page.\
Displayed as a blue icon located on the right side of the line.\
If the link leads to Telegram, a Telegram icon is displayed; in other cases, a standard link icon is used.

**Example of setting this parameter:**

```
support-url: [string]
```

**Transmission methods:**

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

<summary>Website Page Link</summary>

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Button to go to the subscription website page.\
Displayed as a blue icon located on the left side of the line.\
If the parameter is not set, the icon will be gray.

**Example of setting this parameter:**

```
profile-web-page-url: [string]
```

**Transmission methods:**

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

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

The subscription can contain announcement text, passed in **plain text** or **Base64** format.\
**Limit:** maximum displayed text length — **200 characters**.

**Example of setting this parameter:**

```
announce: [string]
```

**Transmission methods:**

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

<summary>Tunnel Configuration (Desktop only)</summary>

Pass your own tunnel configuration for the sing-box core.

**Example of setting this parameter:**

```
custom-tunnel-config: [json]
```

**Transmission methods:**

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

### Advanced Parameters <a href="#id-rasshirennyifunkcional-opisanieparametrov" id="id-rasshirennyifunkcional-opisanieparametrov"></a>

{% hint style="warning" %}
[Provider ID](provider-id.md) parameter is required!
{% endhint %}

<details>

<summary>Change Subscription URL</summary>

If the domain is blocked by your provider, and users can connect to servers and update the subscription only via VPN, this parameter is for you. By setting a new domain name in the value of this parameter, you will ensure its automatic replacement for all subscription users.

**Example of setting this parameter:**

```
new-url: [url]
```

**Transmission methods:**

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
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Change Subscription Domain</summary>

Changing the website domain without changing the full URL, keeping the rest of the address.

**Example of setting this parameter:**

```
new-domain: [domain]
```

**Transmission methods:**

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
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Server Description in Subscription</summary>

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

Allows setting an additional caption that is displayed under the server name instead of the standard text (for example, "VMess", "VLESS", "Trojan").

* Maximum length — 30 characters.
* If it doesn't fit on the screen, it will be shortened with an ellipsis.
* Set after `title` through the `?` separator.

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

<summary>Subscription Fragmentation and Fronting</summary>

Some CDNs support domain fronting. This allows connecting to your site through a third-party domain.

For example, by specifying the connection address `visa.com`, and in the Host header — `my-domain.com`, the provider will only see the request to `visa.com`.

You can also access your domain for the server list using packet fragmentation in SNI TLSHello.

By default, fragmentation is enabled for all subscriptions. The user can add a subscription only once; on repeated attempts, if the account is not premium, the update will not be allowed.

**URL Scheme with Parameters**

```
[link]#title?[fragment]&[resolve-address]&[host]&[insecure]

Fronting:
visa.com/123#MyVPN?resolve-address=visa.com&host=mydomain.com

Fragmentation:
mydomain.com/123#MyVPN?fragment=80-250,10-100,tlshello
```

Fragmentation contains three parameters: `[length]`, `[interval]` and `[packets]`.

When using fronting, you must first specify the URL with the domain through which the connection will be made. You also need to set `resolve-address` — this can be a domain or IP address — and `host`, corresponding to your host in the selected provider's network.

</details>

<details>

<summary>Advanced Fragmentation</summary>

This feature is currently undergoing closed testing and will be available soon...

</details>

<details>

<summary>Non-Disablable HWID</summary>

By default, HWID is enabled on all Happ apps. But if you want the user to be unable to disable the forwarding of this parameter by turning it off in the app settings, you can send a special parameter along with the subscription.

**Example of setting this parameter:**

```
subscription-always-hwid-enable: [true / 1]
```

**Transmission methods:**

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

<summary>Subscription Expiration Notification</summary>

You can enable the automatic subscription expiration notifications feature.\
The user will receive reminders 3 days before the subscription ends: the app will send one notification per day for three days. This will help the user not forget to renew the subscription on time.

Notification text:

```
Your subscription [name] is about to expire, don't forget to renew it.
```

**Example of setting this parameter:**

```
notification-subs-expire: [true / 1]
```

**Transmission methods:**

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

<summary>Hide Server Settings in Subscription</summary>

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

Disable the ability to view and edit server configurations for your subscription users. The setting applies to both already added subscriptions and those that will be added in the future.

**Example of setting this parameter:**

```
hide-settings: [true / 1]
```

**Transmission methods:**

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

<summary>Domain Resolving</summary>

The app can perform preliminary domain resolving of servers before establishing a connection.\
You can specify any DoH server, and when connecting to the Xray server, the domain name will be replaced with the received IP address.

If multiple IP addresses are returned for the domain, the app will automatically select the one with the minimum response time (ping).\
However, keep in mind: with a large number of IP addresses, the connection may take longer, as all options will be tested in advance.

**Example of setting this parameter:**

```
server-address-resolve-enable: [true / 1]
server-address-resolve-dns-domain: [url]
server-address-resolve-dns-ip: [ip]
```

**Transmission methods:**

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

**Managing App Settings**

{% hint style="warning" %}
[Provider ID](provider-id.md) parameter is required!
{% endhint %}

<details>

<summary>Auto-Connect</summary>

Allows automatically connecting the user to servers when launching the app. Additionally, using the **subscription-autoconnect** parameter, you can specify the criterion for connecting to a specific server.

**Example of setting this parameter:**

```
subscription-autoconnect: [true / 1]
subscription-autoconnect-type: [“lastused“/”lowestdelay”]
```

**Transmission methods:**

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

<summary>Auto-Ping</summary>

Launch automatic testing of the server list when opening the app if necessary.

**Example of setting this parameter:**

```
subscription-ping-onopen-enabled: [true / 1]
```

**Transmission methods:**

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

<summary>Auto-Update Subscriptions</summary>

In the app, you can enable or disable auto-update for all subscriptions at once — this setting applies to all subscriptions simultaneously. If you need to set auto-update only for a specific subscription, use the Subscription Auto-Update functionality. When the global setting is disabled, each subscription independently determines its update time.

**Example of setting this parameter:**

```
subscription-auto-update-enable: [true / 1] 
```

**Transmission methods:**

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
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Fragmentation</summary>

This is a global parameter for managing fragmentation for all subscriptions. If you need to assign fragmentation only to a specific subscription or server, use the free functionality and instructions from the general app documentation. When the global setting is disabled, each subscription independently determines the fragmentation settings.

**Example of setting this parameter:**

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

**Transmission methods:**

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
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Ping</summary>

This function allows you to choose the ping method in the app. Three options are available: "via Proxy", "TCP", and "ICMP". For the "via Proxy" mode, you can additionally specify a URL for ping checking.

**Example of setting this parameter:**

```
ping-type: ["proxy", "proxy-head', "tcp","icmp"]
check-url-via-proxy: [url]
```

**Transmission methods:**

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
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>User-Agent</summary>

This function allows changing the User-Agent used in headers when receiving the subscription. Useful in cases where the provider blocks requests with non-standard or unsuitable headers.

**Example of setting this parameter:**

```
change-user-agent: [String] 
```

**Transmission methods:**

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

<summary>App Auto-Start</summary>

This function allows automatically launching the app when the device is turned on. Currently available only on Android.

**Example of setting this parameter:**

```
app-auto-start: [String] 
```

**Transmission methods:**

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

<summary>Subscription Update on App Launch</summary>

This function automatically updates all subscriptions in the app every time the app is opened.

**Example of setting this parameter:**

```
subscription-auto-update-open-enable: [String] 
```

**Transmission methods:**

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

<summary>Proxy for Selected Apps (Android)</summary>

In this parameter, you can specify a list of apps that should use VPN or, conversely, bypass it. If the app is not yet installed on the device but is listed, it will be automatically accounted for on the first VPN connection after installation.

**Example of setting this parameter:**

```
per-app-proxy-mode: [off/on/bypass] \\Specify one of the three parameters
per-app-proxy-list: [com.google.chrome,com.meta.instagram] \\list of appIDs separated by ','
```

**Transmission methods:**

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

<summary>Packet Analysis (Sniffing)</summary>

In **xray-core**, sniffing is needed to analyze the first connection packets and automatically determine the **protocol** (HTTP, TLS, BitTorrent, etc.) and **domain** (SNI/Host).\
May affect media loading in the WeChat app. Enabled by default.

**Example of setting this parameter:**

```
sniffing-enable: [String] 
```

**Transmission methods:**

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

<summary>Prohibit Collapsing Subscriptions</summary>

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

This function disables the ability to collapse the subscription: the server list is always displayed in full, expanded view.

**Example of setting this parameter:**

```
subscriptions-collapse: [String] 
```

**Transmission methods:**

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
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Ping Display Mode</summary>

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

Allows displaying icons instead of time values.

**Example of setting this parameter:**

```
ping-result: [time,icon]
```

**Transmission methods:**

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

Mux in xray-core is a multiplexing function that allows transmitting data from multiple virtual TCP connections through one physical TCP connection. It is designed to reduce delays from TCP-handshake, but not to increase bandwidth (it may even slow down large downloads). Configured in the outbound configuration with parameters like enabled and concurrency (min -1 max 1024).

**Example of setting this parameter:**

```
mux-enable: [true / 1]
mux-tcp-connections: [String]
mux-xudp-connections: [String]
mux-quic: [String]
```

**Transmission methods:**

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
