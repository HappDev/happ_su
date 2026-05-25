---
description: Управляйте настройками приложения через подписку
---

# Управление приложением

**Функционал управления приложением** включает два направления:

* [Стандартные параметры](app-management.md#standartnye-parametry) управления, которые работают для большинства панелей.
* [Расширенные параметры](app-management.md#id-rasshirennyifunkcional-opisanieparametrov) для которых, необходимо указывать [Provider ID](provider-id.md) в подписке.

Чтобы активировать параметр, передайте значение `true` или `1` ; чтобы отключить — любое другое непустое значение (например, `0` или `false`).

## Стандартные параметры

<details>

<summary>Автообновление подписки</summary>

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

В системе создаётся задача на выполнение операции с заданным интервалом. В зависимости от внутренних приоритетов система старается запустить обновление подписки в установленное время.\
Если по какой-либо причине обновление не было выполнено в пределах указанного интервала, оно произойдёт автоматически при следующем запуске приложения.\
Интервал задаётся в часах и должен быть кратен одному часу.

**Пример настройки данного параметра:**

```
profile-update-interval: [int]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-update-interval: 1
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#profile-update-interval: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Имя подписки</summary>

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

Название профиля подписки. Может быть передано как plain text или в base64 (UTF-8). **Ограничение**: Максимальная длина — 25 символов.

Через тело подписки, указав перед параметром знак # (например #profile-title)

**Пример настройки данного параметра:**

```
profile-title: [string]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-title: Name VPN
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#profile-title: Name VPN
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Строка состояния подписки (трафик, дата истечения)</summary>

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

Отображается информация о балансе, объёме использованного трафика и сроке действия подписки.\
В приложении в левой части шкалы показано количество израсходованного трафика (upload + download), а в правой — общий объём (total) после символа «/».\
Дата окончания подписки указывается в параметре **expire**.\
**Примечание:** все данные передаются в одном заголовке и разделяются символом **;**. 

**Пример настройки данного параметра:**

```
subscription-userinfo: [string]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-userinfo: upload=0; download=2153701362; total=0; expire=1790951622
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#subscription-userinfo: upload=0; download=2153701362; total=0; expire=1790951622
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Ссылка на страницу поддержки</summary>

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

Кнопка для перехода на страницу поддержки.\
Отображается в виде синей иконки, расположенной в правой части строки.\
Если ссылка ведёт в Telegram, отображается иконка Telegram; в остальных случаях используется стандартная иконка ссылки.

**Пример настройки данного параметра:**

```
support-url: [string]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
support-url: https://t.me/happ_chat
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#support-url: https://t.me/happ_chat
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Ссылка на страницу сайта</summary>

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

Кнопка для перехода на страницу сайта подписки.\
Отображается в виде синей иконки, расположенной в левой части строки.\
Если параметр не задан, иконка будет серого цвета

**Пример настройки данного параметра:**

```
profile-web-page-url: [string]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-web-page-url: https://happ.su
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#profile-web-page-url: https://happ.su
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Объявление</summary>

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

Подписка может содержать текст объявления, передаваемый в формате **plain text** или **Base64**.\
**Ограничение:** максимальная длина отображаемого текста — **200 символов**.

**Пример настройки данного параметра:**

```
announce: [string]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
announce: base64:SGFwcCB0aGUgYmVzdCE=
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#announce: base64:SGFwcCB0aGUgYmVzdCE=
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Отключение маршрутизации</summary>

Глобальный параметр для отключения маршрутизации в приложении.

**Пример настройки данного параметра:**

```
routing-enable: [string]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
routing-enable: 0
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#routing-enable: 0
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Конфигурация туннеля (только для Desktop)</summary>

Передавайте собственную конфигурацию туннеля для ядра sing-box

**Пример настройки данного параметра:**

```
custom-tunnel-config: [json]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
custom-tunnel-config: {...}
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#custom-tunnel-config: {...}
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Авторизация SOCKS Inbound</summary>

Определяет режим работы и учетные данные для локального SOCKS-прокси.\

* **auto** — автоматическая генерация и подставление данных в конфиги и тунель.
* **manual** — использование заданных в настройках user и password.
* **from-json** — брать настройки из JSON-конфигурации. Для URL config ов работает как режим auto в данном выборе.
* **disable** — отключить авторизацию.

**Параметры:**
```
socks-auth-mode: [auto, manual, from-json, disable]
socks-auth-user: [String] — логин (для режима manual).
socks-auth-password: [String] — пароль (для режима manual).
```

**Пример настройки:**

```
socks-auth-mode: manual
socks-auth-user: myuser
socks-auth-password: mypassword
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
socks-auth-mode: manual
socks-auth-user: myuser
socks-auth-password: mypassword
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#socks-auth-mode: manual
#socks-auth-user: myuser
#socks-auth-password: mypassword
```
{% endcode %}

</details>

<details>

<summary>Авторизация HTTP Inbound</summary>

Определяет режим работы и учетные данные для локального HTTP-прокси.\

* **auto** — автоматическая генерация и подставление данных в конфиги и тунель.
* **manual** — использование заданных в настройках user и password.
* **from-json** — брать настройки из JSON-конфигурации. Для URL config ов работает как режим auto в данном выборе.
* **disable** — отключить авторизацию.

**Параметры:**
```
http-auth-mode: [auto, manual, from-json, disable]
http-auth-user: [String] — логин (для режима manual).
http-auth-password: [String] — пароль (для режима manual).
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
http-auth-mode: manual
http-auth-user: user1
http-auth-password: pass1
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#http-auth-mode: manual
#http-auth-user: user1
#http-auth-password: pass1
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

## Расширенные параметры <a href="#id-rasshirennyifunkcional-opisanieparametrov" id="id-rasshirennyifunkcional-opisanieparametrov"></a>

{% hint style="warning" %}
Необходим параметр [Provider ID](provider-id.md)!
{% endhint %}

<details>

<summary>Смена URL подписки</summary>

Если домен заблокирован вашим провайдером, а пользователи могут подключаться к серверам и обновлять подписку только через VPN, этот параметр именно для вас. Задав новое доменное имя в значении данного параметра, вы обеспечите его автоматическую замену у всех пользователей подписки.

**Пример настройки данного параметра:**

```
new-url: [url]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
new-url: https://mynew-domain.com/3J3jrb4jfc
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#new-url: https://mynew-domain.com/3J3jrb4jfc
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Смена домена подписки</summary>

Изменение домена сайта без смены полного URL, сохраняя остальную часть адреса.

**Пример настройки данного параметра:**

```
new-domain: [domain]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
new-domain: mynew-domain.com
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#new-domain: mynew-domain.com
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Fallback URL (запасной URL для подписки)</summary>

<figure><img src="../.gitbook/assets/telegram-cloud-photo-size-2-5260524142723798836-w.jpg" alt="" width="375"><figcaption></figcaption></figure>

Если основной URL недоступен, вернул ошибку 300–599 или не ответил в течение 9 секунд, приложение переключится на Fallback URL (при его наличии).

**Пример настройки данного параметра:**

```
fallback-url: [url]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
fallback-url: https://mynew-domain.com/3J3jrb4jfc
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#fallback-url: https://mynew-domain.com/3J3jrb4jfc
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Описание сервера в подписке</summary>

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

Позволяет задать дополнительную подпись, которая отображается под названием сервера вместо стандартного текста (например, "VMess", "VLESS", "Trojan").

* Максимальная длина — 30 символов.
* Если не помещается на экран, будет сокращена с троеточием.
* Задаётся после `title` через разделитель `?`.

**Примеры:**

{% code title="VLESS" %}
```
vless://1fb46fdc-e3e4-35d1-bd46-605d773b5762@5.5.8.9:443?encryption=none&node_id=482&headerType=none&type=tcp&security=reality&sni=booking.com&fp=chrome&pbk=YqHW8a4iAc1SZYpTrFVoOQg1F3yAdX1tWXuROZUCsEU&sid=6ba85179e30d4fc2&flow=xtls-rprx-vision&xtls=2#title?serverDescription=SGFwcCB0aGUgYmVzdA==
```
{% endcode %}

{% code title="VMESS" %}
```
vmess://eyJob3N0IjoiZWxhaG9tZWtpdGNoZW4uY29tIiwicGF0aCI6IiIsInRscyI6IiIsImFkZCI6ImVsYWhvbWVraXRjaGVuLmNvbSIsInBvcnQiOjUwMDAsImFpZCI6MCwibmV0IjoidGNwIiwidHlwZSI6Im5vbmUiLCJ2IjoiMiIsInBzIjoi4piB77iPIDogNTMuM0dCIiwiaWQiOiI4N2ZhN2VmMC1jM2ZjLTNiOTAtYTJkOC01OGZjYjhkZmZmMjYiLCJzZXJ2ZXJEZXNjcmlwdGlvbiI6IkhhcHAgdGhlIGJlc3QifQ==
```
{% endcode %}

{% code title="Trojan" %}
```
trojan://8GXLP3dEzm7T8wP5Jx0Ufg@199.107.164.105:443?security=tls&insecure=1&fragment=3,1,tlshello&type=ws&headerType=&path=%2F&host=quictest.burncommunity.ru&sni=quictest.burncommunity.ru&fp=chrome&alpn=http%2F1.1#title?serverDescription=SGFwcCB0aGUgYmVzdA==
```
{% endcode %}

{% code title="Socks5" %}
```
socks://pkg-private2-country-us-city-new_york_city:w0e20i55uuq6pxqg@quality.proxywing.com:1080#title?serverDescription=SGFwcCB0aGUgYmVzdA==
```
{% endcode %}

{% code title="Shadowsocks" %}
```
ss://YWVzLTI1Ni1jZmI6UzdLd1V1N3lCeTU4UzNHYQ==@80.92.204.106:9042#title?serverDescription=SGFwcCB0aGUgYmVzdA==
```
{% endcode %}

{% code title="Wireguard" %}
```
wireguard://password2key@123.123.123.2:10803?publickey=asd33d223d33&address=dom.ru&allowinsecure=1&mtu=1500&reserved=1,22,33#title?serverDescription=SGFwcCB0aGUgYmVzdA==
```
{% endcode %}

{% code title="JSON" %}
```
{
  "dns": {
  ...
  },
  "inbounds": [
  ...
  ],
  "outbounds": [
  ...
  ],
  "remarks": "🇭🇰 Hong Kong",
  "meta": {
    "serverDescription": "Happ the best"
  }
}
```
{% endcode %}

</details>

<details>

<summary>Расширенные объявления</summary>

<div><figure><img src="../.gitbook/assets/3588.png" alt="" width="188"><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/3584.png" alt="" width="188"><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/3585.png" alt="" width="188"><figcaption></figcaption></figure></div>

Более заметные объявления. Делятся на два типа: произвольный информационный текст (`sub-info`) и системное уведомление об окончании подписки (`sub-expire`).

Уведомления об истечении подписки имеют приоритет и отображаются автоматически за 3 дня до окончания или после истечения. Информационный блок показывается только при отсутствии активного expire-сообщения.

Оба механизма можно явно отключить через http headers. Если параметры были переданы и не отменены, они остаются активными до удаления подписки.

| META PARAM KEY              | TYPE     | REQUIRED | LIMITS / VALUES                  | DESCRIPTION |
|----------------------------|----------|----------|----------------------------------|-------------|
| sub-info-color             | String   | No       | red, blue, green (default blue)  | Цвет информационного блока |
| sub-info-text              | String   | Yes*     | max 200 chars                    | Основной текст инфо-блока. Без параметра блок не отображается. Или если в параметр отправили 0. Пустая строка отключает отображение |
| sub-info-button-text       | String   | No       | max 25 chars                     | Текст кнопки. Если отсутствует — кнопка не показывается |
| sub-info-button-link       | String   | No       | any string (URL / deeplink)      | Ссылка кнопки. Открывается в браузере, без валидации |
| sub-expire                 | Boolean  | No       | true \| 1 = enabled              | Включает механизм показа информации об истечении подписки |
| sub-expire-button-link     | String   | No       | any string (URL / deeplink)      | Ссылка на кнопку «Продлить». Без ссылки кнопка не показывается |

#### Логика отображения (summary)

| CONDITION | RESULT |
|----------|--------|
| sub-expire = true и подписка истекает ≤ 3 дней | Показываем сообщение «Ваша подписка заканчивается через N д.» |
| sub-expire = true и подписка истекла | Показываем сообщение «Подписка закончилась!» |
| sub-expire = true и дней > 3 | Сообщение об истечении скрывается |
| Нет даты истечения | Информация об истечении не отображается |
| Есть активное expire-сообщение | sub-info блок не показывается |
| Нет expire-сообщения и есть sub-info-text | Показываем sub-info блок |
| sub-info-text = 0 | sub-info блок отключается |
| sub-expire ≠ true \| 1 | Механизм expire отключается |

#### Примечания

| NOTE |
|------|
| Параметры применяются только к той подписке, для которой они были переданы |
| Если параметры пришли через push и не были явно отключены, они остаются активными бессрочно |
| Кнопка expire всегда имеет текст «Продлить» |
| Количество дней (N) считается как полные дни, максимум 3 |

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
sub-expire: 1
sub-expire-button-link: https://t.me/generate
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#sub-expire: 1
#sub-expire-button-link: https://t.me/generate
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Фрагментация и фронтинг подписки</summary>

Некоторые CDN поддерживают фронтинг доменов. Это позволяет подключаться к своему сайту через сторонний домен.

Например, указав адрес подключения `visa.com`, а в заголовке Host — `my-domain.com`, провайдер увидит только запрос к `visa.com`.

Также вы можете обращаться к своему домену за списком серверов, используя фрагментацию пакетов в SNI TLSHello.

По умолчанию фрагментация включена для всех подписок.

#### &#x20;Схема URL c параметрами

```
[link]#title?[fragment]&[resolve-address]&[host]&[insecure]

Fronting:
visa.com/123#MyVPN?resolve-address=visa.com&host=mydomain.com

Fragmentation:
mydomain.com/123#MyVPN?fragment=80-250,10-100,tlshello
```

Фрагментация содержит три параметра: `[length]`, `[interval]` и `[packets]`.

При использовании фронтинга необходимо сначала указать URL с доменом, через который будет осуществляться соединение. Также требуется задать `resolve-address` — это может быть домен или IP-адрес — и `host`, соответствующий вашему хосту в сети выбранного провайдера.

</details>

<details>

<summary>No Limit Mode</summary>

Режим No Limit Mode может быть использован для всех типов протоколов или только для xhttp. Увеличивает лимит оперативной памяти для xray-core, повышая стабильность и производительность.

> Важно: Функция находится в стадии бета-тестирования. Используйте только один из вариантов активации (для всех или только для xhttp) — одновременное включение недопустимо.

**Пример настройки данного параметра:**

```
no-limit-enabled: [true / 1]
no-limit-xhttp-enabled: [true / 1]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
no-limit-xhttp-enabled: 1
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#no-limit-xhttp-enabled: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Advanced fragmentation</summary>

Данная функция пока что проходит закрытое тестирование и скоро будет доступна...

</details>

<details>

<summary>Неотключаемый HWID</summary>

По умолчанию HWID включен на всех приложениях Happ. Но если вы хотите, чтобы пользователь не мог отключить пересылку этого параметра отключив его в настройках приложения, то вы можете отправить вместе с подпиской специальный параметр.

**Пример настройки данного параметра:**

```
subscription-always-hwid-enable: [true / 1]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-always-hwid-enable: 1
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#subscription-always-hwid-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Уведомление об окончании подписки</summary>

Вы можете включить функцию автоматических уведомлений о завершении подписки.\
Пользователь будет получать напоминания за 3 дня до окончания подписки: приложение отправит по одному уведомлению в день в течение трёх дней. Это поможет пользователю не забыть продлить подписку вовремя.

Текст уведомления:

```
У вашей подписки [name] скоро истечёт срок действия, не забудьте продлить её.
```

**Пример настройки данного параметра:**

```
notification-subs-expire: [true / 1]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
notification-subs-expire: 1
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#notification-subs-expire: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Скрыть настройки серверов в подписке</summary>

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Отключите возможность просмотра и редактирования конфигураций серверов для пользователей вашей подписки. Настройка применяется как к уже добавленным подпискам, так и к тем, что будут добавлены в будущем.

**Пример настройки данного параметра:**

```
hide-settings: [true / 1]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
hide-settings: 1
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#hide-settings: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Резолвинг доменов</summary>

Приложение может выполнять предварительный резолвинг доменов серверов ещё до установления подключения.\
Вы можете указать любой DoH-сервер, и при соединении с сервером Xray доменное имя будет заменено на полученный IP-адрес.

Если для домена возвращается несколько IP-адресов, приложение автоматически выберет тот, у которого минимальное время отклика (ping).\
Однако стоит учитывать: при большом количестве IP-адресов подключение может занять больше времени, так как все варианты будут протестированы заранее.

**Пример настройки данного параметра:**

```
server-address-resolve-enable: [true / 1]
server-address-resolve-dns-domain: [url]
server-address-resolve-dns-ip: [ip]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
server-address-resolve-enable: 1
server-address-resolve-dns-domain: https://common.dot.dns.yandex.net/dns-query
server-address-resolve-dns-ip: 77.88.8.8
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#server-address-resolve-enable: 1
#server-address-resolve-dns-domain: https://common.dot.dns.yandex.net/dns-query
#server-address-resolve-dns-ip: 77.88.8.8
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

## Управление настройками приложения <a href="#upravlenie-nastroikami-prilozheniya" id="upravlenie-nastroikami-prilozheniya"></a>

{% hint style="warning" %}
Необходим параметр [Provider ID](provider-id.md)!
{% endhint %}

<details>

<summary>Автоподключение</summary>

Позволяет автоматически подключать пользователя к серверам при запуске приложения.\
Дополнительно, с помощью параметра **subscription-autoconnect-type** можно указать критерий для подключения к определенному серверу.

**Пример настройки данного параметра:**

```
subscription-autoconnect: [true / 1]
subscription-autoconnect-type: [lastused/lowestdelay/random]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-autoconnect: 1
subscription-autoconnect-type: lowestdelay
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#subscription-autoconnect: 1
#subscription-autoconnect-type: lastused
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Автопинг</summary>

Запускайте автоматическое тестирование списка серверов при открытии приложения если это необходимо.

**Пример настройки данного параметра:**

```
subscription-ping-onopen-enabled: [true / 1]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-ping-onopen-enabled: 1
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#subscription-ping-onopen-enabled: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Автообновление подписок</summary>

В приложении можно включать или отключать автообновление сразу для всех подписок — эта настройка применяется ко всем подпискам одновременно. Если же нужно задать автообновление только для конкретной подписки, воспользуйтесь функционалом Автообновление подписки. При отключении глобальной настройки каждая подписка самостоятельно определяет своё время обновления.

**Пример настройки данного параметра:**

```
subscription-auto-update-enable: [true / 1] 
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-auto-update-enable: 1
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#subscription-auto-update-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Фрагментация и шумы</summary>

Это глобальный параметр управления фрагментацией для всех подписок. Если же нужно назначить фрагментацию только для конкретной подписки или серверу, воспользуйтесь бесплатным функционалом и инструкциями общей документации к приложению. При отключении глобальной настройки каждая подписка самостоятельно определяет настройки фрагментации.

**Пример настройки данного параметра:**

```
fragmentation-enable: [true / 1]
fragmentation-packets: [tlshello,1-2,1-3,1-5]
fragmentation-length: [50-100]
fragmentation-interval: [10-20]
fragmentation-maxsplit: [String]
noises-enable: [true / 1] — включение/выключение шумов.
noises-packet-type: [array, str, hex, base64] — тип передаваемых данных (по умолчанию array).
noises-packet: [String] — фиксированные данные для шума. Список строк, разделенных запятой.
noises-delay: [String] — задержка между отправкой шумовых сигналов в миллисекундах.
noises-rand: [String] — добавляет случайные байты или задает их длину (например, "1-8192").
noises-rand-range: [String] — диапазон значений случайных байтов (по умолчанию "0-255").
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
fragmentation-enable: 1
fragmentation-packets: tlshello
fragmentation-length: 50-100
fragmentation-interval: 5
fragmentation-maxsplit: 100-200
noises-enable: true
noises-packet-type: base64
noises-packet: 7nQBAAABAAAAAAAABnQtcmluZwZtc2VkZ2UDbmV0AAABAAE=
noises-delay: 50
noises-rand: 1-1024
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#fragmentation-enable: 1
#fragmentation-packets: tlshello
#fragmentation-length: 50-100
#fragmentation-interval: 5
#fragmentation-maxsplit: 100-200
#noises-enable: true
#noises-packet-type: base64
#noises-packet: 7nQBAAABAAAAAAAABnQtcmluZwZtc2VkZ2UDbmV0AAABAAE=
#noises-delay: 50
#noises-rand: 1-1024
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Пинг</summary>

Эта функция позволяет выбрать способ выполнения пинга в приложении.\
Доступны четыре варианта:
* **via Proxy - GET**
* **via Proxy - HEAD**
* **TCP**
* **ICMP**
Для режима «via Proxy» можно дополнительно указать URL для проверки пинга.

**Пример настройки данного параметра:**

```
ping-type: [proxy, proxy-head, tcp, icmp]
check-url-via-proxy: [url]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
ping-type: proxy
check-url-via-proxy: https://cp.cloudflare.com/generate_204
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#ping-type: proxy
#check-url-via-proxy: https://cp.cloudflare.com/generate_204
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>User-Agent</summary>

Эта функция позволяет изменить User-Agent, используемый в заголовках при получении подписки. Полезно в случаях, когда провайдер блокирует запросы с нестандартными или неподходящими заголовками.

**Пример настройки данного параметра:**

```
change-user-agent: [String] 
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
change-user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/135.0.0.0 Safari/537.36
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#change-user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/135.0.0.0 Safari/537.36
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Автозапуск приложения</summary>

Эта функция позволяет автоматически запускать приложение при включении устройства. В настоящее время доступна только на Android.&#x20;

**Пример настройки данного параметра:**

```
app-auto-start: [String] 
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
app-auto-start: 1
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#app-auto-start: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Обновление подписки при запуске приложения</summary>

Эта функция автоматически обновляет все подписки в приложении при каждом открытии приложения.

**Пример настройки данного параметра:**

```
subscription-auto-update-open-enable: [String] 
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscription-auto-update-open-enable: 1
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#subscription-auto-update-open-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Прокси для выбранных приложений (Android)</summary>

В этом параметре можно указать список приложений, которые должны использовать VPN или, наоборот, обходить его. Если приложение ещё не установлено на устройстве, но указано в списке, оно будет автоматически учтено при первом подключении к VPN после установки.

**Пример настройки данного параметра:**

```
per-app-proxy-mode: [off/on/bypass] \\Укажите один из трех параметров
per-app-proxy-list: [com.google.chrome,com.meta.instagram] \\список appID через ','
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
per-app-proxy-mode: on
per-app-proxy-list: com.google.chrome,com.meta.instagram
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#per-app-proxy-mode: on
#per-app-proxy-list: com.google.chrome,com.meta.instagram
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Прокси для выбранных приложений Invert (Android)</summary>

В этом параметре можно указать список приложений, которые должны использовать VPN или, наоборот, обходить его.\
**Выделяет все приложения кроме указанных в списке.**

**Пример настройки данного параметра:**

```
per-app-proxy-mode: [off/on/bypass] \\Укажите один из трех параметров
per-app-proxy-list-invert: [com.google.chrome,com.meta.instagram] \\список appID через ','
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
per-app-proxy-mode: on
per-app-proxy-list-invert: com.google.chrome,com.meta.instagram
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#per-app-proxy-mode: on
#per-app-proxy-list-invert: com.google.chrome,com.meta.instagram
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Прокси для выбранных приложений Set (Android)</summary>

В этом параметре можно указать список приложений, которые должны использовать VPN или, наоборот, обходить его.\
**Очищаем все выбранные, и только потом выделяем приложения по указанному списку**

**Пример настройки данного параметра:**

```
per-app-proxy-mode: [off/on/bypass] \\Укажите один из трех параметров
per-app-proxy-list-set: [com.google.chrome,com.meta.instagram] \\список appID через ','
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
per-app-proxy-mode: on
per-app-proxy-list-set: com.google.chrome,com.meta.instagram
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#per-app-proxy-mode: on
#per-app-proxy-list-set: com.google.chrome,com.meta.instagram
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Анализ пакетов (Sniffing)</summary>

В **xray-core** sniffing нужен, чтобы анализировать первые пакеты соединения и автоматически определять **протокол** (HTTP, TLS, BitTorrent и т.д.) и **домен** (SNI/Host).\
Может влиять на загрузку медиа в приложении WeChat. По умолчанию включен.<br>

**Пример настройки данного параметра:**

```
sniffing-enable: [String] 
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
sniffing-enable: 1
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#sniffing-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Запрет сворачивания подписок</summary>

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

Эта функция отключает возможность сворачивать подписку: список серверов всегда отображается полностью, в развёрнутом виде.<br>

**Пример настройки данного параметра:**

```
subscriptions-collapse: [false / 0]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscriptions-collapse: 0
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#subscriptions-collapse: 0
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Принудительное разворачивание подписки</summary>

При получении данного параметра через обновление подписки приложение принудительно развернет её, если она свернута. Значение `false` игнорируется: параметр служит только для разворачивания, свернуть подписку с его помощью нельзя.

**Пример настройки данного параметра:**

```
subscriptions-expand-now: [true / 1]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
subscriptions-expand-now: 1
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#subscriptions-expand-now: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Режим отображения пинга</summary>

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

Позволяет отобразить иконки вместо временных значений<br>

**Пример настройки данного параметра:**

```
ping-result: [time,icon]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
ping-result: icon
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#ping-result: icon
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Mux</summary>

Mux в xray-core — это функция мультиплексирования (multiplexing), которая позволяет передавать данные нескольких виртуальных TCP-соединений через одно физическое TCP-соединение. Она предназначена для снижения задержек от TCP-handshake, но не для повышения пропускной способности (может даже замедлить большие загрузки). Настраивается в outbound-конфигурации с параметрами вроде enabled и concurrency (min -1 max 1024).

**Пример настройки данного параметра:**

```
mux-enable: [true / 1]
mux-tcp-connections: [String]
mux-xudp-connections: [String]
mux-quic: [String]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
mux-enable: 1
mux-tcp-connections: 100
mux-xudp-connections: 200
mux-quic: skip
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#mux-enable: 1
#mux-tcp-connections: 100
#mux-xudp-connections: 200
#mux-quic: skip
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Режим Proxy \ TUN (только для Desktop)</summary>

Необходимо <mark style="color:$warning;">**использовать только один**</mark> из двух перечисленных параметров! Эти параметры определяют тип подключения при добавлении\обновлении подписки.

**Пример настройки данного параметра:**

```
proxy-enable: [true / 1]
tun-enable: [true / 1]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
proxy-enable: 1
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#proxy-enable: 1
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Режим TUN (только для Desktop)</summary>

Определяет какой режим будет использоваться для TUN подключения.

* **`system`** — использует системный сетевой стек ОС.\
  Быстро и эффективно, но зависит от корректной настройки маршрутов и файрвола.
* **`gvisor`** — пользовательский стек gVisor (userspace).\
  Меньше зависимостей от правил ядра и конфликтов с iptables/nftables/Docker, лучше изоляция; возможен небольшой минус к производительности.

**Пример настройки данного параметра:**

```
tun-mode: [system,gvisor]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
tun-mode: gvisor
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#tun-mode: gvisor
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Выбор ядра туннеля (только для Desktop)</summary>

Определяет какое ядро будет использоваться для TUN подключения. Для выбора доступно\

* [sing-box](https://github.com/SagerNet/sing-box)
* [tun2proxy](https://github.com/tun2proxy/tun2proxy)
* default(Happ TUN) наша реализация туннеля 

**Пример настройки данного параметра:**

```
tun-type: [singbox, tun2proxy, default]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
tun-type: tun2proxy
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#tun-type: tun2proxy
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Exclude Routes</summary>

Определяет перечень подсетей и IP-адресов, трафик которых не должен проходить через туннель.\
Адреса указываются в одной строке, разделяя их пробелами и запятыми.

**Пример настройки данного параметра:**

```
exclude-routes: [String]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
exclude-routes: 192.168.1.0/24, 10.0.0.0/8
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#exclude-routes: 192.169.1.0/24, 10.0.0.0/8
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Exclude Routes Set</summary>

Определяет перечень подсетей и IP-адресов, трафик которых не должен проходить через туннель.\
Адреса указываются в одной строке, разделяя их пробелами и запятыми.\
**Перед установкой текущий список очищается.**

**Пример настройки данного параметра:**

```
exclude-routes-set: [String]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
exclude-routes-set: 192.169.1.0/24, 10.0.0.0/8
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#exclude-routes-set: 192.169.1.0/24, 10.0.0.0/8
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Темы (только iOS)</summary>

<figure><img src="../.gitbook/assets/222223.png" alt="" width="375"><figcaption></figcaption></figure>

Позволяет изменить цветовую тему на персональную. Собственную тему можно создать в редакторе — удерживайте надпись «Тема оформления» для вызова меню. Созданную тему можно экспортировать в буфер обмена, а также импортировать из буфера, из файла .happ или передать через подписку.&#x20;

{% code title="VIOLET Theme" overflow="wrap" expandable="true" %}
```json
{
  "backgroundGradientRotationAngle" : 37.1,
  "serverRowBackgroundColor" : "#21003D67",
  "subsHeaderColor" : "#42296DFF",
  "profileWebPageIconColor" : "#A2B8FFFF",
  "selectedServerRowColor" : "#3E2F62B5",
  "disclosureSubHeaderTextColor" : "#C1C2E2FF",
  "buttonTextColor" : "#FFFFFFFF",
  "buttonTimerColor" : "#FFFFFFFF",
  "subscriptionInfoBackgroundColor" : "#21003CFF",
  "backgroundColors" : [
    "#3D2A7DFF",
    "#6557BAFF",
    "#9377FF7F"
  ],
  "disclosureHeaderTextColor" : "#FFFFFFFF",
  "backgroundGradientColorIntensity" : 1,
  "additionalOptionsButtonColor" : "#FFFFFFFF",
  "buttonImageType" : "light",
  "serverRowSubTitleTextColor" : "#C1C2E2FF",
  "supportIconColor" : "#FFFFFFFF",
  "topBarButtonsColor" : "#FFFFFFFF",
  "subscriptionTrafficBackgroundColor" : "#533EA7FF",
  "subHeaderButtonColor" : "#FFFFFFFF",
  "buttonColor" : "#9377FFFF",
  "powerIconColor" : "#3D2A7DFF",
  "subscriptionInfoTextColor" : "#FFFFFFFF",
  "serverRowTitleTextColor" : "#FFFFFFFF",
  "backgroundImageType" : "system",
  "elipseColors" : [
    "#00B460FF",
    "#CF72FFE0",
    "#FFDD00FF"
  ],
  "serverRowChevronColor" : "#FFFFFFFF"
}
```
{% endcode %}

{% code title="Turquoise Theme" overflow="wrap" expandable="true" %}
```json
{
  "backgroundGradientRotationAngle" : 39.21265661716461,
  "serverRowChevronColor" : "#F3FFFDFF",
  "buttonImageType" : "light",
  "buttonTimerColor" : "#3B3C3DFF",
  "subscriptionTrafficBackgroundColor" : "#00343BFF",
  "subscriptionInfoBackgroundColor" : "#006B7AFF",
  "serverRowTitleTextColor" : "#D0FFF3FF",
  "serverRowBackgroundColor" : "#02424DFF",
  "powerIconColor" : "#05525ACA",
  "supportIconColor" : "#F3FFF9FF",
  "profileWebPageIconColor" : "#F5FFF9FF",
  "selectedServerRowColor" : "#006B7BFF",
  "disclosureHeaderTextColor" : "#D0FFF3FF",
  "subsHeaderColor" : "#007982FF",
  "elipseColors" : [
    "#4DFF00CC",
    "#E2FF00FF",
    "#FF6000FF"
  ],
  "subscriptionInfoTextColor" : "#E5FFF7FF",
  "buttonColor" : "#8FFFFEFF",
  "serverRowSubTitleTextColor" : "#ADD3CBFF",
  "topBarButtonsColor" : "#FFFFFFD8",
  "settingsControlsTintColor" : "#00C3C1FF",
  "backgroundGradientColorIntensity" : 1,
  "disclosureSubHeaderTextColor" : "#A4FFE599",
  "additionalOptionsButtonColor" : "#FBFFFF99",
  "backgroundImageType" : "light",
  "backgroundColors" : [
    "#003740FF",
    "#003740FF",
    "#005255FF",
    "#00A6A1FF",
    "#00C9DDFF"
  ],
  "subHeaderButtonColor" : "#BAD7CFFF",
  "buttonTextColor" : "#000000FF"
}
```
{% endcode %}

**Пример настройки данного параметра:**

```
color-profile: [String] //base64 or plainString
color-profile: resetcolors // full reset
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
color-profile: {"backgroundGradientRotationAngle":37.1,"serverRowBackgroundColor":"#21003D67","subsHeaderColor":"#42296DFF","profileWebPageIconColor":"#A2B8FFFF","selectedServerRowColor":"#3E2F62B5","disclosureSubHeaderTextColor":"#C1C2E2FF","buttonTextColor":"#FFFFFFFF","buttonTimerColor":"#FFFFFFFF","subscriptionInfoBackgroundColor":"#21003CFF","backgroundColors":["#3D2A7DFF","#6557BAFF","#9377FF7F"],"disclosureHeaderTextColor":"#FFFFFFFF","backgroundGradientColorIntensity":1,"additionalOptionsButtonColor":"#FFFFFFFF","buttonImageType":"light","serverRowSubTitleTextColor":"#C1C2E2FF","supportIconColor":"#FFFFFFFF","topBarButtonsColor":"#FFFFFFFF","subscriptionTrafficBackgroundColor":"#533EA7FF","subHeaderButtonColor":"#FFFFFFFF","buttonColor":"#9377FFFF","powerIconColor":"#3D2A7DFF","subscriptionInfoTextColor":"#FFFFFFFF","serverRowTitleTextColor":"#FFFFFFFF","backgroundImageType":"system","elipseColors":["#00B460FF","#CF72FFE0","#FFDD00FF"],"serverRowChevronColor":"#FFFFFFFF"}
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#color-profile: {"backgroundGradientRotationAngle":37.1,"serverRowBackgroundColor":"#21003D67","subsHeaderColor":"#42296DFF","profileWebPageIconColor":"#A2B8FFFF","selectedServerRowColor":"#3E2F62B5","disclosureSubHeaderTextColor":"#C1C2E2FF","buttonTextColor":"#FFFFFFFF","buttonTimerColor":"#FFFFFFFF","subscriptionInfoBackgroundColor":"#21003CFF","backgroundColors":["#3D2A7DFF","#6557BAFF","#9377FF7F"],"disclosureHeaderTextColor":"#FFFFFFFF","backgroundGradientColorIntensity":1,"additionalOptionsButtonColor":"#FFFFFFFF","buttonImageType":"light","serverRowSubTitleTextColor":"#C1C2E2FF","supportIconColor":"#FFFFFFFF","topBarButtonsColor":"#FFFFFFFF","subscriptionTrafficBackgroundColor":"#533EA7FF","subHeaderButtonColor":"#FFFFFFFF","buttonColor":"#9377FFFF","powerIconColor":"#3D2A7DFF","subscriptionInfoTextColor":"#FFFFFFFF","serverRowTitleTextColor":"#FFFFFFFF","backgroundImageType":"system","elipseColors":["#00B460FF","#CF72FFE0","#FFDD00FF"],"serverRowChevronColor":"#FFFFFFFF"}
vless://70cc48c5‑b2f4…
vmess://zkIAU1JitkI…
```
{% endcode %}

</details>

<details>

<summary>Включить все сети (Только iOS)</summary>

Включает использование всех сетей в туннеле (NetworkExtension). Функция доступна в ОС начиная с iOS 16.4.\
На устройствах с более старой версией iOS параметр не будет иметь эффекта, а соответствующие переключатели в DevSettings не появятся.

**Пример настройки данного параметра:**

```
include-all-networks-enable: [true / 1]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
include-all-networks-enable: true
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#include-all-networks-enable: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>Исключить локальные сети (Только iOS)</summary>

Если включена опция "Включить все сети", данный параметр позволяет исключить локальные сети из туннеля (NetworkExtension).\
Трафик локальных сетей будет идти напрямую. Доступно для iOS 16.4+.

**Пример настройки данного параметра:**

```
exclude-local-networks-enable: [true / 1]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
exclude-local-networks-enable: true
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#exclude-local-networks-enable: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>Исключить APNS (Только iOS)</summary>

Если включена опция "Включить все сети", данный параметр позволяет исключить Apple Push Notification Service (APNS) из туннеля.\
Все диапазоны работы уведомлений Apple будут идти напрямую. Доступно для iOS 16.4+.

**Пример настройки данного параметра:**

```
exclude-apns-enable: [true / 1]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
exclude-apns-enable: true
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#exclude-apns-enable: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>Не использовать фильтрацию списка серверов</summary>

По умолчанию в Premium-подписках работает автоматическая фильтрация:\
* Если в имени сервера есть "only WiFi" — он виден только при Wi-Fi подключении.
* Если в имени есть "only Mobile" — он виден только при мобильном интернете.
Данная опция отключает это поведение.

**Пример настройки данного параметра:**

```
dont-use-filter: [true / 1]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
dont-use-filter: true
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#dont-use-filter: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>Закрепить текущую подписку</summary>

Позволяет закрепить (Pin) или открепить подписку в общем списке.\
* true — закрепляет подписку сверху.
* false — открепляет.

**Пример настройки данного параметра:**

```
subscription-pin: [true / 1]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
subscription-pin: true
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#subscription-pin: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>Блокировка изменения User-Agent</summary>

Блокирует возможность ручного изменения **User Agent** пользователем через интерфейс приложения.\
При этом провайдер по-прежнему может менять его удаленно через параметр **change-user-agent**.

**Пример настройки данного параметра:**

```
manual-block-user-agent: [true / 1]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
manual-block-user-agent: true
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#manual-block-user-agent: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>Изменение сортировки серверов в подписке</summary>

Определяет порядок отображения серверов внутри подписки:

* **without** — без сортировки (как передано с бэкенда).
* **ping** — по задержке (сервера с меньшим пингом выше, недоступные — в конце).
* **alphabet** — по алфавиту.

**Пример настройки данного параметра:**

```
subscriptions-sort-type: [without, ping, alphabet]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
subscriptions-sort-type: ping
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#subscriptions-sort-type: ping
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>

<summary>Брать DNS для туннеля из JSON</summary>

Логика применяется только при одновременном соблюдении условий: используется конфигурация JSON,\
отсутствует профиль маршрутизации и включен переключатель в настройках.\
Система берет первый сервер из dns.servers в JSON.

Алгоритм выбора:

* **Прямой IP**: Если указан IPv4/IPv6, он ставится как DOU DNS-туннеля.
* **DoH**: Если указан URL (https://), ищется IP в dns.hosts.
  - iOS: Настраивается полноценный DoH-запрос.
  - Android / Desktop: Используется IP из hosts (DOU).

* **Объект**: Извлекается значение из поля address аналогично описанию выше.
* **Резервный DNS (Fallback)**:\
Если основной сервер невалиден, используется стандартный:
  - Android / Desktop: 1.1.1.1 (DOU).
  - iOS: Cloudflare DoH (https://cloudflare-dns.com/dns-query).

**Пример настройки данного параметра:**

```
dns-from-json-enable: [true / 1]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
HTTP/2 200 
dns-from-json-enable: true
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#dns-from-json-enable: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>
<summary>User-Agent для скачивания гео-файлов</summary>

Позволяет изменить значение заголовка User-Agent при скачивании Geo-IP и Geo-Site файлов.

**Доступные значения:** 
* **safari-mac**
* **chrome-win**
* **safari-ios**
* **firefox-win**
* **chrome-android**

**Пример настройки:**

```
user-agent-geo-files: safari-mac
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
user-agent-geo-files: chrome-win
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#user-agent-geo-files: chrome-win
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>
<summary>Таймаут пинга через прокси (Только iOS)</summary>

Устанавливает время ожидания (в секундах) при проверке доступности (пинге) через прокси-сервер.\
Допустимый диапазон: **5 – 15** секунд.\
Значения вне диапазона игнорируются, устанавливается дефолтное значение 7.

**Пример настройки:**

```
proxy-ping-timeout: 10
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
proxy-ping-timeout: 10
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#proxy-ping-timeout: 10
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>

<details>
<summary>Скрыть иконку VPN (Hide Proxy Icon)</summary>

Управляет отображением иконки VPN в статус-баре системы.\
Переключатель реагирует на наличие обоих маршрутов (::/128 и 0.0.0.0/8) в списке исключений (excluded-routes).\
При включении опции эти маршруты автоматически добавляются в список исключений, при выключении — удаляются.

**Пример настройки:**

```
hide-vpn-icon: [true / 1]
```

**Способы передачи:**

{% code title="Через HTTP Headers:" %}
```
hide-vpn-icon: true
```
{% endcode %}

{% code title="Через тело подписки:" %}
```
#hide-vpn-icon: true
vless://70cc48c5‑b2f4…
```
{% endcode %}

</details>


