---
title: 文件所有权和权限
description: 了解使用Adobe Commerce和Magento Open Source的本地安装时文件系统权限的重要性。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# 文件所有权和权限

在开发环境中保护您的Adobe Commerce或Magento Open Source安装，以帮助防止与未经授权的人员或进程访问您的系统（并可能对您的系统造成伤害）相关的问题，这一点非常重要。 使用以下文件系统所有权和权限准则来保护您的安装。

## 文件系统所有者

文件系统所有者是拥有和拥有文件系统中文件的写入权限的用户。

文件系统所有者有两种类型：

- **与单个用户共享托管**

   共享托管提供程序允许您以一个用户身份登录应用程序服务器。 作为单个用户，您可以登录、使用FTP传输文件，并运行Web服务器。 您可以选择将 [`umask`](#restrict-access-with-a-umask) 以进一步限制访问，特别是在生产环境中。

- **由两个用户进行私有托管**

   如果您管理应用程序服务器，则专用托管会非常有用。 每个用户都有特定的责任：

   - 的 _Web服务器用户_ 运行管理员和店面。

   - 的 _命令行用户_ 运行cron作业和命令行实用程序。
   两个用户都需要对文件系统拥有相同的权限，因此最好使用 [共享组](configure-permissions.md#set-ownership-and-permissions-for-two-users) 并设置 [`umask`](#restrict-access-with-a-umask).

### 使用umask限制访问

要加强安全性，特别是在共享托管系统上的生产环境中，您可以使用 `umask` 以限制访问。 A `umask` — 也称为a _文件系统创建掩码_ — 一组位，用于控制如何为新创建的文件设置文件权限。

>[!WARNING]
>
>文件系统安全性是复杂而重要的。 我们强烈建议您先咨询经验丰富的系统管理员或网络管理员，然后再确定要设置的权限级别。 我们为您提供了一种机制供您使用，但您有责任创建权限策略。

Adobe Commerce和Magento Open Source使用三位默认掩码： `002`. 从UNIX默认值中减去默认掩码：文件为666，目录为777。

例如：

- **目录775** — 由用户完全控制，由组完全控制，并允许每个人遍历目录。 共享托管提供程序通常需要这些权限。

- **文件为664** — 用户可写，组可写，其他所有人只读。

有关创建 `magento_umask` 文件，请参阅 [设置变音](../../next-steps/set-umask.md).

## 权限、所有权和应用程序模式

当您使用不同的Adobe Commerce和Magento Open Source应用程序模式时，我们建议您使用不同的权限和所有权：

- 默认
- 开发人员
- 生产

请参阅 [关于模式](../../../configuration/bootstrap/application-modes.md) 在 _配置指南_.

我们在 [文件系统访问权限](../../../configuration/deployment/file-system-permissions.md) 在 _配置指南_.

>[!TIP]
>
>在安装Adobe Commerce或Magento Open Source之前，请查看 [配置文件所有权和权限](configure-permissions.md).
