---
title: 创建指向LESS文件的符号链接
description: 了解如何创建指向LESS文件的符号链接。
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# 创建指向LESS文件的符号链接

{{file-system-owner}}

要创建指向LESS文件的符号链接，请执行以下操作：

命令选项：

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>在开发过程中，此命令会在 `var/view_preprocessed` 和 `pub/static` 文件夹。 此过程不会将LESS文件编译为CSS文件。

下表说明了此命令的参数和值。

| 参数 | 值 | 必需？ |
| --------- | ----- | --------- |
| `--type` | 源文件类型： [减少] (默认：&quot;less&quot;)<br>目前， LESS是唯一支持的文件类型。 | 否 |
| `--locale` | 区域设置代码。<br>要显示区域设置代码列表，请输入 `bin/magento info:language:list` | 否 |
| `--area` | 面积图(`adminhtml` 对于行政区， `frontend` )。 | 否 |
| `--theme` | 中的主题名称 `<VendorName>/<theme-name>` 格式。 例如， `Magento/blank` 或 `Magento/backend`. | 否 |
| `<file>` | 要转换为LESS（不含CSS扩展名）的CSS文件的以空格分隔的列表。 (默认值为 `css/styles-m css/styles-l`，对于adminhtml类型 `css/styles css/styles-old`) | 否 |

例如，为名为的前端主题创建LESS文件 `VendorName/themeName` 在 `en_US` 使用名为的CSS文件进行区域设置 `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`，输入以下命令：

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

将显示以下消息以确认成功：

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

为adminhtml创建LESS文件：

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
