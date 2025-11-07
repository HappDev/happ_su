# Ping

The application supports three types of ping: **ICMP**, **TCP**, and **via Proxy**.

**ICMP Ping**

Uses ICMP packets (similar to the `ping` command in a terminal).\
It is less convenient because it requires temporarily disabling the tunnel to perform the test.

**TCP Ping**

Measures latency by sending a TCP packet directly to the server.\
Does not require disabling the tunnel.\
However, when a CDN is used, it may not reflect the real latency to the destination server — the ping only reaches the nearest CDN node.

**via Proxy Ping**

Runs through the active VPN connection and includes the full path to the target server.\
This is the most accurate and representative method, as it includes all stages of connection, including TLS handshake.

**Example of the via Proxy Ping sequence:**

1. Resolve the server's domain name (if the connection point is specified as a domain).
2. Establish a TCP connection to the server.
3. If TLS is used — initiate a TLS handshake.
4. On the server side, resolve the domain of the test target.
5. Establish a TLS connection to the test site (if it uses HTTPS).
6. Receive and measure the response from the test site.
