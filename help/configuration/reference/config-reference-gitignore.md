---
title: .gitignore引用
description: 了解如何向Adobe Commerce项目的.gitignore列表添加文件。 探索版本控制管理和文件排除最佳实践。
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# .gitignore引用

Magento Open Source包含基本`.gitignore`文件。 查看[最新的Commerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore)文件。 如果必须添加位于`.gitignore`列表中的文件，则可以在暂存提交时使用`-f` （强制）选项：

```shell
git add <path/filename> -f
```
