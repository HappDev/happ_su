# Provider ID

Provider ID — уникальный идентификатор, связывающий вашу подписку с аккаунтом на сайте [happ-proxy.com](https://happ-proxy.com/). Он открывает доступ к расширенной статистике использования приложения и позволяет точно учитывать число активных устройств.

***

### Где взять Provider ID?

Для получения Provider ID необходимо зарегистрироваться на сайте [https://happ-proxy.com](https://happ-proxy.com/)\
После регистрации вы сможете его увидеть в верхней правой части экрана или в профиле пользователя.

### **Как это работает**

Один раз в сутки приложение отправляет GET‑запрос на:

```
https://check.happ-proxy.com/provider?id={ProviderID}
```

В запрос включаются:

* **providerid** — ваш уникальный идентификатор;
* **хеш домена**, с которого загружена подписка;
* **HWID** устройства;
* **название и версия** операционной системы.

Хеш домена гарантирует привязку ProviderID к конкретному домену подписки и исключает его использование на других сайтах или в чужих подписках.

***

### **Способы передачи ProviderID**

Вы можете добавить ProviderID в подписку тремя способами:

1.  **В URL** (query‑параметр)

    ```
    https://your-domain.com/sub/123#?providerid={ProviderID}
    ```
2.  **В теле подписки** (комментарий)

    ```
    #providerid {ProviderID}
    vless://70cc48c5‑b2f4…
    vmess://zkIAU1JitkI…
    ```
3.  **В HTTP‑заголовке** ответа

    ```
    HTTP/2 200 OK
    date: Wed, 14 Apr 2025 10:00:00 GMT
    content-type: application/json
    content-length: 3798
    content-disposition: attachment; filename="213"
    providerid: {ProviderID}
    ```
