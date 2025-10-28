# 链接和参数的示例

<details>

<summary>allowinsecure</summary>

允许在不验证 TLS 证书的情况下建立连接。\
在配置链接中设置：

* **VMess** 使用：\
  `"allowInsecure": "1"`
* 其他协议使用：\
  `allowInsecure=1`

</details>

<details>

<summary>fragmentation</summary>

启用数据分片功能。可通过应用全局设置或单独对某个服务器设置：

* **全局设置** — 适用于所有连接
* **单服务器设置**：
  * **VMess**：\
    `"fragment": "1-10,5-20,tlshello"`
  * **其他协议**：\
    `fragment=3,1,tlshello`

示例说明：\
`1-10` 表示随机包大小在 1 到 10 字节之间\
`tlshello` 模拟 TLS 握手以伪装流量

</details>

<details>

<summary>title</summary>

服务器名称，最多 30 个字符。\
如果超过屏幕宽度，将显示省略号（`...`）。\
通过配置末尾的 `#` 指定。

**示例：**\
`vmess://...#我的服务器`

</details>

<details>

<summary>serverDescription</summary>

仅在设置了 `ProviderID` 参数时生效。\
可在服务器名称下方显示描述信息，替代默认的协议类型（如 "VMess", "VLESS", "Trojan"）。

* 最多 30 个字符
* 超出部分将显示为省略号
* 通过 `?` 在名称之后添加

**示例：**\
`vmess://...#MyServer?serverDescription=<base64>`

**JSON 示例：**

`"meta": {`\
`"serverDescription": "这里是没有 base64 的文本！"`\
`}`

</details>
