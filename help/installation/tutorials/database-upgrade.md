---
title: 升级数据库架构和数据
description: 按照以下步骤升级Adobe Commerce数据库架构。
exl-id: bef04561-6c6b-4636-a8ab-a1ade44f5a8f
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
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

   其中`--keep-generated`是不更新[静态视图文件](../../configuration/cli/static-view-file-deployment.md)的可选参数。 此可选参数仅供经验丰富的系统集成商在有限的情况下使用&#x200B;*1}。*&#x200B;在[生产模式](../../configuration/bootstrap/application-modes.md#production-mode)中只应使用&#x200B;*1}。*&#x200B;它应该&#x200B;*不*&#x200B;在[开发人员模式](../../configuration/bootstrap/application-modes.md#developer-mode)中使用。

1. 清理缓存：

   ```shell
   bin/magento cache:clean
   ```
