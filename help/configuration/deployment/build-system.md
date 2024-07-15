---
title: 构建系统设置
description: 了解如何将Commerce部署到构建系统中。
feature: Configuration, Build, Deploy
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# 构建系统设置

您可以有一个符合以下要求的构建系统：

- 所有Commerce代码都在与开发和生产系统相同的存储库中受源代码控制
- 确保源代码管理中包括&#x200B;_以下所有项_：

   - `app/etc/config.php`
   - `generated`目录（和子目录）
   - `pub/media`目录
   - `pub/media/wysiwyg`目录（和子目录）
   - `pub/static`目录（和子目录）

- 必须安装兼容的PHP版本
- 必须已安装Composer
- 它具有文件系统所有权和权限集，如[开发、生成和生产系统的先决条件](../deployment/technical-details.md)中所述。
- 构建系统不需要安装Commerce，但代码必须可供使用。

>[!WARNING]
>
>如果数据库连接已包含在`config.php`中，则不需要该连接；请参阅[导出配置](../cli/export-configuration.md)。 否则，需要数据库连接。

>[!INFO]
>
>构建计算机可以位于其自身的主机上，也可以位于与已安装的Commerce系统相同的主机上。

## 配置生成计算机

以下部分将讨论如何配置生成计算机。

### 安装编辑器

首先，检查是否已安装Composer：

在命令提示符下，输入以下任一命令：

- `composer --help`
- `composer list --help`

如果显示命令帮助，则说明已经安装了Composer。

如果显示错误，请使用以下步骤安装Composer。

要安装Composer：

1. 在Commerce服务器上更改为或创建一个空目录。

1. 输入以下命令：

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

有关其他安装选项，请参阅[Composer安装文档][composer]。

### 安装PHP

在[CentOS]或[Ubuntu]上安装PHP。

### 设置构建系统

要设置构建系统，请执行以下操作：

1. 以文件系统所有者的身份登录构建系统，或切换到文件系统所有者。
1. 从源代码管理中检索Commerce代码。

   如果使用Git，请使用以下命令：

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. 转到Commerce根目录并输入：

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

1. 如果使用Git，请在文本编辑器中打开`.gitignore`。
1. 以下各行以`#`字符开头，以便注释掉：

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. 将更改保存到`.gitignore`并退出文本编辑器。
1. 如果使用Git，请使用以下命令提交更改：

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   有关详细信息，请参阅[`.gitignore`引用](../reference/config-reference-gitignore.md)。

1. 生成系统应使用[默认模式](../bootstrap/application-modes.md#default-mode)或[开发人员模式](../bootstrap/application-modes.md#developer-mode)：

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>`为必填项。 它可以是`default`或`developer`。

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[乌班图]: https://help.ubuntu.com/lts/serverguide/php.html
