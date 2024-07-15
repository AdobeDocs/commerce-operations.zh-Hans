---
title: .gitignore引用
description: 请参阅如何添加包含在忽略列表中的文件。
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '51'
ht-degree: 0%

---

# .gitignore引用

Magento Open Source包含基`.gitignore`文件。 查看[最新的Commerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore)文件。 如果必须添加位于`.gitignore`列表中的文件，则可以在暂存提交时使用`-f` （强制）选项：

```bash
git add <path/filename> -f
```
