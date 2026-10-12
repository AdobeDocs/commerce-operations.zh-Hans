---
title: .gitignore引用
description: 了解如何向Adobe Commerce项目的.gitignore列表添加文件。 探索版本控制管理和文件排除最佳实践。
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
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
source-wordcount: '65'
ht-degree: 0%
---
# .gitignore引用

Magento Open Source包含基本`.gitignore`文件。 查看[最新的Commerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore)文件。 如果必须添加位于`.gitignore`列表中的文件，则可以在暂存提交时使用`-f` （强制）选项：

```shell
git add <path/filename> -f
```
