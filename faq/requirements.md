# System Requirements

## Architecture and Technologies
To avoid any confusion as to why the requirements differ, it is important to understand the application's architecture:
* **Mobile versions (iOS / Android) and the macOS App Store version:** Developed using **native languages** (Swift for Apple, Kotlin for Android). This ensures maximum system integration, low battery consumption, and high performance.
* **Desktop versions (Windows, macOS DMG, Linux):** Developed using the modern cross-platform framework **Qt 6**. 

---

## Minimum System Requirements
Ensure your device meets the following requirements:

* **iOS / iPadOS:** iOS 15 and newer.
* **macOS (App Store version):** macOS 15 and newer (using Catalyst technology).
* **Android:** Android 5.0 and newer.
* **Desktop (Qt 6 based):**
  * **Windows:** Windows 10 (build 1809 or later) or Windows 11.
  * **macOS (.dmg installer):** macOS 13 and newer.
  * **Linux:** Modern distributions such as Ubuntu 22.04+, Debian 11.6+, Red Hat 8.10+ (requires GCC 10+ and glibc 2.31+ at the system level).
  * 🔗 [More information on Qt 6 supported platforms](https://doc.qt.io/qt-6/supported-platforms.html)
* **TV:** Android TV 5.0+ or Apple TV (tvOS 15+).

---

## ⚠️ What to do if I have an older version of Windows, Linux, or macOS?

Since modern Desktop versions are based on the **Qt 6** framework, they **will not run** on outdated operating systems (e.g., Windows 7, Windows 8, or older Linux/macOS builds that lack the necessary library versions).

If your system does not meet the minimum requirements listed above, **you can still use the application**. To do so, download the special Legacy version (1.0.2), which was built to support older systems:

👉 **[Download Happ Desktop version 1.0.2 for older OS](https://github.com/Happ-proxy/happ-desktop/releases/tag/1.0.2)**
