---
title: 升级数据库架构和数据
description: 按照以下步骤升级Adobe Commerce或Magento Open Source数据库架构。
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# 升级数据库架构和数据

使用此命令之前，必须 [安装应用程序](../advanced.md).

## 升级数据库架构和数据

无论何时执行导致数据库模式或数据更改的操作，都必须通过运行本节中介绍的命令来更新它们。 部分原因如下：

* 您使用命令行升级了应用程序
* 您使用命令行安装或更新了组件
* 使用命令行启用或禁用组件

>[!NOTE]
>
>A *组件* 可以是模块、主题或语言包；组件是否来自Commerce Marketplace无关。

1. 开始升级：

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   位置 `--keep-generated` 是一个可选参数，不会更新 [静态视图文件](../../configuration/cli/static-view-file-deployment.md). 此可选参数可供使用 *仅限* 由经验丰富的系统集成商在有限的情况下提供。 应该使用它 *仅限* 在 [生产模式](../../configuration/bootstrap/application-modes.md#production-mode). 它应该 *非* 使用位置 [开发者模式](../../configuration/bootstrap/application-modes.md#developer-mode).

1. 清理缓存：

   ```bash
   bin/magento cache:clean
   ```
