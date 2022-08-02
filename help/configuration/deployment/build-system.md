---
title: 构建系统设置
description: 了解如何将Commerce部署到构建系统中。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# 构建系统设置

您可以拥有一个符合以下要求的构建系统：

- 所有商务代码在与开发和生产系统相同的存储库中受源代码控制
- 确保以下所有内容均 _包含_ 在源代码管理中：

   - `app/etc/config.php`
   - `generated` 目录（和子目录）
   - `pub/media` 目录
   - `pub/media/wysiwyg` 目录（和子目录）
   - `pub/static` 目录（和子目录）

- 必须安装兼容的PHP版本
- 必须安装了编辑器
- 它具有文件系统所有权和权限集，如 [开发、构建和生产系统的先决条件](../deployment/technical-details.md).
- 构建系统不需要安装商务，但代码必须可供其使用。

>[!WARNING]
>
>如果数据库连接已包含在 `config.php`;请参阅 [导出配置](../cli/export-configuration.md). 否则，需要数据库连接。

>[!INFO]
>
>构建计算机可以位于其自身的主机上，也可以位于与已安装的商务系统相同的主机上。

## 配置生成计算机

以下部分将讨论如何配置生成计算机。

### 安装编辑器

首先，检查是否已安装编辑器：

在命令提示符下，输入以下任意命令：

- `composer --help`
- `composer list --help`

如果显示命令帮助，则表示已安装编辑器。

如果显示错误，请按照以下步骤安装编辑器。

要安装编辑器，请执行以下操作：

1. 更改为或在商务服务器上创建空目录。

1. 输入以下命令：

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

有关其他安装选项，请参阅 [编辑器安装文档][composer].

### 安装PHP

在上安装PHP [CentOS] 或 [乌本图].

### 设置构建系统

要设置构建系统，请执行以下操作：

1. 以文件系统所有者的身份登录到构建系统，或切换到。
1. 从源代码管理中检索商务代码。

   如果您使用Git，请使用以下命令：

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. 更改为商务根目录并输入：

   ```bash
   composer install
   ```

1. 等待依赖项更新。
1. 设置所有权：

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   例如，

   ```bash
   chown -R commerce-username:apache .
   ```

1. 如果您使用Git，请打开 `.gitignore` 在文本编辑器中。
1. 以下每行的开头均使用 `#` 要注释的字符：

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. 将更改保存到 `.gitignore` 并退出文本编辑器。
1. 如果使用Git，请使用以下命令提交更改：

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   请参阅 [`.gitignore` 参考](../reference/config-reference-gitignore.md) 以了解更多信息。

1. 构建系统应使用 [默认模式](../bootstrap/application-modes.md#default-mode) 或 [开发人员模式](../bootstrap/application-modes.md#developer-mode):

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` 必需。 它可以是 `default` 或 `developer`.

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[乌本图]: https://help.ubuntu.com/lts/serverguide/php.html
