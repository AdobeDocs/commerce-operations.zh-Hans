---
title: 创建指向较少文件的符号链接
description: 了解如何创建指向LESS文件的符号链接。
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# 创建指向较少文件的符号链接

{{file-system-owner}}

要创建指向LESS文件的符号链接：

命令选项：

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>在开发过程中，此命令为LESS文件在中创建符号链接 `var/view_preprocessed` 和 `pub/static` 文件夹。 此过程不会将LESS文件编译为CSS文件。

下表说明了此命令的参数和值。

| 参数 | 值 | 必需？ |
| --------- | ----- | --------- |
| `--type` | 源文件的类型： [更少] （默认值：“less”）<br>目前，LESS是唯一支持的文件类型。 | 否 |
| `--locale` | 区域设置代码。<br>要显示区域设置代码列表，请输入 `bin/magento info:language:list` | 否 |
| `--area` | 区域(`adminhtml` 行政区， `frontend` （对于店面）。 | 否 |
| `--theme` | 中的主题名称 `<VendorName>/<theme-name>` 格式。 例如， `Magento/blank` 或 `Magento/backend`. | 否 |
| `<file>` | 要转换为LESS但不带CSS扩展名的CSS文件列表（以空格分隔）。 (默认为 `css/styles-m css/styles-l`，对于adminhtml类型 `css/styles css/styles-old`) | 否 |

例如，为名为的前端主题创建LESS文件 `VendorName/themeName` 在 `en_US` 使用名为的CSS文件设置区域设置 `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`，输入以下命令：

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

显示以下消息以确认成功：

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

要为adminhtml创建LESS文件，请执行以下操作：

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
