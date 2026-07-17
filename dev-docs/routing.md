# 路由

该应用内置了预装的 Geo 文件，确保安装后即可立即使用。Geo 文件的有效性通过更新应用内的核心版本来保持。

# 架构去中心化

应用实现了从单体全局管理向订阅级模块化管理的转变：
* **独立规则集：** 现在，每个订阅（包括服务器列表 `Server-List`）都拥有自己独立的规则和路由配置文件（“控制面板”），并具有独立的生命周期。
* **变更延迟生效：** 任何设置的修改（如切换路由开关、选择其他配置文件）都会写入数据库，但仅在重新连接（**Reconnect**）后才会生效。
* **级联删除：** 从应用中删除订阅时，与其关联的所有路由配置文件以及磁盘上相应的缓存地理文件都将进行级联删除。

#### **JSON 订阅的处理特点（受限模式 - Restricted Mode）**

为了防止应用设置与提供商元数据之间出现同步断层，JSON 配置采用严格的限制模式：
* **配置文件限制：** 一个 JSON 订阅只能拥有 **0 或 1** 个路由配置文件。
* **仅随订阅绑定：** JSON 配置的路由配置文件无法手动添加、从其他订阅复制或从剪贴板导入。它**完全只能与订阅本身一起**由提供商提供。手动创建和复制功能已被完全禁用。
* **无法禁用或修改：** 用户无法手动管理此类配置文件的启用状态或更改其参数：
  * 主路由开关被强制锁定在 `true` 状态（如果提供商本身发送了禁用指令，则锁定为 `false`）。
  * 修改名称、链接以及地理文件本身（GeoSite/GeoIP 模块）的功能已被完全禁用。
* **Tunnel DNS：** 界面中的 Remote DNS 字段已重命名为 **Tunnel DNS**（Tunnel DNS Type, Tunnel IP, Tunnel Domain），在本地用于配置系统隧道，不会注入到提供商的实际 JSON 文件中。

***

#### 添加路由规则

