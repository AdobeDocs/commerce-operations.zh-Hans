---
title: 设置操作模式
description: 阅读有关设置Adobe Commerce操作模式的信息。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---


# 设置操作模式

{{file-system-owner}}

为了提高安全性和易用性，我们添加了一个命令，用于切换 [应用模式](../bootstrap/application-modes.md) 从开发人员到生产，反之亦然。

生产模式具有更好的性能，因为静态视图文件填充在 `pub/static` 目录和由于代码编译而导致。

>[!INFO]
>
>在版本2.0.6及更高版本中，当您在默认、开发和生产模式之间切换时，Commerce不会明确设置文件或目录权限。 与其他模式不同，开发人员和生产模式在 `env.php` 文件。 云基础架构上的Adobe Commerce仅支持生产和维护模式。
>
>请参阅 [商业在开发和生产中的所有权和权限](../deployment/file-system-permissions.md).

当您更改为开发人员或生产模式时，我们会清除以下目录的内容：

```terminal
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

例外：

- `.htaccess` 未删除文件
- `pub/static` 包含指定静态内容版本的文件；未删除此文件

>[!INFO]
>
>默认情况下，商务使用 `var` 用于存储缓存、日志和编译代码的目录。 您可以自定义此目录，但在本指南中，假定该目录为 `var`.

## 显示当前模式

要执行此操作，最简单的方法是将此命令作为 [文件系统所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html). 如果您已共享托管，则这是您的提供商授予您登录服务器的用户。 如果您有专用服务器，则它通常是商务服务器上的本地用户帐户。

命令用法：

```bash
bin/magento deploy:mode:show
```

将显示一条与以下内容类似的消息：

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

其中：

- **`{mode}`** 可以是 `default`, `developer`或 `production`

## 更改模式

命令用法：

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

其中：

- **`{mode}`** 必需；它可以 `developer` 或 `production`

- **`--skip-compilation`** 是用于跳过的可选参数 [代码编译](../cli/code-compiler.md) 更改为生产模式时。

示例如下。

### 更改生产模式

```bash
bin/magento deploy:mode:set production
```

与以下内容类似的消息显示：

```terminal
Enabled maintenance mode
Requested languages: en_US
=== frontend -> Magento/luma -> en_US ===
... more ...
Successful: 1884 files; errors: 0
---

=== frontend -> Magento/blank -> en_US ===
... more ...
Successful: 1828 files; errors: 0
---

=== adminhtml -> Magento/backend -> en_US ===
... more ...
---

=== Minify templates ===
... more ...
Successful: 897 files modified
---

New version of deployed files: 1440461332
Static content deployment complete
Gathering css/styles-m.less sources.
Successfully processed LESS and/or [Sass](https://glossary.magento.com/sass) files
[CSS](https://glossary.magento.com/css) deployment complete
Generated classes:
      Magento\Sales\Api\Data\CreditmemoCommentInterfacePersistor
      Magento\Sales\Api\Data\CreditmemoCommentInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoCommentSearchResultInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoComment\Repository
      Magento\Sales\Api\Data\CreditmemoItemInterfacePersistor
      ... more ...
Compilation complete
Disabled maintenance mode
Enabled production mode.
```

### 更改为开发人员模式

从生产模式更改为开发人员模式时，应清除生成的类和对象管理器实体（如代理），以防止出现意外错误。 这样做后，您可以更改模式。 请执行以下步骤：

1. 如果从生产模式更改为开发人员模式，请删除 `generated/code` 和 `generated/metadata` 目录：

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. 设置模式：

   ```bash
   bin/magento deploy:mode:set developer
   ```

   将显示以下消息：

   ```terminal
   Enabled developer mode.
   ```

### 更改为默认模式

```bash
bin/magento deploy:mode:set default
```

将显示以下消息：

```terminal
Enabled default mode.
```

### 从任意位置运行CLI命令

[从任意位置运行CLI命令](../cli/config-cli.md#config-install-cli-first).

如果尚未添加 `<Commerce-install-directory>/bin` 到系统 `PATH`，则单独运行命令时可能会出错。
