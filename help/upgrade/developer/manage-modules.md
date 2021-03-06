---
title: 管理模块和扩展（开发人员）
description: 使用命令行界面和编辑器包管理器管理Adobe Commerce和Magento Open Source模块和扩展。
source-git-commit: 3432ba8640a82269cb725b8b15854f20c270b1e3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 管理模块和扩展

供稿开发人员通过在Adobe Commerce或Magento Open Source中指定其版本来升级模块和扩展 `composer.json` 文件。 如果您不是参与开发人员，请参阅 [执行升级](../implementation/perform-upgrade.md).

您可以添加 `require` 的 `composer.json` 文件，或者您可以使用 `composer require` 命令：

{{$include /help/_includes/server-login.md}}

您有以下选项：

## 获取可用的模块版本

命令用法：

```bash
composer show --all <vendor>/<name>
```

例如：

```bash
composer show --all example/module
```

## 使用 `composer require` 命令

命令用法：

```bash
composer require <vendor>/<name>:<version>
```

例如：

```bash
composer require example/module:1.0.0
```

编辑器更新依赖项并安装模块时等待。

## 添加 `require` 部分到composer.json文件

1. 打开 `composer.json` 在文本编辑器中。

1. 添加 `require` 中。

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. 保存对 `composer.json` 并退出文本编辑器。

1. 解决依赖关系，并将确切的版本写入 `composer.lock` 文件。

   ```bash
   composer update
   ```
