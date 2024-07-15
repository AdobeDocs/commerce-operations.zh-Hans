---
title: 文件所有权和权限
description: 了解在使用Adobe Commerce的内部安装时文件系统权限的重要性。
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# 文件所有权和权限

在开发环境中保护您的Adobe Commerce安装非常重要，这样有助于防止出现与未经授权的人员或流程访问（并可能损害）您的系统相关的问题。 使用以下文件系统所有权和权限指南来保护您的安装。

## 文件系统所有者

文件系统所有者是拥有并保留对文件系统中文件的写入权限的用户。

有两种类型的文件系统所有者：

- **与单个用户共享托管**

  通过共享托管提供程序，您可以作为一位用户登录到应用程序服务器。 作为单个用户，您可以登录、使用FTP传输文件以及运行Web服务器。 您可以选择设置[`umask`](#restrict-access-with-a-umask)以进一步限制访问，尤其是在生产环境中。

- **与两个用户进行私有托管**

  如果管理应用程序服务器，则专用托管会很有用。 每个用户都有特定的责任：

   - _Web服务器用户_&#x200B;运行管理员和店面。

   - _命令行用户_&#x200B;运行cron作业和命令行实用工具。

  两个用户都需要对文件系统具有相同的权限，因此最好使用[共享组](configure-permissions.md#set-ownership-and-permissions-for-two-users)并设置[`umask`](#restrict-access-with-a-umask)。

### 使用umask限制访问

要加强安全性，特别是在共享托管系统上的生产环境中，您可以使用`umask`来限制访问。 `umask`（也称为&#x200B;_文件系统创建掩码_）是一组位，用于控制如何为新创建的文件设置文件权限。

>[!WARNING]
>
>文件系统安全是复杂而重要的。 我们强烈建议您在决定要设置的权限级别之前，咨询经验丰富的系统管理员或网络管理员。 我们为您提供了一种可供使用的机制，但创建权限策略是您的责任。

Adobe Commerce使用三位默认掩码： `002`。 从UNIX缺省值666（文件）和777（目录）中减去缺省掩码。

例如：

- 目录&#x200B;**的** 775 — 用户可完全控制，组可完全控制，并允许每个人遍历目录。 共享托管提供程序通常需要这些权限。

- **664用于文件** — 用户可写，组可写，其他所有人只读。

有关创建`magento_umask`文件的详细信息，请参阅[设置umask](../../next-steps/set-umask.md)。

## 权限、所有权和应用程序模式

当您使用不同的Adobe Commerce应用程序模式时，我们建议您使用不同的权限和所有权：

- 默认
- 开发人员
- 生产

请参阅&#x200B;_配置指南_&#x200B;中的[关于模式](../../../configuration/bootstrap/application-modes.md)。

我们在&#x200B;_配置指南_&#x200B;的[文件系统访问权限](../../../configuration/deployment/file-system-permissions.md)中进一步讨论权限建议。

>[!TIP]
>
>在安装Adobe Commerce之前，请查看[配置文件所有权和权限](configure-permissions.md)。
