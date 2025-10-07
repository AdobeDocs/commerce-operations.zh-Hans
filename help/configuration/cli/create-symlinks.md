---
title: 创建指向LESS文件的符号链接
description: 了解如何为Adobe Commerce开发创建指向LESS文件的符号链接。 发现样式表链接和开发工作流优化。
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# 创建指向LESS文件的符号链接

{{file-system-owner}}

要创建指向LESS文件的符号链接：

命令选项：

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>在开发过程中，此命令为`var/view_preprocessed`和`pub/static`文件夹中的LESS文件创建符号链接。 此过程不会将LESS文件编译为CSS文件。

下表说明了此命令的参数和值。

| 参数 | 值 | 必需？ |
| --------- | ----- | --------- |
| `--type` | 源文件的类型： [less] （默认值： &quot;less&quot;）<br>目前，LESS是唯一支持的文件类型。 | 否 |
| `--locale` | 区域设置代码。<br>要显示区域设置代码列表，请输入`bin/magento info:language:list` | 否 |
| `--area` | 区域（`adminhtml`表示管理区域，`frontend`表示店面）。 | 否 |
| `--theme` | `<VendorName>/<theme-name>`格式的主题名称。 例如，`Magento/blank`或`Magento/backend`。 | 否 |
| `<file>` | 要转换为LESS但不带CSS扩展名的CSS文件列表（以空格分隔）。 （对于adminhtml类型`css/styles-m css/styles-l`，默认值为`css/styles css/styles-old`） | 否 |

例如，要使用名为`VendorName/themeName`的CSS文件在`en_US`区域设置中为名为`<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`的前端主题创建LESS文件，请输入以下命令：

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

将显示以下消息以确认成功：

```
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

要为admin html创建LESS文件：

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
