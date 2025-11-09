# Apple TV (tvOS)

应用 **Happ — Proxy Utility for TV** 是一个**独立**产品，由于 tvOS 平台的特性和限制，它与 iOS 版本不同。详见下面的“功能与限制”部分。

***

#### 1) 通过本地网络导入

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2FEbxinW2CB6hZbBzBDS3d%2Fimage.png?alt=media&#x26;token=e676520f-c327-429a-aec3-b229004ac3d8" alt=""><figcaption></figcaption></figure>

首次启动时会自动打开**导入屏幕**（相当于点击“+”）。您可以传输：

* 单个服务器配置，
* 一个或多个订阅，
* 或全部内容。

**要求：**

* iPhone/Android 设备上已安装 Happ，且 Apple TV 必须在**同一个 Wi-Fi 网络**中。
* 在电视屏幕上使用 iOS/Android 上的 Happ 扫描**二维码**。

**操作流程：**

1. 在 iOS/Android 上打开 Happ。
2. 扫描电视屏幕上的二维码。
3. 选择要发送的内容（配置/订阅）并确认。

**重要提示：**

* **请勿关闭电视上的导入屏幕**，直到传输完成，否则连接可能中断，数据可能部分导入或完全无法导入。
* 从 iOS 传输时，系统会提示**本地网络连接权限**。如果拒绝，系统对话框不会再次弹出（Apple API 的特性），本地请求将被阻止。解决方法见“功能与限制”部分。

**传输完成后：**

* 成功后，导入屏幕关闭，开始处理接收到的数据（例如，通过订阅 URL 获取配置）。
* 出现错误时（无法解析配置或获取订阅数据），应用会显示错误信息。
* **二维码会自动更新**。

***

#### 2) 通过远程服务器进行网页导入

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2FjcQiOIZf3AeEL4YohkoR%2Fimage.png?alt=media&#x26;token=e5ecab0f-e9fe-4834-9a38-e8772ed9903b" alt=""><figcaption></figcaption></figure>

如果本地网络不可用或被权限阻止，请使用**网页导入**。

**步骤：**

1. 在导入屏幕上选择 **“Web Import”** 。
2. 选择以下任一方式：
   * 在任意浏览器中打开 **tv.happ.su**，输入电视屏幕上的**临时验证码**，然后添加数据并点击“发送”。
   * 扫描电视屏幕上的**二维码**——其中包含地址和临时验证码。

**重要提示：**

* **请勿关闭电视上的导入屏幕**，直到操作完成，否则连接可能关闭，数据将无法完整传输。
* **二维码会自动更新**。

**结果：**

* 传输成功后，应用将隐藏导入屏幕，并执行与本地网络导入相同的操作。

***

#### 3) 连接

成功导入后，**主屏幕**上将显示已接收的订阅/服务器列表。第一个可用服务器将被自动选中。

支持标准操作：

* 服务器选择，
* 连接/断开，
* 延迟测试，
* 订阅更新。

整体行为与 iOS/Android/桌面版一致。

***

#### 4) 设置

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2FXBZO5juJcPFlSh5Lz7rL%2Fimage.png?alt=media&#x26;token=3802b4e7-12d3-421e-9289-1eb736d031ed" alt=""><figcaption></figcaption></figure>

tvOS 上的设置**视觉上与其他平台不同**。

关键区别在于 tvOS 没有经典的**路由**功能，而是提供简化的**直连规则**机制：

* 内置**默认直连规则列表**。
* 您可以根据需要启用/禁用和编辑它们。

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2FlHkcm1uVJyMUcnFJSNPM%2Fimage.png?alt=media&#x26;token=f782e449-97a7-40d9-a51d-4669518cc50a" alt=""><figcaption></figcaption></figure>

***

#### 5) tvOS 的功能与限制

**存储与数据清理**

* Apple TV (tvOS) 没有应用程序的“保证永久”存储空间。当内存不足时，系统可能会**自动删除**已保存的应用数据（配置/订阅）。建议将重要数据保存在订阅/服务器上，并能够快速重新导入。

**隧道的内存限制**

* tvOS（与 iOS 一样）严格限制网络隧道的内存消耗——约**50 MB**。如果超过限制，系统可能会**终止隧道进程**（实际上会“断开”连接）。这是系统限制。

**iOS 的“本地网络”权限**

* iOS 存在一个已知问题（API 缺陷）：如果首次请求**本地网络连接权限**时选择了“不允许”，**系统对话框不会再次弹出**。即使在应用设置中启用了该权限，iOS 仍可能**继续阻止**此类连接。
* **解决方法：** 在 iOS 设备上重新安装应用（之后系统会再次显示对话框），或使用**网页导入**。

***

**提示**

* 如果因权限/网络问题导致“隔空”导入失败——**请立即使用网页导入**：此方法可靠，不依赖本地限制。
* 为最大限度降低数据丢失风险，请**保持订阅最新**，必要时只需几个步骤即可重新导入到电视。
