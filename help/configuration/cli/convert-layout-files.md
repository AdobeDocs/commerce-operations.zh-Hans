---
title: 转换布局文件
description: 转换XML布局文件。
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# 转换XML布局文件

{{file-system-owner}}

如果更新相应的可扩展样式表语言转换(XSLT)样式表，则使用此命令更新布局XML文件。

- [布局说明](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/xml-instructions.html)
- [布局文件类型](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/layout-types.html)

命令选项：

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

其中：

- `{xml file}` — 是要转换的布局XML文件的完整路径和文件名（必需）
- `{xslt stylesheet}` — 是用于转换的XSLT样式表文件的完整路径和文件名（必需）
- `-o|--overwrite` — 包含此选项以覆盖现有XML文件
