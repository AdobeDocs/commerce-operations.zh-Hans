---
title: 克隆示例数据Git存储库
description: 请按照以下步骤操作，通过克隆Git存储库来安装Adobe Commerce并Magento Open Source示例数据。
source-git-commit: 3692dcfd5b50c2f036b005d40a22db061b9ea5fd
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 克隆示例数据Git存储库

本主题讨论如果克隆了Magento Open SourceGitHub存储库，则如何克隆和添加示例数据。 此方法仅适用于参与开发人员(即计划参与Magento Open Source代码库的开发人员)。

如果您不是参与开发人员，请选择页面左侧目录中显示的其他选项之一。

参与开发人员可以使用此方法安装示例数据 *仅* 如果为true:

* 您使用Magento Open Source
* 您 [克隆了GitHub存储库](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>您可以在 `develop` 分支（更新）或已释放的分支(例如 `2.4` （更稳定）。 我们建议您使用已发布的分支，因为它更稳定。 如果您向存储库提供代码并且需要最新的代码，请使用 `develop` 分支。 无论您选择哪个分支，都必须 [克隆](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) Magento Open SourceGitHub存储库的相应分支。 例如， `develop` 分支可用 *仅* Magento Open Source `develop` 分支。

## 克隆示例数据存储库

本节讨论如何通过克隆示例数据存储库来安装示例数据。 您可以通过以下任何方式克隆示例数据存储库：

* 克隆 [SSH协议](#clone-with-ssh)
* 克隆 [HTTPS协议](#clone-with-https)

### 使用SSH克隆

要使用SSH协议克隆示例数据GitHub存储库，请执行以下操作：

1. 在Web浏览器中，转到 [示例数据存储库](https://github.com/magento/magento2-sample-data).
1. 在分支名称旁边，单击 **SSH** 列表。
1. 单击 **复制到剪贴板**

   下图显示了一个示例。

   ![使用SSH克隆GitHub存储库](../../assets/installation/install_mage2_clone-ssh.png)

1. 更改为Web服务器的docroot目录。

   通常，对于乌班图来说 `/var/www` 而对于CentOS，它 `/var/www/html`.

1. 输入 `git clone` 并粘贴您之前获取的值。

   示例如下：

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. 等待存储库在您的服务器上克隆。

   >[!NOTE]
   >
   >如果显示以下错误，请确保 [共享SSH密钥](https://docs.github.com/articles/generating-ssh-keys/) 和GitHub:<br>

   ```terminal
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. 确保签出与从主存储库使用的分支对应的示例数据存储库的分支 `magento2` 存储库。

   例如：

   如果您使用 `2.4-develop` Magento Open SourceGitHub存储库的分支，示例数据分支应为 `2.4-develop`.

   要签出正确的分支，请从示例数据存储库的根目录中运行以下命令(假定您需要 `2.4-develop` 分支):

   ```bash
   git checkout 2.4-develop
   ```

1. 更改为 `<app_root>`.
1. 输入以下命令，在您克隆的文件之间创建符号链接，以便样例数据正常工作：

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. 等待命令完成。

1. 请参阅 [设置文件系统权限和所有权](#set-file-system-ownership-and-permissions).

1. 运行以下命令：

   ```bash
   bin/magento setup:upgrade
   ```

### 使用HTTPS克隆

要使用HTTPS协议克隆示例数据GitHub存储库，请执行以下操作：

1. 在Web浏览器中，转到 [示例数据存储库](https://github.com/magento/magento2-sample-data).
1. 在页面右侧的 **克隆URL** 字段，单击 **HTTPS**.
1. 单击 **复制到剪贴板**.

   下图显示了一个示例。

   ![使用HTTPS克隆GitHub存储库](../../assets/installation/install_mage2_clone-https.png)

1. 更改为Web服务器的docroot目录。

   通常，对于乌班图来说 `/var/www` 而对于CentOS，它 `/var/www/html`.

1. 输入 `git clone` 并粘贴您之前获取的值。

   示例如下：

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. 等待存储库在您的服务器上克隆。
1. 确保签出与从主存储库使用的分支对应的示例数据存储库的分支 `magento2` 存储库。

   例如：

   如果您使用 `2.4-develop` Magento Open SourceGitHub存储库的分支，示例数据分支应为 `2.4-develop`.

   要签出正确的分支，请从示例数据存储库的根目录中运行以下命令(假定您需要 `2.4-develop` 分支):

   ```bash
   git checkout 2.4-develop
   ```

1. 更改为 `<magento_root>`.
1. 输入以下命令，在您克隆的文件之间创建符号链接，以便样例数据正常工作：

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

   例如，

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="/var/www/magento2"
   ```

1. 等待命令完成。
1. 请参阅下一节。

>[!WARNING]
>
>如果正在安装示例数据 *after* 安装Adobe Commerce或Magento Open Source时，还必须运行以下命令来更新数据库和模式：
>
>
```bash
><magento_root>/bin/magento setup:upgrade
>```

## 设置文件系统所有权和权限

因为 `php build-sample-data.php` 脚本会在示例数据存储库和您的Magento Open Source存储库之间创建符号链接，您必须在示例数据存储库中设置文件系统权限和所有权。 未能执行此操作会导致访问店面时出错。

要在示例数据存储库中设置文件系统权限和所有权，请执行以下操作：

1. 更改为示例数据克隆目录。
1. 设置所有权：

   ```bash
   chown -R :<your web server group name> .
   ```

   典型示例：

   * CentOS: `chown -R :apache .`

   * 乌本图： `chown -R :www-data .`

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
