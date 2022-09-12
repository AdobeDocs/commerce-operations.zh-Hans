---
title: 配置文件所有权和权限
description: 请按照以下步骤为Adobe Commerce和Magento Open Source的本地安装配置文件系统权限。
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 配置文件所有权和权限

本主题讨论如何在安装Adobe Commerce或Magento Open Source之前为Web服务器组设置读写权限。 这是必需的，因此命令行可以将文件写入文件系统。

您使用的过程不同，具体取决于您是否使用 [共享托管](#set-permissions-for-one-user-on-shared-hosting) 并拥有一个用户，或者如果您使用 [专用服务器](#set-ownership-and-permissions-for-two-users) 有两个用户。

## 为一个用户设置共享托管权限

如果您以同样运行Web服务器的同一用户身份登录应用程序服务器，此部分将讨论如何设置安装前权限。 此类设置在共享托管环境中很常见。

要在安装应用程序之前设置权限，请执行以下操作：

1. 登录到应用程序服务器。
1. 使用您的共享托管提供商提供的文件管理器应用程序验证是否在以下目录上设置了写入权限：

   * `vendor` （编辑器或压缩的存档安装）
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * 任何其他静态资源

1. 如果您具有命令行访问权限，请按显示的顺序输入以下命令：

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} +
   ```

   ```bash
   chmod u+x bin/magento
   ```

   要（可选）在一行中输入所有命令，请输入以下内容(假定应用程序已安装在 `/var/www/html/magento2`:

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. 如果您尚未执行此操作，请通过以下方式之一获取应用程序：

   * [编辑器元包](../../composer.md)
   * [克隆存储库（仅供开发人员参与）](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. 在设置了文件系统所有权和权限后， [安装应用程序](../../advanced.md)

>[!NOTE]
>
>要在安装应用程序后进一步限制权限，您可以 [配置umask](../../next-steps/set-umask.md).

## 设置两个用户的所有权和权限

本节将讨论如何设置您自己的服务器或专用托管设置的所有权和权限。 在此类设置中，通常 *无法* 以web服务器用户身份登录或切换到。 您通常以一个用户身份登录，并以其他用户的身份运行Web服务器。

要设置两用户系统的所有权和权限，请执行以下操作：

按照显示的顺序完成以下任务：

* [关于共享组](#about-the-shared-group)
* [创建文件系统所有者并为用户提供强密码](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [查找Web服务器用户组](#find-the-web-server-user-group)
* [将文件系统所有者置于Web服务器组中](#put-the-file-system-owner-in-the-web-server-group)
* [获取软件](#get-the-software)
* [设置共享组的所有权和权限](#set-ownership-and-permissions-for-the-shared-group)

### 关于共享组

使Web服务器能够在文件系统中写入文件和目录，同时还能够维护 *所有权* 由文件系统所有者，两个用户必须位于同一组中。 这是必需的，以便两个用户都可以共享对文件（包括使用管理员或其他基于Web的实用工具创建的文件）的访问权限。

此部分讨论如何创建文件系统所有者，并将该用户置于Web服务器的组中。 如果您愿意，可以使用现有用户帐户；出于安全原因，我们建议用户使用强密码。

>[!NOTE]
>
>跳至 [查找Web服务器用户组](#find-the-web-server-user-group) 如果您计划使用现有用户帐户，则。

### 创建文件系统所有者并为用户提供强密码

本节将讨论如何创建文件系统所有者。 (文件系统所有者是 *命令行用户*.)

要在CentOS或Ubuntu上创建用户，请输入以下命令作为 `root` 权限：

```bash
adduser <username>
```

要为用户提供密码，请以用户身份输入以下命令 `root` 权限：

```bash
passwd <username>
```

按照屏幕上的提示为用户创建密码。

>[!WARNING]
>
>如果你没有 `root` 权限，则可以使用其他本地用户帐户。 确保用户具有强密码，并继续 [将文件系统所有者置于Web服务器组中](#step-3-put-the-file-system-owner-in-the-web-servers-group).

例如，创建名为 `magento_user` 并为用户提供密码，请输入：

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>由于创建此用户的目的是提供更高的安全性，因此请确保创建 [强密码](https://en.wikipedia.org/wiki/Password_strength).

### 查找Web服务器用户组

要查找Web服务器用户组，请执行以下操作：

* CentOS:

   ```bash
   grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
   ```

   或

   ```bash
   grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
   ```

通常，用户和组名称均为 `apache`.

* 乌本图： `ps aux | grep apache` 查找Apache用户，然后 `groups <apache user>` 来查找组。

通常，用户名和组名称都是 `www-data`.

### 将文件系统所有者置于Web服务器组中

要将文件系统所有者置于Web服务器的主组中（假定CentOS和Ubuntu的典型Apache组名称），请以用户身份输入以下命令 `root` 权限：

* CentOS: `usermod -a -G apache <username>`
* 乌本图： `usermod -a -G www-data <username>`

>[!NOTE]
>
>的 `-a -G` 选项很重要，因为它们会添加 `apache` 或 `www-data` as a *辅助* 群组到用户帐户，这将保留用户的 *主要* 群组。 向用户帐户添加辅助群组有助于 [限制文件所有权和权限](#set-ownership-and-permissions-for-two-users) 以确保共享组的成员只能访问某些文件。

例如，添加用户 `magento_user` 到 `apache` CentOS上的主组：

```bash
sudo usermod -a -G apache magento_user
```

要确认您的用户是Web服务器组的成员，请输入以下命令：

```bash
groups magento_user
```

以下示例结果显示了用户的主要`magento`)和辅助(`apache`)群组。

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>通常，用户名和主组名称是相同的。

要完成该任务，请重新启动Web服务器：

* 乌本图： `service apache2 restart`
* CentOS: `service httpd restart`

### 获取软件

如果您尚未执行此操作，请通过以下方式之一获取软件：

* [编辑器元包](../../composer.md)
* [克隆存储库（仅供开发人员参与）](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### 设置共享组的所有权和权限

要在安装应用程序之前设置所有权和权限，请执行以下操作：

1. 以文件系统所有者的身份登录或切换到您的应用程序服务器。
1. 按所示顺序输入以下命令：

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :<web server group> .
   ```

   ```bash
   chmod u+x bin/magento
   ```

要（可选）在一行中输入所有命令，请输入以下内容(假定应用程序已安装在 `/var/www/html/magento2` 而web服务器组名称为 `apache`:

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

在事件文件系统权限设置不正确且文件系统所有者无法更改的情况下，您可以以用户身份输入命令 `root` 权限：

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## 切换到文件系统所有者

在执行本主题中的其他任务后，输入以下命令之一以切换到该用户：

* 乌本图： `su <username>`
* CentOS: `su - <username>`

例如，

```bash
su magento_user
```
