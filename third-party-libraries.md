---
hidden: true
noIndex: true
---

# Third-party Libraries

{% tabs %}
{% tab title="Android" %}

{% endtab %}

{% tab title="iOS/Mac" %}

{% endtab %}

{% tab title="Desktop " %}
## Third-Party Licenses - Happ Desktop

This document lists all external software dependencies used in Happ Desktop and their respective licenses.

***

### Core Libraries (Bundled/Linked)

| Dependency            | Version   | License              | Verification Link                                                                                        |
| --------------------- | --------- | -------------------- | -------------------------------------------------------------------------------------------------------- |
| **Qt 6**              | 6.10.0    | LGPL v3 / Commercial | [doc.qt.io/qt-6/licensing.html](https://doc.qt.io/qt-6/licensing.html)                                   |
| **OpenSSL**           | 3.4 / 3.6 | Apache 2.0           | [openssl-library.org/source/license](https://openssl-library.org/source/license/index.html)              |
| **SingleApplication** | 3.6.0     | MIT                  | [github.com/itay-grudev/SingleApplication](https://github.com/itay-grudev/SingleApplication)             |
| **QZXing**            | -         | Apache 2.0           | [github.com/ftylitak/qzxing/blob/master/LICENSE](https://github.com/ftylitak/qzxing/blob/master/LICENSE) |
| **ZXing** (in QZXing) | -         | Apache 2.0           | [github.com/zxing/zxing/wiki/License-Questions](https://github.com/zxing/zxing/wiki/License-Questions)   |
| **xpack**             | -         | Apache 2.0           | [github.com/xyz347/xpack/blob/master/LICENSE](https://github.com/xyz347/xpack/blob/master/LICENSE)       |

***

### External Tools (Downloaded & Bundled at Build Time)

| Dependency               | Version  | License | Verification Link                                                                                                                        |
| ------------------------ | -------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Xray-core**            | 25.10.15 | MPL 2.0 | [github.com/XTLS/Xray-core/blob/main/LICENSE](https://github.com/XTLS/Xray-core/blob/main/LICENSE)                                       |
| **sing-box**             | 1.12.12  | GPL v3+ | [github.com/SagerNet/sing-box/blob/main/LICENSE](https://github.com/SagerNet/sing-box/blob/main/LICENSE)                                 |
| **tun2proxy**            | 0.7.15   | MIT     | [github.com/tun2proxy/tun2proxy](https://github.com/tun2proxy/tun2proxy)                                                                 |
| **byedpi**               | 0.17     | MIT     | [github.com/hufrea/byedpi](https://github.com/hufrea/byedpi)                                                                             |
| **Mullvad Split Tunnel** | -        | GPL v3  | [github.com/mullvad/win-split-tunnel/blob/master/LICENSE-GPL.md](https://github.com/mullvad/win-split-tunnel/blob/master/LICENSE-GPL.md) |

***

### Build & Deployment Tools

| Dependency                | License           | Verification Link                                                                                                                |
| ------------------------- | ----------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| **linuxdeploy**           | MIT               | [github.com/linuxdeploy/linuxdeploy/blob/master/LICENSE.txt](https://github.com/linuxdeploy/linuxdeploy/blob/master/LICENSE.txt) |
| **linuxdeploy-plugin-qt** | MIT               | [github.com/linuxdeploy/linuxdeploy-plugin-qt](https://github.com/linuxdeploy/linuxdeploy-plugin-qt)                             |
| **Inno Setup**            | Custom Permissive | [jrsoftware.org/files/is/license.txt](https://jrsoftware.org/files/is/license.txt)                                               |

***

### Summary by License Type

| License        | Dependencies                                      |
| -------------- | ------------------------------------------------- |
| **Apache 2.0** | OpenSSL, QZXing, ZXing, xpack                     |
| **MIT**        | SingleApplication, tun2proxy, byedpi, linuxdeploy |
| **LGPL v3**    | Qt 6                                              |
| **GPL v3**     | sing-box, Mullvad Split Tunnel                    |
| **MPL 2.0**    | Xray-core                                         |
| **Custom**     | Inno Setup                                        |

***

### License Compliance Notes

#### Copyleft Licenses (Require Attention)

**sing-box (GPL v3+)**

The GPL requires that if you distribute binaries, you must offer source code. Since sing-box is distributed as a separate executable (not linked), your application code is NOT affected, but you must:

* Include GPL license text
* Provide/offer source code access for sing-box

**Mullvad Split Tunnel (GPL v3)**

Same requirements as sing-box.

**Xray-core (MPL 2.0)**

More permissive than GPL. You must:

* Include MPL license text
* Make source code available for any modifications to Xray-core itself

**Qt 6 (LGPL v3)**

You must:

* Use dynamic linking (DLLs/.so files) - already implemented
* Provide Qt source code or link to it
* Include LGPL license text
* Allow users to relink with different Qt version

#### Permissive Licenses (Minimal Obligations)

**Apache 2.0 (OpenSSL, QZXing, xpack)**

* Include license and copyright notices

**MIT (SingleApplication, tun2proxy, byedpi, linuxdeploy)**

* Include license and copyright notices

***

### Full License Texts

For full license texts, please refer to the following:

* **Apache 2.0**: https://www.apache.org/licenses/LICENSE-2.0
* **MIT**: https://opensource.org/licenses/MIT
* **LGPL v3**: https://www.gnu.org/licenses/lgpl-3.0.html
* **GPL v3**: https://www.gnu.org/licenses/gpl-3.0.html
* **MPL 2.0**: https://www.mozilla.org/en-US/MPL/2.0/

***

_Last updated: 2025-12-01_
{% endtab %}
{% endtabs %}
