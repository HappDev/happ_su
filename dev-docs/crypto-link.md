# Зашифрованная ссылка

Приложение поддерживает зашифрованные ссылки. Ссылка может быть зашифрована с использованием RSA-4096.  ~~Рекомендуется использовать только RSA-4096 он называется happ://crypt4/.~~ Доступен новый тип шифрования happ://crypt5/.

Шифрование ссылок предназначено для скрытия адреса подписки от пользователя. После добавления зашифрованной подписки пользователь не может редактировать, просматривать или делиться конфигурациями серверов, содержащимися в подписке. Сами ключи шифрования надежно встроены в приложение, что обеспечивает защиту данных подписки.

Вы можете зашифровать ссылку двумя способами:

1. С использованием [веб-страницы](https://crypto.happ.su).
2. Через [API](crypto-link.md#instrukciya-po-api).

#### **Инструкция по API**

Для использования API необходимо отправить запрос по следующему адресу:\
[https://crypto.happ.su/api-v2.php](https://crypto.happ.su/api-v2.php)

**Пример:**

```bash
curl -X POST -H "Content-Type: application/json" -d '{"url":"https://your-url.com"}' "https://crypto.happ.su/api-v2.php"
```

В результате будет возвращена зашифрованная версия вашей ссылки, которую можно использовать в приложении.

#### **RSA-ключ (устарело)**

Если вы предпочитаете зашифровать ссылку самостоятельно, используйте предоставленный RSA-ключ ниже. Внимание данный способ устарел и не рекомендуется к использованию!

**RSA-ключ (RSA-4096):**

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
