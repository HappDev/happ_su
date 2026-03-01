---
description: >-
  This document contains a description of supported protocols, methods for
  adding them, and detailed instructions for configuring connection parameters.
---

# Examples of links and parameters

### 1. General Information

The HAPP application supports modern protocols designed for security and censorship circumvention: VLESS, VMess, Shadowsocks, Socks5, Trojan, and Hysteria2 (including the `hy2` scheme).

***

### 2. Ways to Add Configurations

* Manual Entry: Accessed via the "+" button on the main screen. This allows for granular configuration of every protocol parameter.
* URL/QR Import: Automatic recognition of schemes (`vless://`, `vmess://`, etc.) from the clipboard or via the camera.
* Subscriptions:
  * _Standard:_ URLs pointing to text-based lists of configurations.
  * _JSON Arrays:_ Advanced data sets including pre-configured keys, routing rules, and Reality parameters.

***

### 3. Specifics of Working with JSON Configurations

When a server configuration is imported into the HAPP app in JSON format, the app handles it uniquely when interacting with the XRAY core.

#### 3.1. Direct Passthrough Principle (1:1)

When the XRAY core is launched, this JSON configuration is passed exactly as is.

> Important: In this mode, standard HAPP routing rules and interface settings are not applied to the JSON file. The configuration operates strictly according to its source code.

#### 3.2. Indirect Management via HAPP

Despite the direct passthrough, the application maintains control over the core's environment through routing profiles:

* GEO File Management: You can control which Geo-data files are passed to the core for execution.
* Optimization (Trimmed GEO Files): By enabling this feature, the core receives only necessary fragments of the databases (with selected tags), saving system resources.
* DNS Tunneling: Remote DNS settings are inherited from the app's active routing profile and can be adjusted by the user to adapt the system behavior.

***

### 4. Advanced Parameters (URI Scheme)

#### 4.1. Hysteria 2 (`hy2://`)

| **Parameter** | **Description**                                         |
| ------------- | ------------------------------------------------------- |
| `auth`        | Authentication data (`username:password` for userpass). |
| `port`        | Multi-port support: e.g., `1234,5000-6000,7044`.        |
| `obfs`        | Obfuscation type (e.g., `salamander`).                  |
| `mportHopInt` | Interval (seconds) between port hopping.                |

#### 4.2. Fragmentation and Noises

Tools designed to bypass Deep Packet Inspection (DPI). Local server settings take priority only if the app's global settings are disabled.

* Fragmentation: `fragment=length,interval,packets[,maxSplit]`
  * _Example:_ `fragment=1-10,5-20,tlshello`
* Noises (requires fragmentation): `noises=type,packet,delay[,applyTo]`
  * _Example:_ `noises=rand,50-150,10-50,ip`

***

### 5. Visualization and Metadata

To organize your server list, use tags at the end of the URL after the `#` symbol:

1. Title (`title`): `#MyServer` (up to 30 characters).
2. Description (`serverDescription`): Replaces the technical subtitle (e.g., "VMess") with custom text.
   * _Format:_ `#Title?serverDescription=<base64_text>`
   * _In JSON:_ Use the field `"meta": {"serverDescription": "Your text"}`.

***

### 6. Socks5 Proxy Examples

The app parses three different recording formats:

* Plain text: `socks://user:pass@1.2.3.4:443`
* Partial Base64: `socks://<base64_user_pass>@1.2.3.4:443#Name`
* Full Base64: `socks://<full_string_base64>`
