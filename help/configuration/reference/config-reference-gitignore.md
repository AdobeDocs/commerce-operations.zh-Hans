---
title: .gitignore參考
description: 瞭解如何新增包含在忽略清單中的檔案。
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 0%

---

# .gitignore參考

Magento Open Source包含基底 `.gitignore` 檔案。 另請參閱 [最新的Commerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) 檔案。 如果您必須新增的檔案位於 `.gitignore` 清單中，您可以使用 `-f` 暫存認可時（強制）選項：

```bash
git add <path/filename> -f
```
