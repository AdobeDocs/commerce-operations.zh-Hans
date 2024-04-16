---
title: 卸载或重新安装Adobe Commerce
description: 按照以下步骤卸载并重新安装Adobe Commerce的内部安装。
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# 卸载或重新安装Adobe Commerce

在使用这些命令之前，您必须 [安装应用程序](../tutorials/install.md).

## 更新应用程序

要更新应用程序，请执行以下操作：

* 如果是从归档文件安装软件，或者使用的是“composer-create-project”，请参见 [升级指南](../../upgrade/overview.md).
* 如果您是参与开发人员(即 `git clone`)，请参见 [更新应用程序](../../upgrade/developer/git-installs.md).

## 重新安装应用程序

从命令行重新安装应用程序的方式取决于您的角色：

* 如果是从归档文件安装软件，或者使用的是“composer-create-project”，请参阅 [更新安装依赖关系](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* 如果您是参与开发人员(即，您已开始使用 `git clone`)，请参见 [更新安装依赖关系](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## 卸载应用程序

卸载应用程序将删除并还原数据库，删除部署配置，并清除以下目录 `var`.

要卸载应用程序，请输入以下命令：

```bash
bin/magento setup:uninstall
```

将显示以下消息以确认卸载成功：

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## （可选）保留生成的文件

默认情况下， `bin/magento setup:upgrade` 清除编译后的代码和缓存。 通常，您使用 `bin/magento setup:upgrade` 更新组件，每个组件可能需要不同的编译类。

但是，在某些情况下（特别是部署到生产环境），您可能希望避免清除编译的代码，因为这样可能需要一些时间。 （缓存仍被清除。） 更新数据库架构和数据 *不含* 清除已编译的代码，请输入：

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>可选 `--keep-generated` 选项应由经验丰富的系统集成人员在有限的情况下使用 *仅限*. 此选项应 *从不* 在开发环境中使用。 不正确使用此可选参数可能会导致代码执行过程中出现错误。

## 安装应用程序

* [使用命令行安装](../advanced.md)
