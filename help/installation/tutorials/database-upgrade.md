---
title: 升级数据库模式和数据
description: 按照以下步骤升级您的Adobe Commerce或Magento Open Source数据库模式。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 升级数据库模式和数据

在使用此命令之前，您必须 [安装应用程序](../advanced.md).

## 升级数据库模式和数据

无论您何时执行导致 [数据库模式](https://glossary.magento.com/database-schema) 或要更改的数据，必须运行本节中讨论的命令来更新它们。 部分原因如下：

* 使用命令行升级了应用程序
* 您使用命令行安装或更新了组件
* 您可以使用命令行启用或禁用组件

>[!NOTE]
>
>A *组件* 可以是模块、主题或语言包；组件是否来自Commerce Marketplace无关紧要。

1. 开始升级：

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   其中 `--keep-generated` 是不更新的可选参数 [静态视图文件](../../configuration/cli/static-view-file-deployment.md). 此可选参数可供使用 *仅* 在有限的情况下由经验丰富的系统集成商进行。 应使用 *仅* in [生产模式](../../configuration/bootstrap/application-modes.md#production-mode). 它应该 *not* 在 [开发人员模式](../../configuration/bootstrap/application-modes.md#developer-mode).

1. 清除缓存：

   ```bash
   bin/magento cache:clean
   ```
