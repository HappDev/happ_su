---
description: Manage application settings via subscription
---

# App management

**The application management functionality** includes two areas:

* [Standard parameters](app-management.md#standartnye-parametry) that work for most panels.
* [Advanced parameters](app-management.md#id-rasshirennyifunkcional-opisanieparametrov) for which you need to specify the [Provider ID](provider-id.md\[...)

To enable a parameter, pass the value `true` or `1`; to disable it, pass any other non-empty value.

## Standard Parameters

<details>

<summary>Subscription Auto-Update</summary>

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

A task is created in the system to perform the operation at the specified interval. Depending on internal priorities, the system tries to run the subscription update at the set time.\
If for any reason the update was not performed within the specified interval, it will occur automatically on the next app launch.\
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

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

The name of the subscription profile. Can be passed as plain text or base64 (UTF-8). **Restriction:** Maximum length — 25 characters.

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

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

Displays information about balance, used traffic volume, and subscription expiration date.\
On the left side of the scale in the app, the amount of used traffic (upload + download) is shown, and on the right — the total volume (total) after the "/" symbol.\
The subscription expiration date is specified in the **expire** parameter.\
**Note:** all data is transmitted in one header and separated by the **;** symbol.

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

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

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

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

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

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

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

If your domain is blocked by the provider, and users can only connect to servers and update the subscription via VPN, this parameter is for you. By setting a new domain name in this parameter value, you ensure its automatic replacement for all subscription users.

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

Change the site domain without changing the full URL, keeping the rest of the address.

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

<summary>Fallback URL</summary>

<figure><img src="../.gitbook/assets/image.png" alt="" width="375"><figcaption></figcaption></figure>

If the primary URL is unreachable, returns an error between 300–599, or fails to respond within 9 seconds, the app will switch to the Fallback URL (if provided).

**Example of configuring this parameter:**

```
fallback-url: [url]
```

**Ways to pass it:**

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
#fallback-url https://mynew-domain.com/3J3jrb4jfc
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Server Description in Subscription</summary>

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

Allows setting an additional caption displayed under the server name instead of the standard text (e.g., "VMess", "VLESS", "Trojan").

* Maximum length — 30 characters.
* If it doesn't fit on the screen, it will be shortened with an ellipsis.
* Set after `title` via the `?` separator.

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

<summary>Advanced Announcements</summary>

<div><figure><img src="../.gitbook/assets/5526.png" alt="" width="188"><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/5528.png" alt="" width="188"><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/5527.png" alt="" width="188"><figcaption></figcaption></figure></div>

More prominent announcements divided into two types: custom informational text (sub-info) and system subscription expiration notifications (sub-expire).\
Expiration notifications take priority and are displayed automatically 3 days before or after the subscription expires. The informational block is shown only if there is no active expire-message.\
Both mechanisms can be explicitly disabled via HTTP headers. If parameters are passed and not cancelled, they remain active until the subscription is deleted.

```
| META PARAM KEY             | TYPE     | REQUIRED | LIMITS / VALUES                  | DESCRIPTION                                                                                                          |
|----------------------------|----------|----------|----------------------------------|----------------------------------------------------------------------------------------------------------------------|
| sub-info-color             | String   | No       | red, blue, green (default blue)  | Color of the information block.                                                                                      |
| sub-info-text              | String   | Yes*     | max 200 chars                    | Main text of the info block. The block is hidden if this parameter is missing. An empty string disables the display. |
| sub-info-button-text       | String   | No       | max 25 chars                     | Button text. If omitted, the button will not be displayed.                                                           |
| sub-info-button-link       | String   | No       | any string (URL / deeplink)      | utton link. Opens in the browser; no validation is performed.                                                        |
| sub-expire                 | Boolean  | No       | true \| 1 = enabled              | Enables the subscription expiration notification mechanism.                                                          |
| sub-expire-button-link     | String   | No       | any string (URL / deeplink)      | Link for the "Renew" button. If omitted, the button will not be displayed.                                           |
```

#### Display Logic Summary

```
| CONDITION                                      | RESULT                                          |
|------------------------------------------------|-------------------------------------------------|
| `sub-expire = true` and expiry $\le$ 3 days 	 | Display: "Your subscription expires in N days." |
| `sub-expire = true` and subscription expired	 | Display: "Subscription has expired!" 		   |
| `sub-expire = true` and days > 3 				 | Expiration message is hidden.                   |
| No expiration date set 						 | Expiration info is not displayed.               |
| Active `expire` message exists 				 | `sub-info` block is not shown (suppressed).     |
| No `expire` message and `sub-info-text` exists | Display the `sub-info` block.                   |
| `sub-info-text = ""` 							 | `sub-info` block is disabled.                   |
| `sub-expire ≠ true/1` 						 | Expiration mechanism is disabled.               |
```

#### Notes

```
| NOTE 																								|
|---------------------------------------------------------------------------------------------------|
| Parameters are applied only to the specific subscription for which they were provided. 			|
| If parameters are received via push and not explicitly disabled, they remain active indefinitely. |
| The `expire` button always uses the text "Renew". 												|
| The number of days (N) is calculated as full days, with a maximum of 3. 							|
```



</details>

<details>

<summary>Subscription Fragmentation and Fronting</summary>

Some CDNs support domain fronting. This allows connecting to your site through a third-party domain. For example, by specifying the connection address `visa.com` and Host header `my-domain.com`, the provider will only see a request to `visa.com`. \
You can also access your domain for the server list using packet fragmentation in SNI TLSHello. \
By default, fragmentation is enabled for all subscriptions. The user can add the subscription only once; on repeat attempts, if the account is not premium, the update will not be allowed.

**URL Scheme with Parameters**

```
[link]#title?[fragment]&[resolve-address]&[host]&[insecure]

Fronting:
visa.com/123#MyVPN?resolve-address=visa.com&host=mydomain.com

Fragmentation:
mydomain.com/123#MyVPN?fragment=80-250,10-100,tlshello
```

Fragmentation has three parameters: `[length]`, `[interval]` and `[packets]`.

For fronting, specify the URL with the domain used for connection first, \[...]

</details>

<details>

<summary>Advanced fragmentation</summary>

This feature is currently in closed testing and will be available soon...

</details>

<details>

<summary>Non-disableable HWID</summary>

By default, HWID is enabled in all Happ apps. But if you want the user to be unable to disable the transmission of this parameter by turning it off in the app settings, you can send a special parameter with the subscription.

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
The user will receive reminders 3 days before expiration: the app will send one notification per day for three days. This helps the user not forget to renew the subscription on time.

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

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

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

The app can perform preliminary domain resolution for servers before establishing a connection.\
You can specify any DoH server, and when connecting to an Xray server, the domain name will be replaced with the received IP address.\
If multiple IP addresses are returned for a domain, the app will automatically select the one with the minimum response time (ping).\
However, note: with a large number of IP addresses, connection may take longer as all options will be pre-tested.

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

Allows automatically connecting the user to servers when launching the app. Additionally, using the **subscription-autoconnect-type** parameter, you can specify the criterion for connecting to a specific server.

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

Run automatic server list testing when opening the app if necessary.

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

In the app, you can enable or disable auto-update for all subscriptions at once — this setting applies to all subscriptions simultaneously. If you need to set auto-update only for a specific subscription, use the Subscription auto-update functionality. When the global setting is disabled, each subscription independently determines its update time.

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
#subscription-auto-update-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Fragmentation</summary>

This is a global fragmentation management parameter for all subscriptions. If you need to assign fragmentation only to a specific subscription or server, use the free functionality and instructions from the general app documentation. When the global setting is disabled, each subscription independently determines fragmentation settings.

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

This function allows selecting the ping execution method in the app. Three options are available: “via Proxy”, “TCP”, and “ICMP”. For “via Proxy” mode, you can additionally specify a URL for ping checking.

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

This function allows changing the User-Agent used in headers when fetching the subscription. Useful when the provider blocks requests with non-standard or unsuitable headers.

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

This function allows automatically launching the app when the device is turned on. Currently available only on Android.

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

This parameter allows specifying a list of apps that should use VPN or, conversely, bypass it. If an app is not yet installed on the device but is listed, it will be automatically taken into account on first VPN connection after installation.

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

In **xray-core**, sniffing is needed to analyze the first packets of a connection and automatically determine the **protocol** (HTTP, TLS, BitTorrent, etc.) and **domain** (SNI/Host).\
May affect media loading in the WeChat app. Enabled by default.

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

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

This function disables the ability to collapse a subscription: the server list is always fully displayed.

**Example of configuring this parameter:**

```
subscriptions-collapse: [false / 0]
```

**Ways to pass it:**

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

Upon receiving this parameter via a subscription update, the app will force-expand the subscription if it is collapsed. The `false` value is ignored: the parameter is used only for expanding and cannot be used to collapse the subscription.

**Example of configuring this parameter:**

```
subscriptions-expand-now: [true / 1]
```

**Ways to pass it:**

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

<summary>Ping Display Mode</summary>

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

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

Mux in xray-core is a multiplexing function that allows transmitting data from multiple virtual TCP connections over one physical TCP connection. It is designed to reduce delays from TCP handshakes but not to increase bandwidth (may even slow down large downloads). Configured in outbound with parameters like enabled and concurrency (min -1, max 1024).

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

<mark style="color:$warning;">**Use only one**</mark> of the two listed parameters! These parameters determine the connection type when adding/updating the subscription.

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

Determines which core will be used for TUN connection. Available: [sing-box](https://github.com/SagerNet/sing-box\[...])

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

<details>

<summary>Themes (only for iOS)</summary>

<figure><img src="../.gitbook/assets/image (1).png" alt="" width="375"><figcaption></figcaption></figure>

Allows you to customize the color theme to your preference. You can create your own theme in the editor — just long-press the “Appearance Theme” label to open the menu. The created theme can be exported to the clipboard, as well as imported from the clipboard, from a .happ file, or transferred through a subscription.

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

**Ways to pass it:**

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
