---
title: 转换布局文件
description: 了解如何使用Adobe Commerce命令行工具转换XML布局文件。 发现XSLT样式表更新和文件转换过程。
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%
---
# 转换XML布局文件

{{file-system-owner}}

如果更新相应的可扩展样式表语言转换(XSLT)样式表，则使用此命令更新布局XML文件。

- [布局说明](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions)
- [布局文件类型](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-files-types-and-conventions)

命令选项：

```shell
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

其中：

- `{xml file}` — 要转换的布局XML文件的完整路径和文件名（必需）
- `{xslt stylesheet}` — 是用于转换的XSLT样式表文件的完整路径和文件名（必需）
- `-o|--overwrite` — 包含此选项以覆盖现有XML文件
