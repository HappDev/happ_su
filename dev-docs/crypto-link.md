# 加密链接

应用支持加密链接。链接可以使用 **RSA-4096** 加密。现在推荐只使用 RSA-4096，它被称为 `happ://crypt3/`。\
加密链接的目的是隐藏用户的订阅地址。添加加密订阅后，用户无法编辑、查看或分享订阅中包含的服务器配置。加密密钥本身被安全地内置在应用中，从而确保订阅数据的保护。。

您可以通过以下三种方式加密链接：

* 使用本[网页](https://crypto.happ.su/)
* 使用 [API](https://www.happ.su/main/ru/documentation/crypto-link#instrukciya-po-api)
* 使用 [RSA](crypto-link.md#rsa-mi-yao) 密钥

#### API 使用说明

要使用 API，您需要发送请求至以下地址：\
[https://crypto.happ.su/api.php](https://crypto.happ.su/api.php)

示例：

```bash
curl -X POST -H "Content-Type: application/json" -d '{"url":"https://your_url.com"}' "https://crypto.happ.su/api.php"
```

结果将返回您链接的加密版本，可以在应用中使用。

#### RSA 密钥

如果您希望自行加密链接，请使用下面提供的 RSA 密钥。

**RSA 密钥 (RSA-4096)：**

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

使用这些密钥，您可以通过首选的 RSA 加密工具加密链接。
