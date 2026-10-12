---
title: 升级数据库架构和数据
description: 按照以下步骤升级Adobe Commerce数据库架构。
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
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
source-wordcount: '169'
ht-degree: 0%
---
# 升级数据库架构和数据

使用此命令之前，必须[安装应用程序](../advanced.md)。

## 升级数据库架构和数据

无论何时执行导致数据库模式或数据更改的操作，都必须通过运行本节中介绍的命令来更新它们。 部分原因如下：

* 您使用命令行升级了应用程序
* 您使用命令行安装或更新了组件
* 使用命令行启用或禁用组件

>[!NOTE]
>
>*组件*&#x200B;可以是模块、主题或语言包；组件是否来自Commerce Marketplace无关。

1. 开始升级：

   ```shell
   bin/magento setup:upgrade [--keep-generated]
   ```

   其中`--keep-generated`是不更新[静态视图文件](../../configuration/cli/static-view-file-deployment.md)的可选参数。 此可选参数仅供经验丰富的系统集成商在有限的情况下使用&#x200B;*1&rbrace;。*&#x200B;在[生产模式](../../configuration/bootstrap/application-modes.md#production-mode)中只应使用&#x200B;*1&rbrace;。*&#x200B;它应该&#x200B;*不*&#x200B;在[开发人员模式](../../configuration/bootstrap/application-modes.md#developer-mode)中使用。

1. 清理缓存：

   ```shell
   bin/magento cache:clean
   ```
