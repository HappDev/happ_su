# Геонастройки / Routing

Приложение поставляется с предустановленными геофайлами, что обеспечивает его готовность к работе сразу после установки. Актуальность геофайлов поддерживается обновлением версии ядра внутри приложения.&#x20;

### **Добавление правил маршрутизации**

Приложение позволяет добавлять правила маршрутизации автоматически, используя специальные ссылки, которые можно создать на сайте [https://routing.happ.su](https://routing.happ.su/).

Ссылки могут быть переданы одним из следующих способов:

* Через буфер обмена.
* С использованием deeplink.
* Через QR-код.
* В виде HTTP-заголовков или тела подписки.

Для передачи через HTTP-заголовок используется параметр `routing`, а для добавления в тело подписки достаточно указать ссылку.

### **Обработка ошибок загрузки**

Приложение использует менеджер загрузки геофайлов, который работает в фоновом режиме.

* Если загрузка геофайлов не завершается в течение 3 минут, процесс останавливается.
* На главном экране появляется сообщение об ошибке.
* В списке профилей рядом с проблемным профилем отображается красный восклицательный знак.

### **Устранение ошибок**

Проблемное состояние профиля исчезает автоматически после:

* Успешного завершения загрузки файлов.
* Удаления проблемного профиля.

Если в списке больше нет проблемных профилей, уведомления об ошибках удаляются.

### **Виды ссылок:**

* `happ://routing/add/{base64}`: Добавляет профиль в список профилей. Первый добавленный профиль становится активным только после успешной загрузки геофайлов. Если профиль с таким именем уже существует, он перезаписывается.
* `happ://routing/onadd/{base64}`: Добавляет и автоматически активирует профиль, даже если другие профили уже активны. Если профиль с таким именем уже существует, он перезаписывается.
* `happ://routing/off`: Отключит функционал маршрутизации

`{base64}`:это JSON-профиль, преобразованный в текстовый формат base64.

### **Структура профилей**

Приложение использует профили маршрутизации, которые настраиваются через JSON.

**Профиль по умолчанию** содержит базовые настройки, используемые для заполнения отсутствующих или некорректных параметров.

**Пример профиля по умолчанию:**

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

**Пример пользовательского профиля:**

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

### **Особенности работы с профилями**

* Если профиль с таким же именем уже существует, его данные обновляются.
* Если у профиля есть параметр `"LastUpdated": ""` и он содержит дату в формате Unix, которая больше предыдущего значения, он будет обновлён.

### Схема добавления / обновления профиля

{% embed url="https://www.figma.com/board/EQnbUQwxUqNG35uJcKfQCz/Routing-Flow?node-id=0-1&t=qKffplQufcmeJfxO-1" %}

**Пример http headers:**

```
HTTP/2 200 
date: Wed, 24 Nov 2024 10:00:52 GMT
content-type: application/json
content-length: 3798
content-disposition: attachment; filename="213"
routing: happ://routing/onadd/ewogICAgIk5hbWUiOiAidGVzdCIsCiAgICAiR2xvYmFsUHJveHkiOiAidHJ1ZSIsCiAgICAiUmVtb3RlRG5zIjogIiIsCiAgICAiRG9tZXN0aWNEbnMiOiAiIiwKICAgICJHZW9pcHVybCI6ICIiLAogICAgIkdlb3NpdGV1cmwiOiAiIiwKICAgICJEbnNIb3N0cyI6IHt9LAogICAgIkRpcmVjdFNpdGVzIjogW10sCiAgICAiRGlyZWN0SXAiOiBbXSwKICAgICJQcm94eVNpdGVzIjogW10sCiAgICAiUHJveHlJcCI6IFtdLAogICAgIkJsb2NrU2l0ZXMiOiBbXSwKICAgICJCbG9ja0lwIjogW10sCiAgICAiRG9tYWluU3RyYXRlZ3kiOiAiQXNJcyIKfQ==
```

**Пример тела подписки:**

```
happ://routing/onadd/ewogICAgIk5hbWUiOiAidGVzdCIsCiAgICAiR2xvYmFsUHJveHkiOiAidHJ1ZSIsCiAgICAiUmVtb3RlRG5zIjogIiIsCiAgICAiRG9tZXN0aWNEbnMiOiAiIiwKICAgICJHZW9pcHVybCI6ICIiLAogICAgIkdlb3NpdGV1cmwiOiAiIiwKICAgICJEbnNIb3N0cyI6IHt9LAogICAgIkRpcmVjdFNpdGVzIjogW10sCiAgICAiRGlyZWN0SXAiOiBbXSwKICAgICJQcm94eVNpdGVzIjogW10sCiAgICAiUHJveHlJcCI6IFtdLAogICAgIkJsb2NrU2l0ZXMiOiBbXSwKICAgICJCbG9ja0lwIjogW10sCiAgICAiRG9tYWluU3RyYXRlZ3kiOiAiQXNJcyIKfQ==
vmess://eyJob3N0IjoiZ3Vhdmypc3RhbmJ1bC5jb20iLCJwYXRoIjoiXC8xUyIsInRscyI6InRscyIsImFkZCI6Ind3dy5ndWF2ZWlzdGFuYnVsLmNvbSIsInBvcnQiOjQ0MywiYWlkIjowLCJuZXQiOiJ3cyIsInR5cGUiOiJub25lIiwiZnAiOiJjaHJvbWUiLCJhbHBuIjoiaHR0cFwvMS4xIiwibm9kZV9zc19wdWJsaWNrZXkiOiIiLCIiOmZhbHNlLCJ2IjoiMiIsInBzIjoiXHVkODNjXHVkZGU5XHVkODNjXHVkZGVhIDRHIC0gR2VybWFueSAtIDAxIiwiaWQiOiI4YjhkYWI4NC03OGEzLTNhMWItYTE1NS03M2FkNDk1ZTY0NmUifQ==
vless://70cc43c5-b2f4-34ac-a092-d806984a6b8c@1.13.7.91:443?encryption=none&security=reality&pbk=qGPTy8EZokn3hWp6hKBQ0MVvEuLRJCcv5UdWeP4TVhI&headerType=none&fp=chrome&type=tcp&flow=xtls-rprx-vision&sni=booking.com&sid=6ba85179e30d4fc2#%F0%9F%87%B1%F0%9F%87%B9%20Test
```

### Настройки маршрутизации, которые определяют логику обработки трафика, работу DNS и правила фильтрации ресурсов.

---

## 1. Основные настройки
* **Название (`name`)**: Имя профиля для идентификации пользователем **По умолчанию: Default**.
* **Глобальный прокси (`globalProxy`)**: 
    * `true`: Весь трафик по умолчанию идет через прокси (первым в списке устанавливается `outbound` с тэгом `proxy`) **По умолчанию: `true`**.
    * `false`: По умолчанию используется прямое соединение (первым в списке устанавливается `outbound` с тэгом `direct`).
    * *Примечание: Это также определяет «выход» (outbound) по умолчанию, если ни одно правило маршрутизации не сработало.*
* **Дата обновления (`lastUpdatedDate`)**: Метка времени последнего изменения профиля или обновления связанных Geo-баз .
* **Важно:** при сохранении профиля маршрутизации впервые в приложении если дата последнего обновления заплонена (!= null) будет выполнено скачивание геофайлов независимо от того совпадают ли их URL с стандартными внутри приложения! 
* Также это свойство можно использовать для принудительного скачивания геофайлов при обновлении профиля (возможно при обновлении подписки) - Условие: Новая дата обновения `lastUpdatedDate` должна быть позже чем текущая дата в сохраненном профиле либо текущая дата отсутствует.

## 2. Конфигурация DNS
Система использует разделение на локальные (Domestic) и удаленные (Remote) DNS-серверы для оптимальной скорости и обхода блокировок.

### Удаленный DNS (Remote) — для запросов `proxy` ресурсов через прокси сервер
* **Тип (`remoteDnsType`)**: Протокол запроса (например, DoH — DNS over HTTPS, DoU — DNS over UDP). 
    * *По умолчанию:* `DoU`.
* **Домен (`remoteDnsDomain`)**: Адрес сервера. **Обязателен**, если выбран тип `DoH`.
    * *По умолчанию:* `https://cloudflare-dns.com/dns-query`.
* **IP (`remoteDnsIp`)**: Статический IP-адрес сервера для исключения проблем с поиском самого DNS-сервера. 
    * *По умолчанию:* `1.1.1.1`.

### Локальный DNS (Domestic) — для запросов `direct` ресурсов в обход прокси сервера (напрямую)
* **Тип (`domesticDnsType`)**: Протокол запроса. 
    * *По умолчанию:* `DoU`.
* **Домен (`domesticDnsDomain`)**: Адрес сервера. **Обязателен**, если выбран тип `DoH`
    * *По умолчанию:* `dns.google/dns-query`.
* **IP (`domesticDnsIp`)**: Статический IP-адрес сервера для исключения проблем с поиском самого DNS-сервера.
    * *По умолчанию:* `8.8.8.8`.

### Дополнительно
* **DNS Hosts (`dnsHosts`)**: Список ручных соответствий «Домен: IP». Работает как системный файл `hosts`. Не отображается в интерфейсе приложения, встраивается напрямую в секцию `dns.hosts` конфигурации Xray. Для подробностей см. [документацию Project X](https://xtls.github.io/ru/config/dns.html).
* **Fake DNS (`fakeDnsEnabled`)**: Подмена реального IP виртуальным. Это ускоряет соединение и позволяет Xray точнее определять направление трафика до завершения реального DNS-запроса.

---

## 3. Правила и списки маршрутизации
Трафик распределяется по трем категориям:
1. **Прямое подключение (`directSites` / `directIp`)**: Ресурсы, доступ к которым будет осуществляться без прокси.
2. **Прокси (`proxySites` / `proxyIp`)**: Ресурсы, требующие туннелирования.
3. **Блокировка (`blockSites` / `blockIp`)**: Запрещенные ресурсы (реклама, трекеры).

### Ресурсы Geo-баз
* **GeoIP URL (`geoipUrl`)**: Ссылка на базу IP-адресов.
* **Geosite URL (`geositeUrl`)**: Ссылка на базу категорий доменов.

---

## 4. Продвинутые параметры

### Стратегия доменов (`domainStrategy`)
Определяет, как Xray сопоставляет домены с правилами IP:
* **AsIs**: Проверка только по домену. Если правила для домена нет, запрос идет дальше.
* **IPIfNonMatch**: Если по домену правило не найдено, Xray резолвит его в IP и проверяет правила для IP.
* **IPOnDemand**: При любой проверке домена Xray сразу резолвит его в IP для сопоставления.

### Использование оптимизированных файлов (`useChunkFiles`)
**Важно:** Функция для экономии ресурсов устройства.
При значении `true` приложение скачивает полные базы по указанным URL (если они не идентичны стандартным url в приложении defGeoIpUrl = "https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geoip.dat"
    defGeoSiteUrl = "https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geosite.dat"), затем сохраняет в дополнительный файл **только те записи, которые вы явно указали в секциях (direct/proxy/block) текущего профиля маршрутизации**. 
* *Внимание:* Если вы используете кастомную JSON-конфигурацию, обязательно продублируйте нужные теги `geosite/geoip` в соответствующие секции профиля, иначе функция «не увидит» их и не включит в сокращенный файл.

### Порядок маршрутизации (`routeOrder`)
Определяет приоритет проверки правил. Трафик проверяется по списку слева направо:
1. Приложение берет первое правило из списка `routeOrder`.
2. Если совпадения нет, переходит к следующему.
3. Если ни одно правило не подошло, трафик направляется в основной выход (Proxy, если `globalProxy` включен, или Direct, если выключен).

---
