# Hysteria2

**URI Scheme**

The Hysteria 2 URI scheme is designed to provide a compact representation of the information required to connect to a Hysteria 2 server.\
It includes various parameters such as the server address, authentication credentials, obfuscation type and settings, and TLS configurations.

**Structure**

```
hysteria2://[auth]@[hostname]:[port]/?[key=value]&[key=value]...
hy2://[auth@]hostname[:port]/?[key=value]&[key=value]...
```

* **Authentication** - auth

Authentication credentials must be specified in the auth component of the URI.\
A special case occurs when the server uses userpass authentication; in this scenario, the auth component must be formatted as username:password.

* **Hostname** - hostname

The server's hostname and an optional port. If the port is omitted, it defaults to 443.
The port section supports a "multi-port" format, which is a specialized address format:

```
example.com:1234,5678,9012
example.com:20000-50000
example.com:1234,5000-6000,7044,8000-9000
There is no limit to the number of ports specified.
```

The client will randomly select one of the specified ports for the initial connection and will periodically switch to a different port. The interval is controlled by the interval parameter (often referred to as mportHopInt) within the udphop section:

```
"udphop": {
  "port": "1234,5000-6000",
  "interval": "30"
}
```

Query Parameters
* **obfs**: The type of obfuscation used. Currently, only salamander is supported.
* **obfs-password**: The password required for the specified obfuscation type, if applicable.
* **sni**: Server Name Indication used for TLS connections. If the hostname is a domain name and sni is missing, the hostname will be used as the serverName.