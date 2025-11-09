# Ping

### Ping (Connection Latency)

**Ping** shows how many milliseconds it takes for a server to respond to a request. Lower value = faster and more stable connection. Remember: Ping reflects latency, not bandwidth.

***

#### How to Check Ping

**1) For an entire subscription**

<figure><img src="../.gitbook/assets/0001-min.png" alt="" width="188"><figcaption></figcaption></figure>

1. Open the main screen.
2. Tap the speedometer icon in the header of the desired subscription.
3. The Ping for each server in that subscription will appear next to it.

<figure><img src="../.gitbook/assets/0002-min.png" alt="" width="188"><figcaption></figcaption></figure>

**2) For an individual configuration**

<figure><img src="../.gitbook/assets/0003-min (1).png" alt="" width="188"><figcaption></figcaption></figure>

1. On the main screen, swipe the configuration element to the right — an actions panel will appear.
2. Tap the speedometer icon — the Ping for this specific configuration will be displayed.

**3) For the current connection**

1. Tap **"Check Current Connection"**.
2. It will display:
   * Ping value in milliseconds (always **ms**);
   * **"Timeout"** error if unavailable.

***

#### What Affects Ping

* Server distance (closer = lower latency);
* Quality and load of your internet channel;
* Network and device load;
* Background processes (downloads, updates, etc.).

***

#### Ping Types in Happ

The app supports three measurement methods. They solve different tasks and may show slightly different results.

**ICMP Ping**

Checks basic network availability with ICMP packets (similar to the `ping` command).

* Requires **temporarily disconnecting the VPN tunnel**.
* Used less frequently due to inconvenience in daily use.

**TCP Ping**

Measures the time to establish a TCP connection to the server.

* **Does not require** disconnecting the VPN tunnel.
* May reflect latency to the **nearest CDN point** if the server uses a content network — so actual latency to the final node may differ.

**Ping via Proxy**

Measures latency **through the active VPN connection**, accounting for the entire path.\
This is the most indicative method for users.

**How the check works:**

1. The app resolves the server's domain name (if a domain is specified).
2. Establishes a TCP connection; performs TLS handshake if necessary.
3. The test resource's domain is resolved on the server side.
4. The server establishes a TLS connection with the target site (if HTTPS).
5. Measures the time to receive a response from the target resource.

**Advantages:**

* Accounts for encryption and the entire data route;
* Provides the most realistic latency value when working with VPN.

**Via Proxy Modes:**

* **Via Proxy GET** — used **by default**; standard HTTP request.
* **Via Proxy HEAD** — request without body; **slightly lighter** on servers.

***

#### How to Change Ping Display Method

**Path:** Settings → **Ping**

Two options are available:

* **Time (ms)** — precise latency value (e.g., _42 ms_).
* **Status Icon** — availability only:
  * green with checkmark — server is available;
  * red with exclamation mark — server is unavailable.

> The selected option is saved automatically and applies to all servers.

***

#### Automatic Check on Launch

The **"Ping on Launch"** feature checks the availability of all servers at once when opening the app — you immediately see the current status without manual testing.

**How to enable:**\
Settings → **Subscriptions** → enable **"Ping on Launch"**.

<figure><img src="../.gitbook/assets/0004-min (1).png" alt="" width="188"><figcaption></figcaption></figure>

After activation, Ping is measured for all servers and their status is updated (response time or icon) every time the app launches.

***

#### Usage Tips

* Compare Ping **under identical conditions** (same network, similar device load).
* Repeat tests: one-off latency spikes are possible due to network overload.
* For assessing real user experience, focus on **Ping via Proxy**.
