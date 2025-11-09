# Local Network Connections

The **"Allow LAN Connections"** feature lets you share your VPN connection with other devices on the same local network or connected to the same Wi-Fi.\
This is convenient if you want to use one VPN connection on multiple devices — for example, on a TV, console, or another computer.

***

#### 1. How to enable the feature

1. Open the Happ **Settings**.
2. Go to **Advanced Settings**.
3. Activate the **"Allow LAN Connections"** option.
4. Connect to a VPN server in the Happ app.

After activation, additional parameters will appear:

* **Current IP** — the local IP address of the device (e.g., `192.168.1.100`);
* **SOCKS5 Port** — for connecting via SOCKS proxy (e.g., `10808`);
* **HTTP Port** — for connecting via HTTP proxy (e.g., `10809`).

> ⚠️ When this feature is disabled (or the VPN connection is lost), connected devices will lose VPN access.

***

#### 2. Configuring connection on other devices

<details>

<summary>Android</summary>

1. Open your device's **Settings**.
2. Go to **Wi-Fi → select your network**.
3. Tap **Advanced** or **Modify network**.
4. In the **Proxy** section, select **Manual**.
5. Specify:
   * **Proxy hostname**: current IP (e.g., `192.168.1.100`);
   * **Proxy port**: HTTP port (e.g., `10809`).
6. Save the settings and connect to the network.

</details>

<details>

<summary>iOS</summary>

1. Open **Settings → Wi-Fi**.
2. Find the connected network and tap the **ℹ️** icon next to it.
3. Scroll down to the **HTTP Proxy** section.
4. Select **Manual**.
5. Enter:
   * **Server**: current IP (e.g., `192.168.1.100`);
   * **Port**: HTTP port (e.g., `10809`).
6. Go back — settings are saved automatically.

</details>

<details>

<summary>Linux</summary>

1. Open **System Settings**.
2. Go to **Network → Proxy**.
3. Activate **Manual proxy configuration**.
4. Enter:
   * **Address**: current IP (e.g., `192.168.1.100`);
   * **Port**: HTTP port (e.g., `10809`).
5. Save changes.

</details>

<details>

<summary>macOS</summary>

1. Open **System Settings → Network**.
2. Select the active connection (**Wi-Fi** or **Ethernet**).
3. Click **Advanced… → Proxies tab**.
4. Check **SOCKS Proxy** or **HTTP Proxy**.
5. Specify:
   * **Server**: current IP (e.g., `192.168.1.100`);
   * **Port**: SOCKS5 port or HTTP port (e.g., `10808` or `10809`).
6. Click **OK** and **Apply**.

</details>

<details>

<summary>Windows</summary>

1. Open **Windows Settings** (via Start → Settings or **Win+I**).
2. Go to **Network & Internet → Proxy**.
3. In the **Manual proxy setup** section, turn on **Use a proxy server**.
4. Specify:
   * **Address**: value from the _Current IP_ field (e.g., `192.168.1.100`);
   * **Port**: value from the _HTTP Port_ field (e.g., `10809`).
5. Click **Save**.

After this, all system traffic will go through the Happ VPN connection.

</details>

***

#### 3. Using built-in proxy settings in individual applications

Some applications (on all platforms — Windows, macOS, Android, Linux) have their own proxy settings.\
If the system proxy is unavailable or you need individual configuration, set up the proxy directly in the required program.\
This method is especially convenient if you only need a proxy for specific applications — for example, browsers.

<details>

<summary>Firefox configuration example</summary>

1. Open **Settings → General → Network Settings**.
2. Click **Settings…**.
3. Select **Manual proxy configuration**.
4. Specify:
   * **SOCKS5 Host**: current IP (e.g., `192.168.1.100`);
   * **Port**: SOCKS5 port (e.g., `10808`).
5. Click **OK**.

</details>

***

#### 4. Common LAN connection errors

| Symptom                          | Possible cause                                                        | What to do                                                                |
| -------------------------------- | --------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Other device cannot see IP       | Devices are on different networks/subnets (e.g., 2.4 and 5 GHz Wi-Fi) | Connect both devices to the same subnet (the same Wi-Fi network)          |
| Connection cannot be established | Firewall is blocking incoming connections                             | Allow incoming connections for Happ app in firewall settings              |
| Proxy not working on Android TV  | No system proxy support                                               | Use a third-party app (e.g., Happ) or configure proxy in each application |
| Port is occupied                 | Port is used by another process                                       | Change the port in Happ settings                                          |
| VPN is on but IP is unavailable  | Internet connection via mobile network or guest network isolation     | Connect both devices to the same Wi-Fi network                            |
