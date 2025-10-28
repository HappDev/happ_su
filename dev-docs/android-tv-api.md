# Android TV API

{% columns %}
{% column %}
<figure><img src="../.gitbook/assets/3242.png" alt=""><figcaption></figcaption></figure>
{% endcolumn %}

{% column %}
<figure><img src="../.gitbook/assets/3425 (1).png" alt=""><figcaption></figcaption></figure>
{% endcolumn %}
{% endcolumns %}

Чтобы передать подписку на телевизор пользователя, необходимо знать 5-значный код, сгенерированный устройством. Этот код отображается при первом запуске приложения на Android TV — достаточно выбрать пункт **Web Import**.

После этого необходимо выполнить **POST-запрос** на адрес:\
`https://check.happ.su/sendtv/[uid]`\
где **\[uid]** — это 5-значный код, отображённый на экране телевизора.

Запрос должен быть в формате JSON:

```json
{ "data": "base64" }
```

Значение `base64` — это конфигурация сервера или подписки, закодированная в формате Base64.

#### Пример запроса с использованием `curl`:

```bash
curl -X POST https://check.happ.su/sendtv/QWET5 \
  -H "Content-Type: application/json" \
  -d '{"data":"aHR0cHM6Ly90ZXN0LXN1YnMuaGFwcC5zdS9wYWdlLnBocD9pZD14Y3huV254Uw=="}'
```

В этом примере:

* `QWET5` — это UID телевизора (тот самый 5-значный код).
* Значение поля `"data"` — это пример конфигурации, закодированной в Base64

