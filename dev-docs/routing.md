# Routing

The app comes with pre-installed geo files, ensuring it's ready to use immediately after installation. The relevance of geo files is maintained by updating the core version within the app.

### Adding Routing Rules

The app allows you to add routing rules automatically by using special links that can be created on the [https://routing.happ.su](https://routing.happ.su/) website.

The links can be transmitted in one of the following ways:

* Via clipboard.
* Using a deeplink.
* Through a QR code.
* As HTTP headers or subscription body.

For HTTP headers, the `routing` parameter is used, while for subscription bodies, simply including the link is sufficient.

### Handling Download Errors

The app uses a geo file download manager that operates in the background.

* If the geo file download does not complete within 3 minutes, the process is stopped.
* An error message appears on the main screen.
* A red exclamation mark is displayed next to the problematic profile in the profile list.

### Troubleshooting

The problematic profile state automatically resolves after:

* Successfully completing file downloads.
* Deleting the problematic profile.

If there are no more problematic profiles in the list, error notifications are removed.

### Types of Links

* `happ://routing/add/{base64}`: Adds a profile to the profile list. The first added profile becomes active only after geo files are successfully downloaded. If a profile with the same name already exists, it is overwritten.
* `happ://routing/onadd/{base64}`: Adds and automatically activates a profile, even if other profiles are active. If a profile with the same name already exists, it is overwritten.
* `happ://routing/off`: Disable the routing function

`{base64}` is a JSON profile converted into a Base64-encoded text format.

### Profile Structure

The app uses routing profiles configured via JSON.

The default profile contains basic settings used to fill in missing or incorrect parameters.

**Example Default Profile:**

```json
{
    "GlobalProxy": "true",
    "RemoteDNSType": "DoH",
    "RemoteDNSDomain": "https://cloudflare-dns.com/dns-query",
    "RemoteDNSIP": "1.1.1.1",
    "DomesticDNSType": "DoH",
    "DomesticDNSDomain": "https://dns.google/dns-query",
    "DomesticDNSIP": "8.8.8.8",
    "Geoipurl": "https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geoip.dat",
    "Geositeurl": "https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geosite.dat",
    "DnsHosts": {
        "cloudflare-dns.com": "1.1.1.1",
        "dns.google": "8.8.8.8"
    },
    "DirectSites": [],
    "DirectIp": [
        "10.0.0.0/8",
        "172.16.0.0/12",
        "192.168.0.0/16",
        "169.254.0.0/16",
        "224.0.0.0/4",
        "255.255.255.255"
    ],
    "DomainStrategy": "IPIfNonMatch",
    "FakeDNS": "false"
}
```

**Example Custom Profile:**

```json
{
    "Name": "China",
    "GlobalProxy": "true",
    "RemoteDNSType": "DoH",
    "RemoteDNSDomain": "https://cloudflare-dns.com/dns-query",
    "RemoteDNSIP": "1.1.1.1",
    "DomesticDNSType": "DoU",
    "DomesticDNSDomain": "",
    "DomesticDNSIP": "8.8.8.8",
    "Geoipurl": "https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geoip.dat",
    "Geositeurl": "https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geosite.dat",
    "LastUpdated": "",
    "DnsHosts": {
        "cloudflare-dns.com": "1.1.1.1"
    },
  "DirectSites": ["geosite:cn", "geosite:geolocation-cn"],
    "DirectIp": [
        "geoip:cn",
        "10.0.0.0/8",
        "172.16.0.0/12",
        "192.168.0.0/16",
        "169.254.0.0/16",
        "224.0.0.0/4",
        "255.255.255.255"
    ],
  "ProxySites": ["geosite:cn"],
  "ProxyIp": ["geoip:amazon"],
  "BlockSites": ["geosite:ads"],
  "BlockIp": ["geoip:ads"],
    "DomainStrategy": "IPIfNonMatch",
    "FakeDNS": "false"
}
```

### Profile Management Features

* If a profile with the same name already exists, its data is updated.
* Geo files are updated no more than once a week, even if the profile is updated every hour.
* If the profile has a parameter "LastUpdated": "", and it contains a date in unix format that is higher than the previous value.

**Example http headers:**

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
routing: happ://routing/onadd/ewogICAgIk5hbWUiOiAidGVzdCIsCiAgICAiR2xvYmFsUHJveHkiOiAidHJ1ZSIsCiAgICAiUmVtb3RlRG5zIjogIiIsCiAgICAiRG9tZXN0aWNEbnMiOiAiIiwKICAgICJHZW9pcHVybCI6ICIiLAogICAgIkdlb3NpdGV1cmwiOiAiIiwKICAgICJEbnNIb3N0cyI6IHt9LAogICAgIkRpcmVjdFNpdGVzIjogW10sCiAgICAiRGlyZWN0SXAiOiBbXSwKICAgICJQcm94eVNpdGVzIjogW10sCiAgICAiUHJveHlJcCI6IFtdLAogICAgIkJsb2NrU2l0ZXMiOiBbXSwKICAgICJCbG9ja0lwIjogW10sCiAgICAiRG9tYWluU3RyYXRlZ3kiOiAiQXNJcyIKfQ==
```

**Example subscription body:**

```
happ://routing/onadd/ewogICAgIk5hbWUiOiAidGVzdCIsCiAgICAiR2xvYmFsUHJveHkiOiAidHJ1ZSIsCiAgICAiUmVtb3RlRG5zIjogIiIsCiAgICAiRG9tZXN0aWNEbnMiOiAiIiwKICAgICJHZW9pcHVybCI6ICIiLAogICAgIkdlb3NpdGV1cmwiOiAiIiwKICAgICJEbnNIb3N0cyI6IHt9LAogICAgIkRpcmVjdFNpdGVzIjogW10sCiAgICAiRGlyZWN0SXAiOiBbXSwKICAgICJQcm94eVNpdGVzIjogW10sCiAgICAiUHJveHlJcCI6IFtdLAogICAgIkJsb2NrU2l0ZXMiOiBbXSwKICAgICJCbG9ja0lwIjogW10sCiAgICAiRG9tYWluU3RyYXRlZ3kiOiAiQXNJcyIKfQ==
vmess://eyJob3N0IjoiZ3Vhdmypc3RhbmJ1bC5jb20iLCJwYXRoIjoiXC8xUyIsInRscyI6InRscyIsImFkZCI6Ind3dy5ndWF2ZWlzdGFuYnVsLmNvbSIsInBvcnQiOjQ0MywiYWlkIjowLCJuZXQiOiJ3cyIsInR5cGUiOiJub25lIiwiZnAiOiJjaHJvbWUiLCJhbHBuIjoiaHR0cFwvMS4xIiwibm9kZV9zc19wdWJsaWNrZXkiOiIiLCIiOmZhbHNlLCJ2IjoiMiIsInBzIjoiXHVkODNjXHVkZGU5XHVkODNjXHVkZGVhIDRHIC0gR2VybWFueSAtIDAxIiwiaWQiOiI4YjhkYWI4NC03OGEzLTNhMWItYTE1NS03M2FkNDk1ZTY0NmUifQ==
vless://70cc43c5-b2f4-34ac-a092-d806984a6b8c@1.13.7.91:443?encryption=none&security=reality&pbk=qGPTy8EZokn3hWp6hKBQ0MVvEuLRJCcv5UdWeP4TVhI&headerType=none&fp=chrome&type=tcp&flow=xtls-rprx-vision&sni=booking.com&sid=6ba85179e30d4fc2#%F0%9F%87%B1%F0%9F%87%B9%20Test
```

