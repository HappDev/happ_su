---
description: Manage application settings via subscription
---

# Application Management

**The application management functionality** includes two areas:

* [Standard parameters](app-management.md#standartnye-parametry) that work for most panels.
* [Advanced parameters](app-management.md#id-rasshirennyifunkcional-opisanieparametrov) for which you need to specify the [Provider ID](provider-id.md[...)

To enable a parameter, pass the value `true` or `1`; to disable it, pass any other non-empty value.

## Standard Parameters

<details>

<summary>Subscription Auto-Update</summary>

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

The system creates a task to perform the operation at a specified interval. Depending on internal priorities, the operation may be delayed but will still occur asynchronously.
If for any reason the update wasn’t performed within the specified interval, it will be automatically triggered at the next available opportunity.
The interval is set in hours and must be a multiple of one hour.

**Example of configuring this parameter:**

```
profile-update-interval: [int]
```

**Ways to pass it:**

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

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

The name of the subscription profile. Can be passed as plain text or base64 (UTF-8). **Restriction:** Maximum length — 20 characters.

In the subscription body, specify the parameter with a # (e.g., #profile-title)

**Example of configuring this parameter:**

```
profile-title: [string]
```

**Ways to pass it:**

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

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Displays information about balance, traffic usage, and subscription validity period.\
The app shows the used traffic (upload + download) on the left side of the scale, and the total on the right.\
The subscription end date is specified in the **expire** parameter.\
**Note:** All data is sent in a single header separated by **;**.

**Example of configuring this parameter:**

```
subscription-userinfo: [string]
```

**Ways to pass it:**

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

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

A button to go to the support page.\
Displayed as a blue icon on the right.\
If the link leads to Telegram, a Telegram icon is shown; otherwise, a standard link icon is used.

**Example of configuring this parameter:**

```
support-url: [string]
```

**Ways to pass it:**

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

<summary>Website Link</summary>

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

A button to go to the subscription website.\
Displayed as a blue icon on the left.\
If the parameter is not set, the icon will be gray.

**Example of configuring this parameter:**

```
profile-web-page-url: [string]
```

**Ways to pass it:**

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

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

The subscription can contain an announcement message, passed as **plain text** or **Base64**.\
**Restriction:** maximum length of displayed text — **200 characters**.

**Example of configuring this parameter:**

```
announce: [string]
```

**Ways to pass it:**

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

<summary>Disable Routing</summary>

A global parameter to disable routing in the app.

**Example of configuring this parameter:**

```
routing-enable: [string]
```

**Ways to pass it:**

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

<summary>Tunnel Configuration (Desktop only)</summary>

Pass your own tunnel configuration for the sing-box core.

**Example of configuring this parameter:**

```
custom-tunnel-config: [json]
```

**Ways to pass it:**

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

## Advanced Parameters <a href="#id-rasshirennyifunkcional-opisanieparametrov" id="id-rasshirennyifunkcional-opisanieparametrov"></a>

{% hint style="warning" %}
[Provider ID](provider-id.md) parameter is required!
{% endhint %}

<details>

<summary>Change Subscription URL</summary>

If your domain is blocked by your provider but users can still connect to servers and update subscriptions, you can specify a new subscription link.

**Example of configuring this parameter:**

```
new-url: [url]
```

**Ways to pass it:**

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

Change the site domain without changing the full URL and preserving the rest of the address.

**Example of configuring this parameter:**

```
new-domain: [domain]
```

**Ways to pass it:**

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

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

Allows you to set an additional label displayed below the server name instead of the default text.

* Maximum length — 30 characters.
* If it doesn't fit on the screen, it will be truncated with an ellipsis.
* Set after `title` separated by `?`.

**Examples:**

{% code title="VLESS" %}
```
vless://1fb46fdc-e3e4-35d1-bd46-605d773b5762@5.5.8.9:443?encryption=none&node_id=482&headerType=none&type=tcp&security=reality&sni=booking.com&fp=chrome&pbk=YqHW8a4iAc1SZYpTrFVoOQg1F3yAdX1tWXuROZUCsEU[...]
```
{% endcode %}

{% code title="VMESS" %}
```
vmess://eyJob3N0IjoiZWxhaG9tZWtpdGNoZW4uY29tIiwicGF0aCI6IiIsInRscyI6IiIsImFkZCI6ImVsYWhvbWVraXRjaGVuLmNvbSIsInBvcnQiOjUwMDAsImFpZCI6MCwibmV0IjoidGNwIiwidHlwZSI6Im5vbmUiLCJ2IjoiMiIsInBzIjoi4piB77iPIDog[...]
```
{% endcode %}

{% code title="Trojan" %}
```
trojan://8GXLP3dEzm7T8wP5Jx0Ufg@199.107.164.105:443?security=tls&insecure=1&fragment=3,1,tlshello&type=ws&headerType=&path=%2F&host=quictest.burncommunity.ru&sni=quictest.burncommunity.ru&fp=chrome&al[...]
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

Some CDNs support domain fronting. This allows you to connect to your site using a third-party domain.

For example, specifying the connection address `visa.com` and the Host header as `my-domain.com`, the provider will only see the request to `visa.com`.

You can also fetch server lists from your domain using SNI TLSHello packet fragmentation.

By default, fragmentation is enabled for all subscriptions. The user can only add a subscription once; [...]

#### &#x20;URL Scheme with Parameters

```
[link]#title?[fragment]&[resolve-address]&[host]&[insecure]

Fronting:
visa.com/123#MyVPN?resolve-address=visa.com&host=mydomain.com

Fragmentation:
mydomain.com/123#MyVPN?fragment=80-250,10-100,tlshello
```

Fragmentation has three parameters: `[length]`, `[interval]` and `[packets]`.

For fronting, specify the URL with the domain used for connection first, [...]

</details>

<details>

<summary>Advanced fragmentation</summary>

This feature is currently in closed testing and will be available soon...

</details>

<details>

<summary>Non-disableable HWID</summary>

By default, HWID is enabled on all Happ applications. If you want users to be unable to disable HWID forwarding, enable this parameter.

**Example of configuring this parameter:**

```
subscription-always-hwid-enable: [true / 1]
```

**Ways to pass it:**

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

You can enable automatic notifications about subscription expiration.\
The user will receive reminders 3 days before the subscription ends: the app will send one notification per day.

Notification text:

```
 Your subscription [name] will expire soon, don’t forget to renew it.
```

**Example of configuring this parameter:**

```
notification-subs-expire: [true / 1]
```

**Ways to pass it:**

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

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

Disable the ability to view and edit server configurations for users of your subscription. Not available for all apps.

**Example of configuring this parameter:**

```
hide-settings: [true / 1]
```

**Ways to pass it:**

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

The app can pre-resolve server domains before establishing a connection.\
You can specify any DoH server, and when connecting to the Xray server, the domain will be replaced with the returned IP.

If multiple IPs are returned, the app will automatically select the one with the lowest latency.\
However, note: with a large number of IPs, connection time may increase since all IPs will be checked.

**Example of configuring this parameter:**

```
server-address-resolve-enable: [true / 1]
server-address-resolve-dns-domain: [url]
server-address-resolve-dns-ip: [ip]
```

**Ways to pass it:**

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

#### Application Settings Management <a href="#upravlenie-nastroikami-prilozheniya" id="upravlenie-nastroikami-prilozheniya"></a>

{% hint style="warning" %}
[Provider ID](provider-id.md) parameter is required!
{% endhint %}

<details>

<summary>Auto Connect</summary>

Allows you to automatically connect the user to servers when the application starts. Additionally, you can specify the behavior.

**Example of configuring this parameter:**

```
subscription-autoconnect: [true / 1]
subscription-autoconnect-type: [“lastused“/”lowestdelay”]
```

**Ways to pass it:**

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

<summary>Auto Ping</summary>

Run automatic server list testing when the app is opened if needed.

**Example of configuring this parameter:**

```
subscription-ping-onopen-enabled: [true / 1]
```

**Ways to pass it:**

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

You can enable or disable auto-updating for all subscriptions in the app — this setting applies globally.

**Example of configuring this parameter:**

```
subscription-auto-update-enable: [true / 1] 
```

**Ways to pass it:**

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

This is a global control parameter for fragmentation for all subscriptions. For specific subscriptions, set fragmentation individually.

**Example of configuring this parameter:**

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

**Ways to pass it:**

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

This function allows you to select how ping is performed in the app. There are three options available: "via Proxy", "TCP" and "ICMP".

**Example of configuring this parameter:**

```
ping-type: ["proxy", "proxy-head', "tcp","icmp"]
check-url-via-proxy: [url]
```

**Ways to pass it:**

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

This function allows you to change the User-Agent used in headers when obtaining a subscription. Useful if default User-Agent is blocked.

**Example of configuring this parameter:**

```
change-user-agent: [String] 
```

**Ways to pass it:**

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

This enables automatic app startup when the device is powered on. Currently available ...

**Example of configuring this parameter:**

```
app-auto-start: [String] 
```

**Ways to pass it:**

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

<summary>Update Subscriptions When App Launches</summary>

This function automatically updates all subscriptions in the app whenever the app is opened.

**Example of configuring this parameter:**

```
subscription-auto-update-open-enable: [String] 
```

**Ways to pass it:**

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

<summary>App-specific Proxy (Android)</summary>

In this parameter, you can specify a list of apps that should use the VPN or, vice versa, bypass it. [...]

**Example of configuring this parameter:**

```
per-app-proxy-mode: [off/on/bypass] \\Specify one of three parameters
per-app-proxy-list: [com.google.chrome,com.meta.instagram] \\list appIDs separated by ','
```

**Ways to pass it:**

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

In **xray-core**, sniffing is used to analyze the first packets of the connection and automatically determine the **protocol** (HTTP, etc.).
It may affect media loading in the WeChat app. Enabled by default.

**Example of configuring this parameter:**

```
sniffing-enable: [String] 
```

**Ways to pass it:**

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

<summary>Disable Subscription Collapse</summary>

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

This function disables the ability to collapse a subscription: the server list is always fully displayed.

**Example of configuring this parameter:**

```
subscriptions-collapse: [String] 
```

**Ways to pass it:**

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

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

Allows displaying icons instead of time values.

**Example of configuring this parameter:**

```
ping-result: [time,icon]
```

**Ways to pass it:**

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

Mux in xray-core is a multiplexing feature that allows the transfer of data of multiple virtual sessions over a single connection.

**Example of configuring this parameter:**

```
mux-enable: [true / 1]
mux-tcp-connections: [String]
mux-xudp-connections: [String]
mux-quic: [String]
```

**Ways to pass it:**

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

<summary>Proxy \ TUN Mode (Desktop only)</summary>

You must <mark style="color:$warning;">**use only one**</mark> of the two parameters listed! These settings ...

**Example of configuring this parameter:**

```
proxy-enable: [true / 1]
tun-enable: [true / 1]
```

**Ways to pass it:**

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

<summary>TUN Mode (Desktop only)</summary>

Determines which mode will be used for TUN connection.

* **`system`** — Uses OS system network stack. Fast and efficient, but depends on properly set routes and firewall.
* **`gvisor`** — Userspace gVisor stack. Less dependent on kernel rules and iptables/nftables/Docker conflicts, better isolation; might have slightly lower performance.

**Example of configuring this parameter:**

```
tun-mode: [system,gvisor]
```

**Ways to pass it:**

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

<summary>Tunnel Core Selection (Desktop only)</summary>

Determines which core will be used for TUN connection. Available: [sing-box](https://github.com/SagerNet/sing-box[...])

**Example of configuring this parameter:**

```
tun-type: [singbox, tun2proxy]
```

**Ways to pass it:**

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

<summary>Exclude routes</summary>

Defines subnets and IP addresses whose traffic should not go through the tunnel.\
Addresses are specified in a single line, separated by spaces and commas.

**Example of configuring this parameter:**

```
exclude-routes: [String]
```

**Ways to pass it:**

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
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>
