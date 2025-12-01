---
hidden: true
noIndex: true
---

# Third-party Libraries

{% tabs %}
{% tab title="Android" %}
## Third-Party Licenses — Happ Android

This document lists all external Android software dependencies used in Happ Android and their respective licenses.\
Source file:

***

### Core Libraries (AndroidX, Google, Kotlin, System)

| Dependency Group       | Components                                                                                                                                                                                                       | Version(s) | License    | Verification Link                                                                                                                          |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| **AndroidX**           | activity-ktx, appcompat, camera-_, cardview, constraintlayout, core-splashscreen, datastore, fragment-ktx, legacy-support-v4, lifecycle-_, multidex, preference-ktx, recyclerview, viewpager2, work-\*, leanback | various    | Apache 2.0 | [https://github.com/androidx/androidx/blob/androidx-main/LICENSE.txt](https://github.com/androidx/androidx/blob/androidx-main/LICENSE.txt) |
| **Google Libraries**   | Material Components, Flexbox Layout, Gson, ZXing Core, Play In-App Updates, Firebase BOM + Messaging                                                                                                             | various    | Apache 2.0 | [https://www.apache.org/licenses/LICENSE-2.0](https://www.apache.org/licenses/LICENSE-2.0)                                                 |
| **Kotlin / JetBrains** | kotlin-reflect, kotlinx-coroutines-\*, kotlinx-collections-immutable, kotlinx-datetime, kotlinx-serialization-json                                                                                               | various    | Apache 2.0 | [https://github.com/JetBrains/kotlin/blob/master/license/LICENSE.txt](https://github.com/JetBrains/kotlin/blob/master/license/LICENSE.txt) |
| **Conscrypt**          | conscrypt-android                                                                                                                                                                                                | 2.5.3      | Apache 2.0 | [https://github.com/google/conscrypt/blob/master/LICENSE](https://github.com/google/conscrypt/blob/master/LICENSE)                         |
| **desugar\_jdk\_libs** | desugar\_jdk\_libs                                                                                                                                                                                               | 2.1.5      | Apache 2.0 | [https://github.com/google/desugar\_jdk\_libs/blob/master/LICENSE](https://github.com/google/desugar_jdk_libs/blob/master/LICENSE)         |

***

### Networking, Security & Storage Libraries

| Dependency                 | Version | License    | Verification Link                                                                                                        |
| -------------------------- | ------- | ---------- | ------------------------------------------------------------------------------------------------------------------------ |
| **OkHttp (Square)**        | 4.12.0  | Apache 2.0 | [https://github.com/square/okhttp/blob/master/LICENSE.txt](https://github.com/square/okhttp/blob/master/LICENSE.txt)     |
| **Coil 3 (Image Loading)** | 3.3.0   | Apache 2.0 | [https://github.com/coil-kt/coil/blob/main/LICENSE.txt](https://github.com/coil-kt/coil/blob/main/LICENSE.txt)           |
| **java-jwt (Auth0)**       | 4.5.0   | MIT        | [https://github.com/auth0/java-jwt/blob/master/LICENSE](https://github.com/auth0/java-jwt/blob/master/LICENSE)           |
| **MMKV (Tencent)**         | 1.3.14  | BSD-3      | [https://github.com/Tencent/MMKV/blob/master/LICENSE.TXT](https://github.com/Tencent/MMKV/blob/master/LICENSE.TXT)       |
| **Sentry Android**         | 8.21.1  | MIT        | [https://github.com/getsentry/sentry-java/blob/main/LICENSE](https://github.com/getsentry/sentry-java/blob/main/LICENSE) |

***

### Legacy / Rx / UI Utility Libraries

| Dependency                       | Version | License    | Verification Link                                                                                                                                      |
| -------------------------------- | ------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **RxJava 1.x**                   | 1.3.8   | Apache 2.0 | [https://github.com/ReactiveX/RxJava/blob/1.x/LICENSE](https://github.com/ReactiveX/RxJava/blob/1.x/LICENSE)                                           |
| **RxAndroid 1.x**                | 1.2.1   | Apache 2.0 | [https://github.com/ReactiveX/RxJava/blob/1.x/LICENSE](https://github.com/ReactiveX/RxJava/blob/1.x/LICENSE)                                           |
| **RxPermissions**                | 0.9.3   | Apache 2.0 | [https://github.com/tbruyelle/RxPermissions/blob/master/LICENSE](https://github.com/tbruyelle/RxPermissions/blob/master/LICENSE) (inherited)           |
| **Blacksquircle UI (EditorKit)** | 2.9.0   | Apache 2.0 | [https://github.com/blacksquircle/Android-Code-Editor/blob/master/LICENSE](https://github.com/blacksquircle/Android-Code-Editor/blob/master/LICENSE)   |
| **RoundableLayout**              | 1.1.4   | Apache 2.0 | [https://github.com/zladnrms/RoundableLayout/blob/master/LICENSE](https://github.com/zladnrms/RoundableLayout/blob/master/LICENSE)                     |
| **FABProgressCircle**            | 1.01    | Apache 2.0 | [https://github.com/JorgeCastilloPrz/FABProgressCircle/blob/master/LICENSE](https://github.com/JorgeCastilloPrz/FABProgressCircle/blob/master/LICENSE) |
| **ToastCompat**                  | 1.1.0   | Apache 2.0 | [https://github.com/drakeet/ToastCompat/blob/master/LICENSE](https://github.com/drakeet/ToastCompat/blob/master/LICENSE)                               |
| **BatteryPermissionHelper**      | 1.0.3   | Apache 2.0 | [https://github.com/waseemsabir/BatteryPermissionHelper/blob/main/LICENSE](https://github.com/waseemsabir/BatteryPermissionHelper/blob/main/LICENSE)   |
| **JUnit 4**                      | 4.13.2  | EPL 1.0    | [https://github.com/junit-team/junit4/blob/main/LICENSE-junit.txt](https://github.com/junit-team/junit4/blob/main/LICENSE-junit.txt)                   |

***

### External Tools (Bundled / Runtime Dependencies)

| Dependency    | Description                                               | License | Verification Link                                                                                          |
| ------------- | --------------------------------------------------------- | ------- | ---------------------------------------------------------------------------------------------------------- |
| **Xray-core** | Network core used for tunneling (fork of V2Ray/Xray-core) | MPL 2.0 | [https://github.com/XTLS/Xray-core/blob/main/LICENSE](https://github.com/XTLS/Xray-core/blob/main/LICENSE) |

***

### Summary by License Type

| License          | Dependencies                                                                                                                                                                                                     |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Apache 2.0**   | AndroidX, Google libraries, Kotlin libs, Conscrypt, desugar\_jdk\_libs, OkHttp, Coil, RxJava/RxAndroid/RxPermissions, Blacksquircle UI, RoundableLayout, FABProgressCircle, ToastCompat, BatteryPermissionHelper |
| **MIT**          | java-jwt, Sentry                                                                                                                                                                                                 |
| **BSD-3 Clause** | MMKV                                                                                                                                                                                                             |
| **EPL 1.0**      | JUnit                                                                                                                                                                                                            |
| **MPL 2.0**      | Xray-core                                                                                                                                                                                                        |

***

### License Compliance Notes

#### MPL 2.0 (Xray-core)

* Requires providing access to modified Xray-core source code if distributed.
* Does **not** affect your proprietary application code.
* Include MPL 2.0 license text in your distribution.

#### Apache 2.0 (Most Dependencies)

* Requires preserving copyright notice.
* Requires including license text.
* Patents grant included.

#### MIT (java-jwt, Sentry)

* Very permissive.
* Only attribution required.

#### BSD-3 (MMKV)

* Permissive; attribution required.

#### EPL 1.0 (JUnit)

* Test-only dependency; no runtime distribution obligations.

***

### Full License Texts

* **Apache 2.0** — [https://www.apache.org/licenses/LICENSE-2.0](https://www.apache.org/licenses/LICENSE-2.0)
* **MIT** — [https://opensource.org/licenses/MIT](https://opensource.org/licenses/MIT)
* **BSD-3 Clause** — [https://opensource.org/licenses/BSD-3-Clause](https://opensource.org/licenses/BSD-3-Clause)
* **EPL 1.0** — [https://www.eclipse.org/legal/epl-v10.html](https://www.eclipse.org/legal/epl-v10.html)
* **MPL 2.0** — [https://www.mozilla.org/en-US/MPL/2.0/](https://www.mozilla.org/en-US/MPL/2.0/)

***

_Last updated: 2025-12-01_
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
