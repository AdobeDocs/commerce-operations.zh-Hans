---
title: 克隆示例数据Git存储库
description: 按照以下步骤通过克隆Git存储库来安装Adobe Commerce示例数据。
exl-id: 748eee30-2821-457d-9c1c-62ede8bc0510
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%

---

# 克隆示例数据Git存储库

本主题讨论如何在克隆Magento Open SourceGitHub存储库时克隆和添加示例数据。 此方法仅适用于参与开发的开发人员(即计划参与Magento Open Source代码库的开发人员)。

如果您不是参与开发人员，请选择页面左侧目录中显示的其他选项之一。

参与开发的开发人员可以使用此方法来安装示例数据 *仅限* 如果满足以下条件：

* 您使用Magento Open Source
* 您 [克隆了GitHub存储库](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>您可以将示例数据与 `develop` 分支（更新）或已发布的分支(例如 `2.4` （更稳定）。 我们建议您使用已发布的分支，因为它更稳定。 如果您要向存储库贡献代码，并且需要最新的代码，请使用 `develop` 分支。 无论您选择哪个分支，您都必须 [克隆](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) Magento Open SourceGitHub存储库的相应分支。 例如，的示例数据 `develop` 分支可使用 *仅限* 使用Magento Open Source `develop` 分支。

## 克隆示例数据存储库

本节讨论如何通过克隆示例数据存储库来安装示例数据。 您可以通过以下任一方式克隆示例数据存储库：

* 克隆 [SSH协议](#clone-with-ssh)
* 克隆 [HTTPS协议](#clone-with-https)

### 使用SSH进行克隆

要使用SSH协议克隆示例数据GitHub存储库，请执行以下操作：

1. 在Web浏览器中，转到 [示例数据存储库](https://github.com/magento/magento2-sample-data).
1. 在分支名称旁边，单击 **SSH** 从名单上。
1. 单击 **复制到剪贴板**

   下图显示了一个示例。

   ![使用SSH克隆GitHub存储库](../../assets/installation/install_mage2_clone-ssh.png)

1. 转到Web服务器的docroot目录。

   通常，对于Ubuntu，它是 `/var/www` 对于CentOS来说 `/var/www/html`.

1. 输入 `git clone` 并粘贴您之前获得的值。

   下面是一个示例：

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. 等待存储库在您的服务器上克隆。

   >[!NOTE]
   >
   >如果显示以下错误，请确保 [已共享您的SSH密钥](https://docs.github.com/articles/generating-ssh-keys/) 使用GitHub：<br>

   ```terminal
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. 确保您从主存储库中签出与所用分支对应的示例数据存储库分支。 `magento2` 存储库。

   例如：

   如果您使用 `2.4-develop` Magento Open SourceGitHub存储库的分支，示例数据分支应为 `2.4-develop`.

   要检查正确的分支，请从示例数据存储库的根目录中运行以下命令(假设您需要 `2.4-develop` 分支)：

   ```bash
   git checkout 2.4-develop
   ```

1. 更改为 `<app_root>`.
1. 输入以下命令，在您克隆的文件之间创建符号链接，以使示例数据正常工作：

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. 等待命令完成。

1. 请参阅 [设置文件系统权限和所有权](#set-file-system-ownership-and-permissions).

1. 运行以下命令：

   ```bash
   bin/magento setup:upgrade
   ```

### 使用HTTPS进行克隆

要使用HTTPS协议克隆示例数据GitHub存储库，请执行以下操作：

1. 在Web浏览器中，转到 [示例数据存储库](https://github.com/magento/magento2-sample-data).
1. 在页面的右侧，在 **克隆URL** 字段，请单击 **HTTPS**.
1. 单击 **复制到剪贴板**.

   下图显示了一个示例。

   ![使用HTTPS克隆GitHub存储库](../../assets/installation/install_mage2_clone-https.png)

1. 转到Web服务器的docroot目录。

   通常，对于Ubuntu，它是 `/var/www` 对于CentOS来说 `/var/www/html`.

1. 输入 `git clone` 并粘贴您之前获得的值。

   下面是一个示例：

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. 等待存储库在您的服务器上克隆。
1. 确保您从主存储库中签出与所用分支对应的示例数据存储库分支。 `magento2` 存储库。

   例如：

   如果您使用 `2.4-develop` Magento Open SourceGitHub存储库的分支，示例数据分支应为 `2.4-develop`.

   要检查正确的分支，请从示例数据存储库的根目录中运行以下命令(假设您需要 `2.4-develop` 分支)：

   ```bash
   git checkout 2.4-develop
   ```

1. 更改为 `<magento_root>`.
1. 输入以下命令，在您克隆的文件之间创建符号链接，以使示例数据正常工作：

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

   例如，

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="/var/www/magento2"
   ```

1. 等待命令完成。
1. 请参阅下一部分。

>[!WARNING]
>
>如果您正在安装示例数据 *之后* 安装Adobe Commerce时，还必须运行以下命令来更新数据库和架构：
>
>```bash
><magento_root>/bin/magento setup:upgrade
>```

## 设置文件系统所有权和权限

因为 `php build-sample-data.php` script在示例数据存储库和Magento Open Source存储库之间创建符号链接，您必须在示例数据存储库中设置文件系统权限和所有权。 否则，会导致访问店面时出现错误。

要对示例数据存储库设置文件系统权限和所有权，请执行以下操作：

1. 切换到示例数据克隆目录。
1. 设置所有权：

   ```bash
   chown -R :<your web server group name> .
   ```

   典型示例：

   * CentOS： `chown -R :apache .`

   * Ubuntu： `chown -R :www-data .`

1. 设置权限：

   ```bash
   find . -type d -exec chmod g+ws {} +
   ```

1. 清除静态文件：

   ```bash
   cd <your Magento Open Source install dir>
   ```

   ```bash
   rm -rf var/cache/* var/page_cache/* generated/*
   ```

## 完成示例数据安装

{{$include /help/_includes/sample-data-complete.md}}
