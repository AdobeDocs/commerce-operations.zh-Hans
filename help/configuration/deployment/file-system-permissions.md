---
title: 文件系统访问权限
description: 请参阅如何为开发和生产系统设置Commerce应用程序文件系统的所有者或所有者。
feature: Configuration, Roles/Permissions
exl-id: 95b27db9-5247-4f58-a9af-1590897d73db
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# 文件系统访问权限

本节讨论如何为开发和生产系统设置Commerce文件系统的所有者或所有者。 在继续之前，请查看[文件系统所有权和权限概述](../../installation/prerequisites/file-system/overview.md)中讨论的概念。

本主题重点介绍Commerce开发和生产系统。 如果要安装Commerce，请参阅[设置安装前的所有权和权限](../../installation/prerequisites/file-system/configure-permissions.md)。

后面的部分讨论了对一个或两个文件系统所有者的要求。 这意味着：

- **一个用户** — 通常在共享托管提供程序上需要，该提供程序只允许你访问服务器上的一个用户。此用户可以登录，使用FTP传输文件，并且此用户还运行Web服务器。

- **两个用户** — 如果您运行自己的Commerce服务器，我们建议使用两个用户：一个用于传输文件和运行命令行实用工具，另一个用于Web服务器软件。 如果可能，这是最好的，因为它更安全。

  相反，您拥有单独的用户：

   - 运行Admin和storefront的Web服务器用户。

   - _命令行用户_，这是可用于登录到服务器的本地用户帐户。 此用户运行Commerce cron作业和命令行实用程序。

## 共享托管的生产文件系统所有权（一个用户）

要使用单一所有者设置，您必须以运行Web服务器的相同用户身份登录到Commerce服务器。 这是共享托管的典型做法。

由于拥有一位文件系统所有者不太安全，因此我们建议您尽可能在专用服务器上将Commerce在生产环境中部署，而不是在共享主机上部署。

### 为默认或开发人员模式设置一个所有者

在默认或开发人员模式下，用户必须可以写入以下目录：

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- 任何其他静态资源
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

您可以使用命令行或共享托管提供程序提供的文件管理器应用程序来设置这些权限。

### 为生产模式设置一个所有者

准备好将站点部署到生产环境时，您应该从以下目录中的文件删除写访问权限，以提高安全性：

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- 任何其他静态资源
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

要更新组件、安装新组件或升级Commerce软件，上述所有目录都必须是读写目录。

#### 将代码文件和目录设为只读

要删除Web服务器用户组中文件和目录的写入权限：

1. 登录到您的Commerce服务器。

1. 转到Commerce安装目录。

1. 更改为生产模式。

   ```bash
   bin/magento deploy:mode:set production
   ```

1. 删除对以下目录的写入权限。

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. 使命令行工具可执行。

   ```bash
   chmod u+x bin/magento
   ```

#### 使代码文件和目录可写

要使文件和目录可写，以便您可以更新组件并升级Commerce软件，请执行以下操作：

1. 登录到您的Commerce服务器。
1. 转到Commerce安装目录。
1. 输入以下命令：

   ```bash
   chmod -R u+w .
   ```

### 可选设置`magento_umask`

请参阅[安装指南](../../installation/next-steps/set-umask.md)中的&#x200B;_可选设置umask_。

## 专用托管的生产文件系统所有权（两个用户）

如果您使用自己的服务器（包括托管提供商的专用服务器设置），则有两个用户：

- 运行管理员和店面的&#x200B;**Web服务器用户**。

  Linux系统通常不为此用户提供Shell；您无法以Web服务器用户身份登录Commerce服务器或切换到该用户。

- 您以或切换身份登录到Commerce服务器的&#x200B;**命令行用户**。

  Commerce使用此用户运行CLI命令和cron。

  >[!INFO]
  >
  >命令行用户也称为&#x200B;_文件系统所有者_。

由于这些用户需要访问相同的文件，因此我们建议您创建他们同时属于的[共享组](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group)。 以下过程假定您已完成此操作。

请参阅以下部分之一：

- 开发人员模式或默认模式下的两个文件系统所有者
- 两个处于生产模式的文件系统所有者

### 为默认或开发人员模式设置两个所有者

在开发模式和默认模式下，以下目录中的文件必须可以由用户同时写入：

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

设置目录上的[`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/)位，以便权限始终从父目录继承。

>[!INFO]
>
>`setgid`仅适用于目录，_不适用于_&#x200B;文件。

此外，这些目录应可由Web服务器组写入。 由于这些目录中可能存在内容，因此应递归添加权限。

#### 设置权限和`setgid`

要为开发人员模式设置`setgid`和权限：

1. 以文件系统所有者的身份登录Commerce服务器或切换到文件系统所有者。
1. 按照显示的顺序输入以下命令：

   ```bash
   cd <magento_root>
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### 两个处于生产模式的文件系统所有者

准备好将站点部署到生产环境时，您应该从以下目录中的文件删除写访问权限，以提高安全性：

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- 任何其他静态资源
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### 将代码文件和目录设为只读

要从Web服务器用户组中删除对文件和目录的可写权限：

1. 登录到您的Commerce服务器。
1. 转到Commerce安装目录。
1. 作为文件系统所有者，输入以下命令以更改为生产模式：

   ```bash
   bin/magento deploy:mode:set production
   ```

1. 以具有`root`权限的用户身份输入以下命令：

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### 使代码文件和目录可写

要使文件和目录可写，以便您可以更新组件并升级Commerce软件，请执行以下操作：

1. 登录到您的Commerce服务器。
1. 转到Commerce安装目录。
1. 输入以下命令：

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
