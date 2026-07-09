# 系统要求

## 架构与技术
为了避免您对系统要求有所疑问，了解应用程序的架构非常重要：
* **移动端版本 (iOS / Android) 和 macOS App Store 版本:** 使用 **原生语言** 开发 (Apple 使用 Swift，Android 使用 Kotlin)。这确保了与系统的最大集成度、较低的电池消耗和极高的运行速度。
* **桌面端版本 (Windows, macOS DMG, Linux):** 使用现代跨平台框架 **Qt 6** 开发。

---

## 最低系统要求
请确保您的设备满足以下要求：

* **iOS / iPadOS:** iOS 15 及更高版本。
* **macOS (App Store 版本):** macOS 15 及更高版本 (使用 Catalyst 技术)。
* **Android:** Android 5.0 及更高版本。
* **桌面端 (基于 Qt 6):**
  * **Windows:** Windows 10 (内部版本 1809 或更高) 或 Windows 11。
  * **macOS (.dmg 安装程序):** macOS 13 及更高版本。
  * **Linux:** 现代发行版，如 Ubuntu 22.04+、Debian 11.6+、Red Hat 8.10+ (系统级别需要 GCC 10+ 和 glibc 2.31+)。
  * 🔗 [了解有关 Qt 6 支持平台的更多信息](https://doc.qt.io/qt-6/supported-platforms.html)
* **电视端 (TV):** Android TV 5.0+ 或 Apple TV (tvOS 15+)。

---

## ⚠️ 如果我使用的是旧版 Windows、Linux 或 macOS 怎么办？

由于现代桌面版本基于 **Qt 6** 框架，它们 **无法在** 过时的操作系统上运行 (例如 Windows 7、Windows 8，或缺少必要库版本的旧版 Linux/macOS)。

如果您的系统不满足上述最低要求，**您仍然可以使用该应用程序**。为此，请下载专为支持旧系统而构建的 Legacy (旧版) 版本 (1.0.2)：

👉 **[下载适用于旧版操作系统的 Happ Desktop 1.0.2 版本](https://github.com/Happ-proxy/happ-desktop/releases/tag/1.0.2)**
