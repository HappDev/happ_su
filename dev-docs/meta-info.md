---
hidden: true
noIndex: true
---

# Meta Info

<figure><img src="../.gitbook/assets/Frame 110.png" alt="" width="375"><figcaption></figcaption></figure>

A subscription owner can display information about consumed and remaining traffic, subscription expiration date, display announcements, and set up to two links for icons in the metadata display bar.

All data can be provided in either plain text or base64 format.

Metadata can be transmitted in two ways:

1. Through the HTTP header of the subscription page.
2. Through the subscription body by prefixing the parameter with the `#` symbol (e.g., `#profile-title`).

### Display Parameters

* **`profile-title`** (string):\
  The profile name. It can be provided as plain text or in base64 (UTF-8).\
  **Limit**: Maximum length — 25 characters.
* **`subscription-userinfo`** (string):\
  Contains information for displaying traffic usage and subscription expiration date.
  * The left side of the progress bar shows the total consumed traffic (`upload + download`), while the right side after the `/` sign displays the total allowance (`total`).
  * The subscription expiration date is specified in the `expire` parameter.\
    **Note**: All data is included in a single header and separated by the `;` character.
* **`support-url`** (string):\
  A support link.
  * Displayed as a blue icon on the right side of the bar.
  * The clickable area is highlighted with a green rectangle.
* **`profile-web-page-url`** (string):\
  A link to the profile web page.
  * If this parameter is specified, the icon becomes blue (similar to `support-url`).
  * The clickable area is also highlighted with a green rectangle.
* **`announce`** (string):\
  Announcement text. It can be provided in plain text or base64 format.\
  **Limit**: The maximum length of displayed text is 200 characters.

### **Update Parameter**

**profile-update-interval (int):** The interval for automatic subscription updates, specified in hours.\
If the user has set an interval in the app settings, this parameter will be ignored.

### Additional Recommendations

* To ensure proper metadata display, make sure the data format meets the requirements (plain text or base64 UTF-8).
* Parameters specified in the subscription body take precedence over those passed through HTTP headers.
* If some parameters are received via HTTP headers and others through the subscription body, all parameters should be merged, respecting their priority, and displayed correctly.

***

### Example **http headers:** <a href="#primer-http-headers" id="primer-http-headers"></a>

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-web-page-url: https://happ.su
support-url: https://t.me//happ_chat
profile-title: base64:0J/QvtC00L/QuNGB0LrQsA==
profile-update-interval: 1
subscription-userinfo: upload=0; download=122190068697; total=0; expire=0
announce: base64:J1bC5jb20iLCJwYXRoIjoiXC8xUyIsInRscyI6InRscyIsImFkZCI6Ind3dy5ndWF2ZWlzdGFuYnVsLmN
cf-cache-status: DYNAMIC
```

### Example subscription bod&#x79;**:** <a href="#primer-tela-podpiski" id="primer-tela-podpiski"></a>

```
#profile-title: Happ.su
#profile-title: base64:U3Vic2NyaXB0aW9u
#profile-update-interval: 1
#subscription-userinfo: upload=455727941; download=6174315083; total=1073741824000; expire=1671815872
#support-url: https://t.me/happ_chat
#profile-web-page-url: https://happ.su
#announce: base64:J1bC5jb20iLCJwYXRoIjoiXC8xUyIsInRscyI6InRscyIsImFkZCI6Ind3dy5ndWF2ZWlzdGFuYnVsLmN
vmess://eyJob3N0IjoiZ3Vhdmypc3RhbmJ1bC5jb20iLCJwYXRoIjoiXC8xUyIsInRscyI6InRscyIsImFkZCI6Ind3dy5ndWF2ZWlzdGFuYnVsLmNvbSIsInBvcnQiOjQ0MywiYWlkIjowLCJuZXQiOiJ3cyIsInR5cGUiOiJub25lIiwiZnAiOiJjaHJvbWUiLCJhbHBuIjoiaHR0cFwvMS4xIiwibm9kZV9zc19wdWJsaWNrZXkiOiIiLCIiOmZhbHNlLCJ2IjoiMiIsInBzIjoiXHVkODNjXHVkZGU5XHVkODNjXHVkZGVhIDRHIC0gR2VybWFueSAtIDAxIiwiaWQiOiI4YjhkYWI4NC03OGEzLTNhMWItYTE1NS03M2FkNDk1ZTY0NmUifQ==
vless://70cc43c5-b2f4-34ac-a092-d806984a6b8c@1.13.7.91:443?encryption=none&security=reality&pbk=qGPTy8EZokn3hWp6hKBQ0MVvEuLRJCcv5UdWeP4TVhI&headerType=none&fp=chrome&type=tcp&flow=xtls-rprx-vision&sni=booking.com&sid=6ba85179e30d4fc2#%F0%9F%87%B1%F0%9F%87%B9%20Test
```
