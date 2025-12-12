# Displaying flags and smileys

### Flags

If the **first emoji** in the server name is a **flag**, it will be used as the server icon.\
Any additional flags or emojis after the first one will be ignored by the icon and only shown in the server name.

You can provide a flag in two formats:

* **As an emoji symbol** (e.g. 🇺🇸 — visual representation)
* **As a UTF-8 URL-encoded string**, for example:
  * `%F0%9F%87%AF%F0%9F%87%B5` — 🇯🇵 (Japan)
  * `%F0%9F%87%B7%F0%9F%87%BA` — 🇨🇳 (China)
  * `%F0%9F%87%BA%F0%9F%87%B8` — 🇺🇸 (USA)

⚠️ For **subscription headers**, only emoji **symbols** (e.g. 🥰) are supported.\
**UTF-8 encoded emojis are not supported**.

***

### Emojis

You can also use regular emojis (like smileys) in server names.\
However, if a smiley appears **before the flag**, the flag will **not be shown as the icon**.

✅ Correct example:\
🇺🇸 `😎 USA Node` → icon: 🇺🇸

❌ Incorrect example:\
`😎` 🇺🇸 `USA Node` → no icon

⚠️ For **subscription headers**, only emoji **symbols** (e.g. 🥰) are supported.\
**UTF-8 encoded emojis are not supported**.

### Example

```
vless://uuid@ip:80?flow=&type=tcp&security=none#Right1%F0%9F%87%AF%F0%9F%87%B5%F0%9F%A5%B0
vless://uuid@ip:80?flow=&type=tcp&security=none#Right2🇯🇵🥰
vless://uuid@ip:80?flow=&type=tcp&security=none#Wrong1%F0%9F%A5%B0%F0%9F%87%AF%F0%9F%87%B5
vless://uuid@ip:80?flow=&type=tcp&security=none#Wrong2🥰🇯🇵
```

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
