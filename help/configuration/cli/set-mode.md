---
title: 设置操作模式
description: 阅读有关设置Adobe Commerce操作模式的信息。
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# 设置操作模式

{{file-system-owner}}

为了提高安全性和易用性，我们添加了一个命令来切换 [应用程序模式](../bootstrap/application-modes.md) 从开发人员到生产环境，反之亦然。

生产模式具有更好的性能，因为静态视图文件填充在 `pub/static` 目录和由于代码编译而产生。

>[!INFO]
>
>在2.0.6版及更高版本中，在默认、开发和生产模式之间切换时，Commerce不会明确设置文件或目录权限。 与其他模式不同，开发人员和生产模式在 `env.php` 文件。 云基础架构上的Adobe Commerce仅支持生产和维护模式。
>
>请参阅 [开发和生产中的商业所有权和权限](../deployment/file-system-permissions.md).

当您更改为开发人员模式或生产模式时，我们将清除以下目录的内容：

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
>默认情况下，Commerce使用 `var` 目录来存储缓存、日志和编译的代码。 您可以自定义此目录，但在本指南中，假定为 `var`.

## 显示当前模式

最简单的方法是以 [文件系统所有者](../../installation/prerequisites/file-system/overview.md). 如果您共享了主机，则这是您的提供商为您提供的用于登录到服务器的用户。 如果您有专用服务器，它通常是Commerce服务器上的本地用户帐户。

命令用法：

```bash
bin/magento deploy:mode:show
```

此时将显示一条与以下内容类似的消息：

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

其中：

- **`{mode}`** 可以是 `default`， `developer`，或 `production`

## 更改模式

命令用法：

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

其中：

- **`{mode}`** 必需；它可以 `developer` 或 `production`

- **`--skip-compilation`** 是可用于跳过的可选参数 [代码编译](../cli/code-compiler.md) 当您更改为生产模式时。

示例如下。

### 更改为生产模式

```bash
bin/magento deploy:mode:set production
```

与以下内容类似的消息：

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
Successfully processed LESS and/or Sass files
CSS deployment complete
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

从生产模式更改为开发人员模式时，应清除生成的类和Object Manager实体（如代理）以防止意外错误。 完成此操作后，您可以更改模式。 请使用以下步骤：

1. 如果您要从生产模式更改为开发人员模式，请删除 `generated/code` 和 `generated/metadata` 目录：

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

### 从任何位置运行CLI命令

[从任何位置运行CLI命令](../cli/config-cli.md#config-install-cli-first).

如果您尚未添加 `<Commerce-install-directory>/bin` 到您的系统 `PATH`，则单独运行命令时可能会出错。
