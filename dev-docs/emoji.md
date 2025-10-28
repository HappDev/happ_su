# 显示国旗和表情符号

### 国旗

如果服务器名称中的第一个 emoji 是国旗图标，该图标将作为服务器图标显示。​其后的其他国旗或表情符号将被忽略，仅在服务器名称中显示。​

您可以通过以下两种格式提供国旗：​

* 作为 emoji 符号（例如：🇯🇵）​
* 作为 UTF-8 URL 编码的字符串，例如：​
  * `%F0%9F%87%AF%F0%9F%87%B5` — 🇯🇵（日本）​
  * `%F0%9F%87%B7%F0%9F%87%BA` — 🇷🇺（俄罗斯）​
  * `%F0%9F%87%BA%F0%9F%87%B8` — 🇺🇸（美国）​

⚠️ 在订阅标题中，仅支持 emoji 符号（例如：🇺🇸）。不支持 UTF-8 编码的 emoji。​

***

### 表情符号

您也可以在服务器名称中使用常规的表情符号（如笑脸）。​但请注意，如果表情符号出现在国旗之前，国旗将不会作为图标显示。​

✅ 正确示例：​`🇺🇸 USA Node` → 图标：🇺🇸​

❌ 错误示例：​`🥰🇺🇸 USA Node` → 无图标​

⚠️ 在订阅标题中，仅支持 emoji 符号（例如：🥰）。不支持 UTF-8 编码的 emoji。​

***

### 示例

以下是一些示例链接：​

```
vless://uuid@ip:80?flow=&type=tcp&security=none#Right1%F0%9F%87%AF%F0%9F%87%B5%F0%9F%A5%B0
vless://uuid@ip:80?flow=&type=tcp&security=none#Right2🇯🇵🥰
vless://uuid@ip:80?flow=&type=tcp&security=none#Wrong1%F0%9F%A5%B0%F0%9F%87%AF%F0%9F%87%B5
vless://uuid@ip:80?flow=&type=tcp&security=none#Wrong2🥰🇯🇵
```

请确保在服务器名称中正确使用 emoji，以实现预期的图标显示效果。\
<img src="../.gitbook/assets/image.png" alt="" data-size="original">
