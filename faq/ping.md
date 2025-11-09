# Ping

### Ping（连接延迟）

**Ping** 显示服务器响应请求所需的毫秒数。数值越小，连接越快越稳定。请记住：Ping 反映的是延迟，而非带宽。

***

#### 如何检查 Ping

**1) 检查整个订阅**

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2Fl9jYi2RsvRo204pH7OXN%2Fimage.png?alt=media&#x26;token=7b1bdbee-15d6-4f3c-bd4f-7bab3bab9765" alt="" width="188"><figcaption></figcaption></figure>

1. 打开主屏幕。
2. 在目标订阅的标题栏点击车速表图标。
3. 该订阅下每个服务器旁将显示其 Ping 值。

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2F5fiwfjipoaPhDuhA6SL8%2Fimage.png?alt=media&#x26;token=97065210-5af7-41db-8202-92328ec18c2e" alt="" width="188"><figcaption></figcaption></figure>

**2) 检查单个配置**

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2Fl1s4oOCJ3rdTw90yUk8q%2Fimage.png?alt=media&#x26;token=75a873e6-f980-4914-9cfb-0454489e055e" alt="" width="188"><figcaption></figcaption></figure>

1. 在主屏幕上向右滑动配置项，操作面板将会出现。
2. 点击车速表图标，将显示此配置的 Ping 值。

**3) 检查当前连接**

1. 点击“**检查当前连接**”。
2. 将显示：
   * Ping 值（毫秒，始终显示为 **ms**）；
   * 如无法访问，则显示“**超时**”错误。

***

#### 影响 Ping 的因素

* 服务器距离（距离越近，延迟越小）；
* 您的互联网线路质量和负载；
* 网络和设备的负载；
* 后台进程（下载、更新等）。

***

#### Happ 中的 Ping 类型

应用支持三种测量方式。它们用于解决不同的问题，可能会产生略有不同的结果。

**ICMP Ping**

使用 ICMP 数据包检查基础网络可达性（类似于 `ping` 命令）。

* 需要暂时断开 VPN 隧道。
* 由于日常使用不便，使用频率较低。

**TCP Ping**

测量与服务器建立 TCP 连接所需的时间。

* 无需断开 VPN 隧道。
* 如果服务器使用内容分发网络，可能会反映到最近 CDN 点的延迟，因此到最终节点的实际延迟可能不同。

**通过代理的 Ping (Via Proxy)**

通过活跃的 VPN 连接测量延迟，考虑整个路径。这对用户来说是最具指示性的方法。

**检查如何进行：**

1. 应用解析服务器的域名（如果指定了域名）。
2. 建立 TCP 连接；必要时进行 TLS 握手。
3. 在服务器端解析被测试资源的域名。
4. 服务器与目标网站建立 TLS 连接（如果是 HTTPS）。
5. 测量从目标资源接收响应的时间。

**优点：**

* 考虑了加密和整个数据路由；
* 提供了使用 VPN 时最真实的延迟值。

**Via Proxy 模式：**

* **Via Proxy GET** — 默认使用；标准 HTTP 请求。
* **Via Proxy HEAD** — 无正文请求；对服务器负载稍轻。

***

#### 如何更改 Ping 显示方式

**路径：** 设置 → **Ping**

提供两种选项：

* **时间 (ms)** — 精确的延迟值（例如 _42 ms_）。
* **状态图标** — 仅显示可用性：
  * 绿色带勾 — 服务器可用；
  * 红色带感叹号 — 服务器不可用。

> 所选选项会自动保存并应用于所有服务器。

***

#### 启动时自动检查

“**启动时 Ping**”功能会在打开应用时立即检查所有服务器的可用性，无需手动测试即可立即看到当前状态。

**如何启用：**\
设置 → **订阅** → 启用“**启动时 Ping**”。

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2FFMbbjU0PNkLX7CqcsRvu%2Fimage.png?alt=media&#x26;token=650951c2-6d9a-4ccc-b3c7-33cd25ebd7fd" alt="" width="188"><figcaption></figcaption></figure>

激活后，每次启动应用时都会测量所有服务器的 Ping 值，并更新其状态（响应时间或图标）。

***

#### 使用建议

* 在相同条件下比较 Ping（同一网络，设备负载相似）。
* 重复测试：由于网络过载，可能会出现一次性延迟峰值。
* 评估真实用户体验时，请以\*\*通过代理的 Ping (Via Proxy)\*\*为准。
