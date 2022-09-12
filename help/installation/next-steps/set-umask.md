---
title: 设置变调（可选）
description: 通过限制文件系统权限，改善Adobe Commerce或Magento Open Source本地安装的安全态势。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 设置变调（可选）

Web服务器组必须对文件系统中的某些目录具有写入权限；但是，您可能希望获得更严格的安全性，尤其是在生产环境中。 我们为您提供了使用 [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

我们的解决方案是让您可以选择创建一个名为 `magento_umask` 在限制web服务器组和其他所有人的权限的应用程序根目录中。

>[!NOTE]
>
>我们建议仅在一个用户或共享托管系统上更改umask。 如果您有专用应用程序服务器，则组必须具有对文件系统的写访问权限；umask会从组中删除写访问权限。

默认的umask(无 `magento_umask` 指定) `002`，表示：

* 775，表示用户完全控制，组完全控制，并且允许每个人遍历目录。 共享托管提供程序通常需要这些权限。

* 664，表示用户可写，组可写，其他每个人只读

常见建议是使用 `022` 在 `magento_umask` 文件，这表示：

* 目录为755:完全控制用户，其他所有人都可以遍历目录。
* 文件为644:用户的读写权限，以及其他每个人的只读权限。

要设置 `magento_umask`:

1. 在命令行终端中，以 [文件系统所有者](../prerequisites/file-system/overview.md).
1. 导航到应用程序安装目录：

   ```bash
   cd <Application install directory>
   ```

1. 使用以下命令创建名为 `magento_umask` 写 `umask` 值。

   ```bash
   echo <desired umask number> > magento_umask
   ```

   您现在应该有一个名为 `magento_umask` 在 `<Magento install dir>` 其中唯一的内容是 `umask` 数字。

1. 注销并重新登录为 [文件系统所有者](../prerequisites/file-system/overview.md) 以应用更改。
