---
title: .gitignore引用
description: 请参阅如何添加包含在忽略列表中的文件。
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 0%

---

# .gitignore引用

Magento Open Source包括基底 `.gitignore` 文件。 参见 [最新的Commerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) 文件。 如果您必须添加一个文件，该文件位于 `.gitignore` 列表，您可以使用 `-f` 暂存提交时的（强制）选项：

```bash
git add <path/filename> -f
```
