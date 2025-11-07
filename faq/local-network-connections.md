# Local Network Connections

Use the "Allow connections from LAN" option to share your VPN with devices connected to the same local network or Wi-Fi as you.

**How to Enable This Feature**

* **iOS**: Open the app settings and enable the "Allow connections from LAN" option.
* **Android**: Open the app settings, go to "Advanced Settings," and activate "Allow LAN Connections."

Once enabled, new parameters will appear:

* **Current IP**
* **SOCKS5 Port**
* **HTTP Port**

Connect to the VPN within the app and use these parameters on the device you want to connect to the VPN.

<details>

<summary>Windows</summary>

1. Open **Windows Settings** in one of the following ways:
   * Click the **Start** button (Windows icon) in the lower-left corner of the screen and select the gear icon for **Settings**.
   * Press **Win + I** on your keyboard.
2. Navigate to **Network & Internet**.
3. Select **Proxy** from the left menu.
4. Under **Manual Proxy Setup**, toggle **Use a Proxy Server** to "On."
5. Enter the **Current IP** from the app as the **Address** (e.g., `192.168.1.100`) and the **HTTP Port** as the **Port** (e.g., `10809`).
6. Click **Save**.

</details>

<details>

<summary>Android TV</summary>

Setting up a system-wide proxy on Android TV can vary by model and version. Unfortunately, unlike Android on phones and tablets, Android TV often lacks built-in proxy configuration options in Wi-Fi settings. As a result, you may need to use third-party applications or configure the proxy individually in each app (if supported).

**Steps to Check for Built-In Proxy Settings:**

1. Open the **Settings** on your Android TV.
2. Navigate to **Network** or **Wi-Fi**.
3. Select your connected Wi-Fi network.
4. Look for proxy-related options such as "Proxy Settings." If available, you can enter the **IP Address** and **HTTP Port** here.

</details>

<details>

<summary>macOS</summary>

1. Open **System Settings** (Apple Icon → System Settings or press **Command + Space** and type "System Settings").
2. Navigate to **Network**.
3. Select your active network connection (e.g., **Wi-Fi** or **Ethernet**).
4. Click **Advanced...**.
5. Go to the **Proxies** tab.
6. Check the box for **SOCKS Proxy**.
7. Enter the **SOCKS Proxy Server IP** in the **Server** field and the **Port** in the **Port** field.
8. Click **OK** to save changes.

</details>

<details>

<summary>Linux</summary>

#### Configuring SOCKS Proxy for Specific Applications (e.g., Firefox)

If you need a proxy for a single application, configuring it directly in the app is the simplest approach.

**Firefox Example:**

1. Open **Firefox**.
2. Go to **Settings** (three horizontal lines in the top-right corner) → **General**.
3. Scroll to **Network Settings** and click **Settings...**.
4. Choose **Manual Proxy Configuration**.
5. In the **SOCKS v5** field, enter the **SOCKS Host** (e.g., `192.168.1.100`) and the **Port** (e.g., `10809`).
6. Click **OK**.

#### Other Applications

Some applications may also have built-in proxy settings. Check the settings of the specific app you are using to see if a proxy can be configured directly.

</details>

####
