---
hidden: true
noIndex: true
---

# Отображение Meta info

<figure><img src="../.gitbook/assets/Frame 110 (1).png" alt="" width="375"><figcaption></figcaption></figure>

Владелец подписки может отобразить информацию о потребленном и оставшемся трафике, сроке действия подписки, а также отображать объявления и задавать до двух ссылок для иконок в строке отображения метаданных.

Все данные могут быть переданы в формате plain text или base64.

Метаданные можно передать двумя способами:

1. Через HTTP-заголовок страницы подписки.
2. Через тело подписки, указав перед параметром знак # (например #profile-title).

### Параметры отображения

* **`profile-title`** (string):\
  Название профиля. Может быть передано как plain text или в base64 (UTF-8).\
  **Ограничение**: Максимальная длина — 25 символов.
* **`subscription-userinfo`** (string):\
  Содержит информацию для отображения трафика и срока подписки.
  * В левой части шкалы отображается сумма потребленного трафика (`upload + download`), в правой части после знака `/` — общий объем (`total`).
  * Дата окончания подписки указана в параметре `expire`.\
    **Примечание**: Все данные передаются в одном заголовке и разделяются символом `;`.
* **`support-url`** (string):\
  Ссылка на поддержку.
  * Отображается иконкой синего цвета в правой части строки.
  * Область клика выделена зеленым прямоугольником.
* **`profile-web-page-url`** (string):\
  Ссылка на веб-страницу профиля.
  * Если параметр указан, иконка приобретает синий цвет (аналогично `support-url`).
  * Область клика также выделена зеленым прямоугольником.
* **`announce`** (string):\
  Текст объявления. Может быть передан в формате plain text или base64.\
  **Ограничение**: Максимальная длина отображаемого текста — 200 символов.

### Параметр обновления

**profile-update-interval** (int): Интервал автоматического обновления подписки, задаётся в часах.\
Если пользователь указал интервал в настройках приложения, этот параметр будет проигнорирован.

### Дополнительные рекомендации

* Для корректного отображения метаданных убедитесь, что формат данных соответствует требованиям (plain text или base64 UTF-8).
* Параметры, указанные в теле подписки, имеют более высокий приоритет, чем параметры, переданные через HTTP-заголовки.
* Если часть параметров поступает через HTTP-заголовки, а другая часть через тело подписки, необходимо объединить (merge) все параметры, учитывая их приоритеты, и корректно отобразить результат.<br>

***

### **Пример http headers:**

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
profile-web-page-url: https://happ.su
support-url: https://t.me//happ_chat
profile-title: base64:0J/QvtC00L/QuNGB0LrQsA==
profile-update-interval: 1
subscription-userinfo: upload=0; download=122190068697; total=0; expire=0
announce: base64:J1bC5jb20iLCJwYXRoIjoiXC8xUyIsInRscyI6InRscyIsImFkZCI6Ind3dy5ndWF2ZWlzdGFuYnVsLmN
cf-cache-status: DYNAMIC
```

### **Пример тела подписки:**

```
#profile-title: Happ.su
#profile-title: base64:0J/QvtC00L/QuNGB0LrQsA==
#profile-update-interval: 1
#subscription-userinfo: upload=455727941; download=6174315083; total=1073741824000; expire=1671815872
#support-url: https://t.me/happ_chat
#profile-web-page-url: https://happ.su
#announce: base64:J1bC5jb20iLCJwYXRoIjoiXC8xUyIsInRscyI6InRscyIsImFkZCI6Ind3dy5ndWF2ZWlzdGFuYnVsLmN
vmess://eyJob3N0IjoiZ3Vhdmypc3RhbmJ1bC5jb20iLCJwYXRoIjoiXC8xUyIsInRscyI6InRscyIsImFkZCI6Ind3dy5ndWF2ZWlzdGFuYnVsLmNvbSIsInBvcnQiOjQ0MywiYWlkIjowLCJuZXQiOiJ3cyIsInR5cGUiOiJub25lIiwiZnAiOiJjaHJvbWUiLCJhbHBuIjoiaHR0cFwvMS4xIiwibm9kZV9zc19wdWJsaWNrZXkiOiIiLCIiOmZhbHNlLCJ2IjoiMiIsInBzIjoiXHVkODNjXHVkZGU5XHVkODNjXHVkZGVhIDRHIC0gR2VybWFueSAtIDAxIiwiaWQiOiI4YjhkYWI4NC03OGEzLTNhMWItYTE1NS03M2FkNDk1ZTY0NmUifQ==
vless://70cc43c5-b2f4-34ac-a092-d806984a6b8c@1.13.7.91:443?encryption=none&security=reality&pbk=qGPTy8EZokn3hWp6hKBQ0MVvEuLRJCcv5UdWeP4TVhI&headerType=none&fp=chrome&type=tcp&flow=xtls-rprx-vision&sni=booking.com&sid=6ba85179e30d4fc2#%F0%9F%87%B1%F0%9F%87%B9%20Test
```
