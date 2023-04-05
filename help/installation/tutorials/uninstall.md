---
title: 卸载或重新安装Adobe Commerce
description: 按照以下步骤卸载并重新安装Adobe Commerce和Magento Open Source的内部安装。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---


# 卸载或重新安装Adobe Commerce

在使用这些命令之前，您必须 [安装应用程序](../tutorials/install.md).

## 更新应用程序

要更新应用程序，请执行以下操作：

* 如果您通过存档安装了软件，或者如果您使用了“composer-create-project”，请参阅 [升级指南](../../upgrade/overview.md).
* 如果您是参与开发人员(即，使用 `git clone`)，请参阅 [更新应用程序](../../upgrade/developer/git-installs.md).

## 重新安装应用程序

从命令行重新安装应用程序的方式取决于您的角色：

* 如果您通过存档安装了软件，或者使用了“composer-create-project”，请参阅 [更新安装依赖项](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* 如果您是参与开发人员(即，您开始使用 `git clone`)，请参阅 [更新安装依赖项](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## 卸载应用程序

卸载应用程序会丢弃并还原数据库，删除部署配置，并清除下面的目录 `var`.

要卸载应用程序，请输入以下命令：

```bash
bin/magento setup:uninstall
```

将显示以下消息以确认卸载成功：

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## （可选）保留生成的文件

默认情况下， `bin/magento setup:upgrade` 清除编译的代码和缓存。 通常，您使用 `bin/magento setup:upgrade` 要更新组件和每个组件可能需要不同的编译类。

但是，在某些情况下（特别是部署到生产），您可能希望避免清除已编译的代码，因为这可能需要一些时间。 （缓存仍被清除。） 更新数据库模式和数据 *无* 清除编译代码，输入：

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>可选 `--keep-generated` 选项应在有限情况下由经验丰富的系统集成商使用 *仅*. 此选项应 *从* 用于开发环境。 如果不正确使用此可选参数，则可能会在代码执行期间导致错误。

## 安装应用程序

* [使用命令行进行安装](../advanced.md)
