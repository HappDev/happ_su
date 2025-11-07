---
description: Manage application settings via subscription
---
# Application Management
**Application management functionality** includes two directions:
* [Standard parameters](app-management.md#standard-parameters) that work for most panels.
* [Advanced parameters](app-management.md#advanced-parameters) for which you need to specify [Provider ID](provider-id.md) in the subscription.
To activate a parameter, pass the value `true` or `1`; to disable — any other non-empty value (for example, `0` or `false`).

## Standard parameters
<details>
<summary>Subscription auto-update</summary>
<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
A task is created in the system to perform the operation at the specified interval. Depending on internal priorities, the system tries to run the subscription update at the set time.\
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
<summary>Subscription name</summary>
<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
Subscription profile name. Can be passed as plain text or in base64 (UTF-8). **Limit**: Maximum length — 25 characters.
Via subscription body, prefix the parameter with # (e.g., #profile-title).
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
<summary>Subscription status line (traffic, expiration date)</summary>
<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
Displays information about balance, used traffic volume, and subscription expiration date.\
On the left side of the scale in the app, the amount of used traffic (upload + download) is shown, and on the right — the total volume (total) after the "/" symbol.\
The subscription expiration date is specified in the **expire** parameter.\
**Note:** all data is transmitted in one header and separated by the **;** symbol.
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
<summary>Support page link</summary>
<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>
Button to go to the support page.\
Displayed as a blue icon located on the right side of the line.\
If the link leads to Telegram, the Telegram icon is displayed; otherwise, the standard link icon is used.
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
<summary>Website page link</summary>
<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>
Button to go to the subscription website.\
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
<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>
The subscription can contain announcement text transmitted in **plain text** or **Base64** format.\
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
<summary>Disable routing</summary>
Global parameter to disable routing in the app.
**Example of setting this parameter:**
```
routing-enable: [string]
```
**Transmission methods:**
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
## Advanced parameters <a href="#advanced-parameters" id="advanced-parameters"></a>
{% hint style="warning" %}
Requires [Provider ID](provider-id.md) parameter!
{% endhint %}
<details>
<summary>Change subscription URL</summary>
If your domain is blocked by the provider, and users can only connect to servers and update the subscription via VPN, this parameter is for you. By setting a new domain name in this parameter value, you ensure its automatic replacement for all subscription users.
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
#new-url: https://mynew-domain.com/3J3jrb4jfc
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}
</details>
<details>
<summary>Change subscription domain</summary>
Change the site domain without changing the full URL, keeping the rest of the address.
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
#new-domain: mynew-domain.com
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}
</details>
<details>
<summary>Server description in subscription</summary>
<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>
Allows setting an additional caption displayed under the server name instead of the standard text (e.g., "VMess", "VLESS", "Trojan").
* Maximum length — 30 characters.
* If it doesn't fit on the screen, it will be shortened with an ellipsis.
* Set after `title` via the `?` separator.
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
<summary>Subscription fragmentation and fronting</summary>
Some CDNs support domain fronting. This allows connecting to your site through a third-party domain.
For example, by specifying the connection address `visa.com` and Host header `my-domain.com`, the provider will only see a request to `visa.com`.
You can also access your domain for the server list using packet fragmentation in SNI TLSHello.
By default, fragmentation is enabled for all subscriptions. The user can add the subscription only once; on repeat attempts, if the account is not premium, the update will not be allowed.
#### URL scheme with parameters
```
[link]#title?[fragment]&[resolve-address]&[host]&[insecure]
Fronting:
visa.com/123#MyVPN?resolve-address=visa.com&host=mydomain.com
Fragmentation:
mydomain.com/123#MyVPN?fragment=80-250,10-100,tlshello
```
Fragmentation contains three parameters: `[length]`, `[interval]`, and `[packets]`.
When using fronting, first specify the URL with the domain through which the connection will be made. Also set `resolve-address` — this can be a domain or IP address — and `host`, corresponding to your host in the selected provider's network.
</details>
<details>
<summary>Advanced fragmentation</summary>
This feature is currently in closed testing and will be available soon...
</details>
<details>
<summary>Non-disableable HWID</summary>
By default, HWID is enabled in all Happ apps. But if you want the user to be unable to disable the transmission of this parameter by turning it off in the app settings, you can send a special parameter with the subscription.
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
<summary>Subscription expiration notification</summary>
You can enable automatic notifications about subscription expiration.\
The user will receive reminders 3 days before expiration: the app will send one notification per day for three days. This helps the user not forget to renew the subscription on time.
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
<summary>Hide server settings in subscription</summary>
<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>
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
<summary>Domain resolution</summary>
The app can perform preliminary domain resolution for servers before establishing a connection.\
You can specify any DoH server, and when connecting to an Xray server, the domain name will be replaced with the received IP address.
If multiple IP addresses are returned for a domain, the app will automatically select the one with the minimum response time (ping).\
However, note: with a large number of IP addresses, connection may take longer as all options will be pre-tested.
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
#### Application settings management <a href="#application-settings-management" id="application-settings-management"></a>
{% hint style="warning" %}
Requires [Provider ID](provider-id.md) parameter!
{% endhint %}
<details>
<summary>Auto-connect</summary>
Allows automatically connecting the user to servers when launching the app. Additionally, using the **subscription-autoconnect-type** parameter, you can specify the criterion for connecting to a specific server.
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
<summary>Auto-ping</summary>
Run automatic server list testing when opening the app if necessary.
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
<summary>Subscriptions auto-update</summary>
In the app, you can enable or disable auto-update for all subscriptions at once — this setting applies to all subscriptions simultaneously. If you need to set auto-update only for a specific subscription, use the Subscription auto-update functionality. When the global setting is disabled, each subscription independently determines its update time.
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
#subscription-auto-update-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}
</details>
<details>
<summary>Fragmentation</summary>
This is a global fragmentation management parameter for all subscriptions. If you need to assign fragmentation only to a specific subscription or server, use the free functionality and instructions from the general app documentation. When the global setting is disabled, each subscription independently determines fragmentation settings.
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
This function allows selecting the ping execution method in the app. Three options are available: “via Proxy”, “TCP”, and “ICMP”. For “via Proxy” mode, you can additionally specify a URL for ping checking.
**Example of setting this parameter:**
```
ping-type: ["proxy", "proxy-head", "tcp","icmp"]
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
#ping-type: proxy
#check-url-via-proxy: https://cp.cloudflare.com/generate_204
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}
</details>
<details>
<summary>User-Agent</summary>
This function allows changing the User-Agent used in headers when fetching the subscription. Useful when the provider blocks requests with non-standard or unsuitable headers.
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
<summary>App auto-start</summary>
This function allows automatically launching the app when the device is turned on. Currently available only on Android.&#x20;
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
<summary>Update subscription on app launch</summary>
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
<summary>Proxy for selected apps (Android)</summary>
This parameter allows specifying a list of apps that should use VPN or, conversely, bypass it. If an app is not yet installed on the device but is listed, it will be automatically taken into account on first VPN connection after installation.
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
<summary>Packet analysis (Sniffing)</summary>
In **xray-core**, sniffing is needed to analyze the first packets of a connection and automatically determine the **protocol** (HTTP, TLS, BitTorrent, etc.) and **domain** (SNI/Host).\
May affect media loading in the WeChat app. Enabled by default.\
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
<summary>Disable subscription collapsing</summary>
<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>
This function disables the ability to collapse subscriptions: the server list is always displayed fully expanded.\
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
<summary>Ping display mode</summary>
<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>
Allows displaying icons instead of time values.\
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
Mux in xray-core is a multiplexing function that allows transmitting data from multiple virtual TCP connections over one physical TCP connection. It is designed to reduce delays from TCP handshakes but not to increase bandwidth (may even slow down large downloads). Configured in outbound with parameters like enabled and concurrency (min -1, max 1024).
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
<details>
<summary>Proxy / TUN mode (Desktop only)</summary>
<mark style="color:$warning;">**Use only one**</mark> of the two listed parameters! These parameters determine the connection type when adding/updating the subscription.
**Example of setting this parameter:**
```
proxy-enable: [true / 1]
tun-enable: [true / 1]
```
**Transmission methods:**
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
Determines which mode will be used for TUN connection.
* **`system`** — uses the OS system network stack.\
  Fast and efficient, but depends on correct route and firewall settings.
* **`gvisor`** — gVisor userspace stack.\
  Fewer dependencies on kernel rules and conflicts with iptables/nftables/Docker, better isolation; possible slight performance penalty.
**Example of setting this parameter:**
```
tun-mode: [system,gvisor]
```
**Transmission methods:**
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
Determines which core will be used for TUN connection. Available: [sing-box](https://github.com/SagerNet/sing-box), [tun2proxy](https://github.com/tun2proxy/tun2proxy)
**Example of setting this parameter:**
```
tun-type: [singbox, tun2proxy]
```
**Transmission methods:**
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
Determines the list of subnets and IP addresses whose traffic should not pass through the tunnel.\
Addresses are specified in one line, separated by spaces and commas.
**Example of setting this parameter:**
```
exclude-routes: [String]
```
**Transmission methods:**
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
