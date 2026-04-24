# Hysteria2

**URI 方案 (URI Scheme)**

Hysteria 2 的 URI 方案旨在以简洁的方式提供连接 Hysteria 2 服务器所需的所有必要信息。
它包含各种参数，例如服务器地址、认证信息、混淆类型及其参数，以及 TLS 设置。

**结构 (Structure)**

```
hysteria2://[auth]@[hostname]:[port]/?[key=value]&[key=value]...
hy2://[auth@]hostname[:port]/?[key=value]&[key=value]...
```

* **认证** - auth

身份验证凭据必须在 URI 的 auth 部分指定。
特殊情况：当服务器使用 userpass（用户名密码）认证时，auth 部分的格式应为 username:password。

* **主机名** - hostname

服务器的主机名和可选端口。如果省略端口，则默认使用 443。
端口部分支持“多端口”格式，这是一种特殊的地址格式：

```
example.com:1234,5678,9012
example.com:20000-50000
example.com:1234,5000-6000,7044,8000-9000
指定的端口数量没有限制。
```

客户端会从指定的端口中随机选择一个用于初始连接，并定期切换到另一个端口。间隔控制参数位于 udphop 部分的 interval（即 mportHopInt）：

```
"udphop": {
  "port": "1234,5000-6000",
  "interval": "30"
}
```

查询参数 (Query Parameters)

* **obfs**: 所使用的混淆类型。目前仅支持 salamander。
* **obfs-password**: 指定混淆类型所需的密码（如果适用）。
* **sni**: 用于 TLS 连接的服务器名称指示（Server Name Indication）。如果 hostname 是域名且未提供 sni 参数，则 hostname 将被用作 serverName。