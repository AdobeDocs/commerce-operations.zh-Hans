---
title: 转换布局文件
description: 转换XML布局文件
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 0%

---

# 转换XML布局文件

{{file-system-owner}}

如果更新相应的可扩展样式表语言转换(XSLT)样式表，则使用此命令更新布局XML文件。

- [布局说明](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [布局文件类型](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

命令选项：

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

其中：

- `{xml file}` — 要转换的布局XML文件的完整路径和文件名（必需）
- `{xslt stylesheet}` — 是用于转换的XSLT样式表文件的完整路径和文件名（必需）
- `-o|--overwrite` — 包含此选项以覆盖现有XML文件
