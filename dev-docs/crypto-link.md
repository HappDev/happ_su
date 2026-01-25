# 加密链接

该应用程序支持加密链接。链接可以使用 RSA-4096 进行加密。 ~~建议仅使用 RSA-4096，其协议名称为 `happ://crypt4/`。~~ 现已推出新型加密方式 `happ://crypt5/`。

链接加密旨在向用户隐藏订阅地址。添加加密订阅后，用户将无法编辑、查看或分享该订阅中包含的服务器配置。加密密钥本身已安全地嵌入在应用程序中，确保了订阅数据的安全性。

您可以通过以下两种方式加密链接：

1. 使用 [网页端](https://crypto.happ.su/)。
2. 通过 [API](https://www.google.com/search?q=%23api-%E8%AF%B4%E6%98%8E)。

**API 说明**

如需使用 API，请向以下地址发送请求：

[https://crypto.happ.su/api-v2.php](https://crypto.happ.su/api-v2.php)

示例：

```bash
curl -X POST -H "Content-Type: application/json" -d '{"url":"https://your-url.com"}' "https://crypto.happ.su/api-v2.php"
```

请求将返回您链接的加密版本，该版本可直接在应用程序中使用。

**RSA 密钥（已弃用）**

如果您倾向于自行加密链接，请使用下方提供的 RSA 密钥。注意：此方法已过时，不建议使用！

RSA 密钥 (RSA-4096):

```
-----BEGIN PUBLIC KEY-----
MIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEAlBetA0wjbaj+h7oJ/d/h
pNrXvAcuhOdFGEFcfCxSWyLzWk4SAQ05gtaEGZyetTax2uqagi9HT6lapUSUe2S8
nMLJf5K+LEs9TYrhhBdx/B0BGahA+lPJa7nUwp7WfUmSF4hir+xka5ApHjzkAQn6
cdG6FKtSPgq1rYRPd1jRf2maEHwiP/e/jqdXLPP0SFBjWTMt/joUDgE7v/IGGB0L
Q7mGPAlgmxwUHVqP4bJnZ//5sNLxWMjtYHOYjaV+lixNSfhFM3MdBndjpkmgSfmg
D5uYQYDL29TDk6Eu+xetUEqry8ySPjUbNWdDXCglQWMxDGjaqYXMWgxBA1UKjUBW
wbgr5yKTJ7mTqhlYEC9D5V/LOnKd6pTSvaMxkHXwk8hBWvUNWAxzAf5JZ7EVE3jt
0j682+/hnmL/hymUE44yMG1gCcWvSpB3BTlKoMnl4yrTakmdkbASeFRkN3iMRewa
IenvMhzJh1fq7xwX94otdd5eLB2vRFavrnhOcN2JJAkKTnx9dwQwFpGEkg+8U613
+Tfm/f82l56fFeoFN98dD2mUFLFZoeJ5CG81ZeXrH83niI0joX7rtoAZIPWzq3Y1
Zb/Zq+kK2hSIhphY172Uvs8X2Qp2ac9UoTPM71tURsA9IvPNvUwSIo/aKlX5KE3I
VE0tje7twWXL5Gb1sfcXRzsCAwEAAQ==
-----END PUBLIC KEY-----
```
