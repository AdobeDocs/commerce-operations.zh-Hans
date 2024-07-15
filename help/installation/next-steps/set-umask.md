---
title: 设置umask（可选）
description: 通过限制文件系统权限来改进Adobe Commerce本地安装的安全状态。
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# 设置umask（可选）

Web服务器组必须具有对文件系统中特定目录的写入权限；但是，您可能希望加强安全性，特别是在生产环境中。 我们为您提供了灵活性，让您能够使用[umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)进一步限制这些权限。

我们的解决方案是让您可以选择在应用程序根目录中创建一个名为`magento_umask`的文件，以限制Web服务器组和其他所有用户的权限。

>[!NOTE]
>
>我们建议仅在单用户或共享托管系统上更改umask。 如果您有专用应用程序服务器，则组必须具有对文件系统的写入权限；umask会删除组的写入权限。

默认umask（未指定`magento_umask`）为`002`，这意味着：

* 775用于目录，这意味着用户可完全控制，组可完全控制，并允许每个人遍历目录。 共享托管提供程序通常需要这些权限。

* 664用于文件，这意味着用户可写，组可写，其他每个人以只读方式访问

一个常见建议是在`magento_umask`文件中使用值`022`，这意味着：

* 755适用于目录：用户可完全控制，其他所有人都能遍历目录。
* 644对于文件：用户的读写权限，其他所有人的只读权限。

要设置`magento_umask`：

1. 在命令行终端中，以[文件系统所有者](../prerequisites/file-system/overview.md)的身份登录到您的应用程序服务器。
1. 导航到应用程序安装目录：

   ```bash
   cd <Application install directory>
   ```

1. 使用以下命令创建名为`magento_umask`的文件并将`umask`值写入其中。

   ```bash
   echo <desired umask number> > magento_umask
   ```

   您现在应在`<Magento install dir>`中拥有名为`magento_umask`的文件，其中唯一的内容为`umask`数字。

1. 注销并以[文件系统所有者](../prerequisites/file-system/overview.md)的身份重新登录以应用更改。
