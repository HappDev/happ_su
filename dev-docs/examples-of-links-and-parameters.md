# 链接和参数示例

##

{% hint style="warning" %}
此信息**不是 VPN 配置指南**，也**不用于绕过封锁、访问违反您所在国家法律的禁止网站或应用程序**。
{% endhint %}

#### 参数

<details>

<summary>allowinsecure</summary>

允许在不验证 TLS 证书的情况下建立连接。\
在配置 URL 中传递：

* **VMess** 中指定为：\
  `"allowInsecure": "1"`
* 其他协议中作为 URL 参数：\
  `allowInsecure=1`

</details>

<details>

<summary>分片与「噪声」(fragmentation / noises)</summary>

Xray 中的分片是将**出站流量拆分为更小的片段**的机制，具有可控的发送间隔和模式。\
`noises` 是分片的补充，通过添加**伪数据包**来增加行为的多样性。

> `noises` **仅在启用分片时**生效。

***

#### 配置位置

* **全局** — 在应用通用设置中启用，作用于**所有**订阅和服务器。\
  参见章节：[应用管理](https://www.happ.su/main/dev-docs/app-management)
* **本地（针对特定服务器）** — 在应用内**该**服务器的设置中启用。

**同时启用时的行为：**\
如果分片/「噪声」在**全局和本地均启用**，则应用**全局配置**。本地配置用于当全局**关闭**时，仅在特定服务器上启用该功能。

***

#### 1) 分片 (fragmentation)

**字符串格式**

```
fragment=length,interval,packets[,maxSplit]
```

**参数说明**

* **length** — 片段长度，格式为 `Int32Range`（例如 `3` 或 `1-3`）。
* **interval** — 片段间隔，格式为 `Int32Range`（例如 `1` 或 `1-5`）。
* **packets** — 数据包类型（例如 `tlshello`）。
* **maxSplit** _（可选）_ — 最大拆分数量，格式为 `Int32Range`（例如 `100` 或 `100-200`）。\
  从 **Xray 25.9.5** 版本开始支持。

> `Int32Range` — 单个数字或 `min-max` 范围；使用范围时会动态选择数值。

**示例（仅针对特定服务器）**

*   **VMess（JSON 字段）：**

    ```json
    "fragment": "1-10,5-20,tlshello,100-200"
    ```
*   **其他协议（字符串形式）：**

    ```
    fragment=3,1,tlshello,100-200
    ```

    `maxSplit` 可省略：

    ```
    fragment=3,1,tlshello
    ```

***

#### 2) 「噪声」(noises)

**字符串格式**

```
noises=type,packet,delay[,applyTo]
```

**参数说明**

* **type** — `rand` | `str` | `base64`
* **packet** — 内容：
  * 当 `rand` 时 — 长度或范围，格式为 `Int32Range`（例如 `50` 或 `50-150`）；
  * 当 `str` 时 — 字符串（例如 `string`）；
  * 当 `base64` 时 — base64 字符串（例如 `7nQBAAABAAAAAAAABnQtcmluZwZtc2VkZ2UDbmV0AAABAAE=`）。
* **delay** — 延迟，格式为 `Int32Range`（例如 `10-50`）。
* **applyTo** _（可选）_ — 应用范围：`ip` _（默认）_、`ipv4`、`ipv6`。

**示例（仅针对特定服务器）**

*   **VMess（JSON 字段）：**

    ```json
    "noises": "rand,50-150,10-50,ip"
    ```
*   **其他协议（字符串形式）：**

    ```
    noises=rand,50-150,10-50,ip
    ```

    `applyTo` 可省略：

    ```
    noises=rand,50-150,10-50
    ```

***

**注意事项与常见错误**

* 使用**不带空格的逗号**。
* 范围必须有效（`min <= max`）。
* 未激活分片时，`noises` **不会生效**。
* 过小的 `length`、过短的 `interval` 或过大的 `maxSplit` 可能会降低速度并增加延迟。

</details>

<details>

<summary>title</summary>

服务器名称（最多 30 个字符）。\
如果宽度超出屏幕，显示名称可能会被截断并以省略号（`...`）结尾。\
在配置字符串末尾、以 `#` 符号后指定。

**示例：**\
`vmess://...#Мой_Сервер`

</details>

<details>

<summary>serverDescription</summary>

仅适用于本地服务器列表。对于订阅需要 `ProviderID` 参数。\
允许设置额外说明文字，该文字显示在服务器名称下方，代替标准文本（例如 "VMess"、"VLESS"、"Trojan"）。

* 最大长度为 30 个字符。
* 如果无法完整显示，将以省略号截断。
* 在 `title` 之后通过分隔符 `?` 设置。

**示例：**\
`vmess://...#MyServer?serverDescription=<base64>`

**JSON 示例：**\
`"meta":{`\
`"serverDescription":"此处为无需 base64 的文本！"`\
`}`

</details>

<details>

<summary>Socks 代理</summary>

以下是应用可解析的同一配置的三种变体示例：

**示例：**

```
socks://user123:pass321@12.8.8.8:443
socks://dXNlcjEyMzpwYXNzMzIx@12.8.8.8:443#name
socks://dXNlcjEyMzpwYXNzMzIxQDEyLjguOC44OjQ0Mw==
```

</details>
