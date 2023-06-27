---
title: 设置umask（可选）
description: 通过限制文件Magento Open Source权限，提高Adobe Commerce或系统内部部署的安全状态。
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# 设置umask（可选）

Web服务器组必须具有对文件系统中特定目录的写入权限；但是，您可能希望获得更严格的安全性，特别是在生产环境中。 我们为您提供了灵活性，让您能够使用 [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

我们的解决方案是让您可以选择创建名为的文件 `magento_umask` 在应用程序根目录中，该目录限制Web服务器组和其他所有用户的权限。

>[!NOTE]
>
>我们建议仅在单用户或共享托管系统上更改umask。 如果您有专用应用程序服务器，则组必须具有对文件系统的写访问权限；umask会从组中删除写访问权限。

默认umask(不含 `magento_umask` specified)为 `002`，这意味着：

* 775 for directories ，即用户完全控制，组完全控制，并允许每个人遍历目录。 共享托管提供程序通常需要这些权限。

* 664表示文件可由用户写入，可由组写入，对于其他所有人则为只读

一个常见建议是使用值 `022` 在 `magento_umask` 文件，这意味着：

* 755 for directories：用户可完全控制，其他人都可以遍历目录。
* 644 for files：用户的读写权限，其他所有人的只读权限。

要设置 `magento_umask`：

1. 在命令行终端中，以 [文件系统所有者](../prerequisites/file-system/overview.md).
1. 导航到应用程序安装目录：

   ```bash
   cd <Application install directory>
   ```

1. 使用以下命令创建一个名为的文件 `magento_umask` 并编写 `umask` 值。

   ```bash
   echo <desired umask number> > magento_umask
   ```

   现在，您应该有一个名为的文件 `magento_umask` 在 `<Magento install dir>` 唯一内容为 `umask` 数字。

1. 注销并重新登录作为 [文件系统所有者](../prerequisites/file-system/overview.md) 以应用更改。
