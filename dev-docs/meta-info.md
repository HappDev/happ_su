---
hidden: true
noIndex: true
---

# 元信息

<figure><img src="../.gitbook/assets/Frame 110.png" alt="" width="375"><figcaption></figcaption></figure>



订阅拥有者可以显示已使用与剩余流量的信息、订阅过期日期、展示公告，并且可以在元数据展示栏中设置最多两个图标链接。所有数据均可使用明文或 base64 格式提供。

元数据可以通过两种方式传输：

* 通过订阅页面的 HTTP 头信息。
* 通过订阅正文传输，方法是在参数前添加 “#” 符号（例如：#profile-title）。

#### 展示参数

**profile-title (string)：**\
配置文件名称，可以以明文或 base64 (UTF-8) 格式提供。\
**限制：** 最大长度 — 25 个字符。

**subscription-userinfo (string)：**\
包含显示流量使用情况及订阅过期日期的信息。

* 进度条左侧显示已消耗的总流量（上传 + 下载），右侧（斜杠后）显示总额度（total）。
* 订阅过期日期通过 expire 参数指定。\
  **注意：** 所有数据包含在单一的头信息中，并以 “;” 字符分隔。

**support-url (string)：**\
支持链接，以蓝色图标显示在展示栏右侧，可点击区域用绿色矩形高亮显示。

**profile-web-page-url (string)：**\
指向配置文件网页的链接。如果指定此参数，图标同样变为蓝色（类似于 support-url），且可点击区域用绿色矩形高亮显示。

**announce (string)：**\
公告文本，可以以明文或 base64 格式提供。\
**限制：** 显示文本的最大长度为 200 个字符。

#### **更新参数**  **profile-update-interval (int)：** 自动更新订阅的间隔，单位为小时。 如果用户在应用设置中指定了更新间隔，此参数将被忽略.

#### 其他建议

* 为确保元数据正确显示，请确保数据格式符合要求（明文或 base64 UTF-8）。
* 订阅正文中指定的参数优先于通过 HTTP 头传递的参数。
* 如果部分参数通过 HTTP 头接收，而其他参数通过订阅正文接收，应将所有参数合并，按照优先级正确显示。

***

#### 示例 HTTP 头信息

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

#### 示例订阅正文

```
#profile-title: Happ.su
#profile-title: base64:U3Vic2NyaXB0aW9u
#profile-update-interval: 1
#subscription-userinfo: upload=455727941; download=6174315083; total=1073741824000; expire=1671815872
#support-url: https://t.me/happ_chat
#profile-web-page-url: https://happ.su
#announce: base64:J1bC5jb20iLCJwYXRoIjoiXC8xUyIsInRscyI6InRscyIsImFkZCI6Ind3dy5ndWF2ZWlzdGFuYnVsLmN
```