应用支持通过专用链接自动添加路由规则，这些链接可在 [https://routing.happ.su](https://routing.happ.su) 网站上生成。链接可以通过以下任一方式传递：

* 通过剪贴板
* 使用深度链接
* 扫描二维码
* 作为 HTTP 头或订阅正文的一部分

对于 HTTP 头，将使用路由参数；而在订阅正文中，只需包含链接即可。

#### 处理下载错误

应用使用一个在后台运行的 Geo 文件下载管理器：

* 如果 Geo 文件下载在 3 分钟内未完成，则下载过程会被终止。
* 主屏幕上会显示一条错误信息。
* 配置列表中有问题的配置旁边会显示一个红色感叹号。

#### 故障排除

有问题的配置状态将在以下情况下自动恢复：

* 文件下载成功完成。
* 删除有问题的配置。

当配置列表中不再存在有问题的配置时，错误通知将被移除。

#### 添加 / 更新配置文件

**添加路由配置文件**

在导入路由配置文件时，如果订阅中尚不存在该文件，则会添加该配置文件并将其与该订阅绑定，同时开始下载地理文件。

**更新路由配置文件**

当系统收到导入与现有同名配置文件的命令时，将触发更新流程。

* **初始化更新。** 系统收到新的配置文件导入。该实体进入过渡的 `Update`（更新中）状态。
* **后台下载（保障连接不中断）。** 开始通过更新版本中的链接下载新的地理文件。
  * **重要提示：** 在下载过程中，`Current`（当前）状态保持不变。内核继续使用旧的规则和旧的地理文件运行，以确保无缝路由。
* **下载完成与原子替换。** 一旦更新版本的所有地理文件都成功下载完成：
  * 旧的地理文件将被新文件替换。
  * `Current`（当前）状态将被导入的新规则覆盖。
* **状态同步。** 替换成功后，系统会更新单一实体内部的元数据：
  * `Default`（默认）状态更新 —— 刚刚导入的规则集现在被视为默认规则集。
  * `Update`（更新中）状态被标记为已完成（或被清除），系统恢复到正常工作模式。

#### 链接类型

* `happ://routing/add/{base64}`**:** 向配置列表中添加一个配置文件。首次添加的配置在 Geo 文件成功下载后才会激活。如果已存在同名配置，则会被覆盖。
* `happ://routing/onadd/{base64}`**:** 添加并自动激活配置文件，即使其他配置已处于激活状态。如果已存在同名配置，则会被覆盖。
* `happ://routing/off`**:** 禁用路由功能

其中，`{base64}` 是将 JSON 格式的配置文件转换为 Base64 编码文本后的结果。

#### 配置文件结构

应用使用通过 JSON 配置的路由配置文件。默认配置文件包含用于补全缺失或不正确参数的基本设置。

**示例默认配置文件：**

```json
{
    "GlobalProxy": "true",
    "RemoteDNSType": "DoH",
    "RemoteDNSDomain": "https://cloudflare-dns.com/dns-query",
    "RemoteDNSIP": "1.1.1.1",
    "DomesticDNSType": "DoH",
    "DomesticDNSDomain": "https://dns.google/dns-query",
    "DomesticDNSIP": "8.8.8.8",
    "Geoipurl": "https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geoip.dat",
    "Geositeurl": "https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geosite.dat",
    "DnsHosts": {
        "cloudflare-dns.com": "1.1.1.1",
        "dns.google": "8.8.8.8"
    },
    "DirectSites": [],
    "DirectIp": [
        "10.0.0.0/8",
        "172.16.0.0/12",
        "192.168.0.0/16",
        "169.254.0.0/16",
        "224.0.0.0/4",
        "255.255.255.255"
    ],
    "DomainStrategy": "IPIfNonMatch",
    "FakeDNS": "false"
}
```

**示例自定义配置文件：**

```json
{
    "Name": "China",
    "GlobalProxy": "true",
    "RemoteDNSType": "DoH",
    "RemoteDNSDomain": "https://cloudflare-dns.com/dns-query",
    "RemoteDNSIP": "1.1.1.1",
    "DomesticDNSType": "DoU",
    "DomesticDNSDomain": "",
    "DomesticDNSIP": "8.8.8.8",
    "Geoipurl": "https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geoip.dat",
    "Geositeurl": "https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geosite.dat",
    "LastUpdated": "",
    "DnsHosts": {
        "cloudflare-dns.com": "1.1.1.1"
    },
    "DirectSites": ["geosite:cn", "geosite:geolocation-cn"],
    "DirectIp": [
        "geoip:cn",
        "10.0.0.0/8",
        "172.16.0.0/12",
        "192.168.0.0/16",
        "169.254.0.0/16",
        "224.0.0.0/4",
        "255.255.255.255"
    ],
    "ProxySites": ["geosite:cn"],
    "ProxyIp": ["geoip:amazon"],
    "BlockSites": ["geosite:ads"],
    "BlockIp": ["geoip:ads"],
    "DomainStrategy": "IPIfNonMatch",
    "FakeDNS": "false"
}
```

#### 配置文件管理功能

* 如果已存在同名配置文件，则其数据将被更新。
* 即使配置文件每小时更新一次，Geo 文件每周最多只更新一次。
* 如果配置文件中包含 `"LastUpdated": ""` 参数，并且新值（unix 时间格式）高于之前的值，则更新生效。

**示例 HTTP 头信息：**

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
routing: happ://routing/onadd/ewogICAgIk5hbWUiOiAidGVzdCIsCiAgICAiR2xvYmFsUHJveHkiOiAidHJ1ZSIsCiAgICAiUmVtb3RlRG5zIjogIiIsCiAgICAiRG9tZXN0aWNEbnMiOiAiIiwKICAgICJHZW9pcHVybCI6ICIiLAogICAgIkdlb3NpdGV1cmwiOiAiIiwKICAgICJEbnNIb3N0cyI6IHt9LAogICAgIkRpcmVjdFNpdGVzIjogW10sCiAgICAiRGlyZWN0SXAiOiBbXSwKICAgICJQcm94eVNpdGVzIjogW10sCiAgICAiUHJveHlJcCI6IFtdLAogICAgIkJsb2NrU2l0ZXMiOiBbXSwKICAgICJCbG9ja0lwIjogW10sCiAgICAiRG9tYWluU3RyYXRlZ3kiOiAiQXNJcyIKfQ==
```

**示例订阅正文：**

```
happ://routing/onadd/ewogICAgIk5hbWUiOiAidGVzdCIsCiAgICAiR2xvYmFsUHJveHkiOiAidHJ1ZSIsCiAgICAiUmVtb3RlRG5zIjogIiIsCiAgICAiRG9tZXN0aWNEbnMiOiAiIiwKICAgICJHZW9pcHVybCI6ICIiLAogICAgIkdlb3NpdGV1cmwiOiAiIiwKICAgICJEbnNIb3N0cyI6IHt9LAogICAgIkRpcmVjdFNpdGVzIjogW10sCiAgICAiRGlyZWN0SXAiOiBbXSwKICAgICJQcm94eVNpdGVzIjogW10sCiAgICAiUHJveHlJcCI6IFtdLAogICAgIkJsb2NrU2l0ZXMiOiBbXSwKICAgICJCbG9ja0lwIjogW10sCiAgICAiRG9tYWluU3RyYXRlZ3kiOiAiQXNJcyIKfQ==
vmess://eyJob3N0IjoiZ3Vhdmypc3RhbmJ1bC5jb20iLCJwYXRoIjoiXC8xUyIsInRscyI6InRscyIsImFkZCI6Ind3dy5ndWF2ZWlzdGFuYnVsLmNvbSIsInBvcnQiOjQ0MywiYWlkIjowLCJuZXQiOiJ3cyIsInR5cGUiOiJub25lIiwiZnAiOiJjaHJvbWUiLCJhbHBuIjoiaHR0cFwvMS4xIiwibm9kZV9zc19wdWJsaWNrZXkiOiIiLCIiOmZhbHNlLCJ2IjoiMiIsInBzIjoiXHVkODNjXHVkZGU5XHVkODNjXHVkZGVhIDRHIC0gR2VybWFueSAtIDAxIiwiaWQiOiI4YjhkYWI4NC03OGEzLTNhMWItYTE1NS03M2FkNDk1ZTY0NmUifQ==
vless://70cc43c5-b2f4-34ac-a092-d806984a6b8c@1.13.7.91:443?encryption=none&security=reality&pbk=qGPTy8EZokn3hWp6hKBQ0MVvEuLRJCcv5UdWeP4TVhI&headerType=none&fp=chrome&type=tcp&flow=xtls-rprx-vision&sni=booking.com&sid=6ba85179e30d4fc2#%F0%9F%87%B1%F0%9F%87%B9%20Test
```
