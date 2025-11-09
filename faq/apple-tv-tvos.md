# Apple TV (tvOS)

The **Happ — Proxy Utility for TV** application is a **standalone** product, distinct from the iOS version, due to the peculiarities and limitations of the tvOS platform. Details are in the "Features and Limitations of tvOS" section below.

***

#### 1) Import via local network

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2FEbxinW2CB6hZbBzBDS3d%2Fimage.png?alt=media&#x26;token=e676520f-c327-429a-aec3-b229004ac3d8" alt=""><figcaption></figcaption></figure>

On first launch, the **import screen** will automatically open (equivalent to pressing "+"). You can transfer:

* individual server configurations,
* one or more subscriptions,
* or everything at once.

**Requirements:**

* iPhone/Android with Happ installed and Apple TV must be on the **same Wi-Fi network**.
* Scan the **QR code** on the TV screen using Happ on iOS/Android.

**How it works:**

1. Open Happ on iOS/Android.
2. Scan the QR code from the TV screen.
3. Select what to send (configurations/subscriptions) and confirm.

**Important:**

* **Do not close the import screen** on the TV until the transfer is complete — otherwise the connection may be interrupted and data may be imported partially or not at all.
* When transferring from iOS, the system will prompt for **permission to connect to the local network**. If you deny it, the system dialog will not appear again (a quirk of Apple's API), and local requests will be blocked. See the solution in the "Features and Limitations of tvOS" section.

**After transfer:**

* On success, the import screen closes and processing of received data begins (e.g., fetching configurations from subscription URLs).
* On failure (unable to parse configuration or fetch subscription data), the app will display an error message.
* **The QR code is updated automatically**.

***

#### 2) Web import via remote server

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2FjcQiOIZf3AeEL4YohkoR%2Fimage.png?alt=media&#x26;token=e5ecab0f-e9fe-4834-9a38-e8772ed9903b" alt=""><figcaption></figcaption></figure>

If the local network is unavailable or permissions are blocked, use **Web Import**.

**Steps:**

1. On the import screen, select **"Web Import"**.
2. Choose one of the options:
   * Open **tv.happ.su** in any browser, enter the **temporary code** from the TV screen, add the data, and click "Send".
   * Scan the **QR code** from the TV screen — it contains both the URL and the temporary code.

**Important:**

* **Do not close the import screen** on the TV until the operation is complete — otherwise the connection may be closed and data may not be delivered fully.
* **The QR code is updated automatically**.

**Result:**

* After successful transfer, the app will hide the import screen and perform the same actions as with local network import.

***

#### 3) Connection

After successful import, the list of received subscriptions/servers will appear on the **home screen**. The first available server will be selected automatically.

Standard operations are supported:

* server selection,
* connect/disconnect,
* ping,
* subscription update.

Overall behavior matches the iOS/Android/Desktop versions.

***

#### 4) Settings

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2FXBZO5juJcPFlSh5Lz7rL%2Fimage.png?alt=media&#x26;token=3802b4e7-12d3-421e-9289-1eb736d031ed" alt=""><figcaption></figcaption></figure>

Settings on tvOS **visually differ** from those on other platforms.

The key difference is that tvOS does not have classic **routing**. Instead, it offers a simplified **Direct Rules** mechanism:

* A **default Direct Rules list** is built in.
* You can enable/disable and edit them for your needs.

<figure><img src="https://3543042857-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FQmSIGg7AmcgXo76saXyc%2Fuploads%2FlHkcm1uVJyMUcnFJSNPM%2Fimage.png?alt=media&#x26;token=f782e449-97a7-40d9-a51d-4669518cc50a" alt=""><figcaption></figcaption></figure>

***

#### 5) Features and Limitations of tvOS

**Storage and data cleanup**

* Apple TV (tvOS) does not have "guaranteed persistent" storage for applications. When memory is low, the system may **automatically delete saved app data** (configurations/subscriptions). It is recommended to keep important data in subscriptions/on a server and be able to quickly re-import it.

**Tunnel memory limit**

* tvOS (like iOS) strictly limits memory consumption for network tunnels — about **50 MB**. If the limit is exceeded, the system may **terminate the tunnel process** (essentially "disconnecting" the connection). This is a system limitation.

**"Local Network" permission on iOS**

* iOS has a known quirk (API bug): if you selected "Don't Allow" on the first request for **local network permission**, **the system dialog will not appear again**. Even after enabling the permission in app settings, iOS may **continue to block** such connections.
* **Solution:** Reinstall the app on your iOS device (the system will show the dialog again) or use **Web Import**.

***

**Tips**

* If "over-the-air" import fails due to permissions/network issues — **use Web Import right away**: it is reliable and does not depend on local restrictions.
* To minimize data loss risk, keep **current subscriptions** and re-import them to TV in just a couple of steps when needed.
