---
title: 下载示例数据编辑器包
description: 按照以下步骤使用编辑器PHP包管理器安装Adobe Commerce示例数据。
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# 下载示例数据编辑器包

本节讨论如何安装示例数据(如果通过以下任一方式获得Adobe Commerce软件)：

* 已从下载压缩的档案 `https://magento.com/tech-resources/download`.

  如果您从GitHub下载了存档，则此方法不起作用，因为 `composer.json` 文件不包含 `repo.magento.com` URL。

* 已使用 `composer create-project`

您可以使用此方法获取Adobe Commerce的示例数据，但必须使用相同的示例数据 [身份验证密钥](../prerequisites/authentication-keys.md) 用于安装该应用程序的应用程序。

>[!NOTE]
>
>如果您遇到错误，例如 `Could not find package...` 或 `...no matching package found...`，请确保您的命令中没有键入任何错误。 如果您仍遇到错误，则可能无权访问正确的编辑器存储库，尤其是如果您使用的是Adobe Commerce，更是如此。 联系人 [Adobe Commerce支持](https://support.magento.com/hc/en-us) 以寻求帮助。

您可以使用Composer在安装应用程序之前或之后安装示例数据；但是， [其他任务](remove-or-update.md).

如果您是参与开发人员，请参阅 [通过克隆存储库进行安装](git-repositories.md).

>[!WARNING]
>
>如果您的应用程序设置为以下值，则不安装示例数据 [生产模式](../../configuration/bootstrap/application-modes.md#production-mode). 切换到 [开发者模式](../../configuration/bootstrap/application-modes.md#developer-mode) 首先。 在生产模式下安装示例数据 [失败](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

要使用命令行安装示例数据，请输入以下命令作为文件系统所有者 `<app_root>` 目录：

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>如果您正在安装示例数据 _之后_ 安装应用程序时，还必须运行以下命令以更新中的数据库和模式 `<app_root>` 目录：

```bash
bin/magento setup:upgrade
```

您需要执行以下操作 [身份验证](../prerequisites/authentication-keys.md) 以完成操作。

## 身份验证错误

可能会显示以下身份验证错误：

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

如果显示错误，请转到应用程序安装目录并运行 `composer update`，提示您输入 [身份验证密钥](../prerequisites/authentication-keys.md).

## 完成示例数据安装

{{$include /help/_includes/sample-data-complete.md}}
