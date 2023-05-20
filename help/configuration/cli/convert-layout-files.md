---
title: 轉換配置檔案
description: 轉換XML配置檔案。
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---

# 轉換XML配置檔案

{{file-system-owner}}

如果您更新對應的可延伸樣式表語言轉換(XSLT)樣式表，請使用此命令來更新版面XML檔案。

- [版面配置指示](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [配置檔案型別](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

命令選項：

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

其中：

- `{xml file}` — 是要轉換的版面XML檔案的完整路徑和檔案名稱（必要）
- `{xslt stylesheet}` — 是用於轉換的XSLT樣式表檔案的完整路徑和檔案名稱（必要）
- `-o|--overwrite` — 包含此選項以覆寫現有的XML檔案
