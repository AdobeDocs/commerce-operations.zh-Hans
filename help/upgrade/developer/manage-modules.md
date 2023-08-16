---
title: 管理模块和扩展（开发人员）
description: 使用命令行界面和编辑器包管理器管理Adobe Commerce和Magento Open Source模块及扩展。
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 012cba58b336b032b1c911539008c1fb961c2e07
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 2%

---

# 管理模块和扩展

参与升级的开发人员通过在Adobe Commerce或Magento Open Source中指定其版本来升级模块和扩展 `composer.json` 文件。 如果您不是参与开发人员，请参阅 [执行升级](../implementation/perform-upgrade.md).

您可以添加 `require` 部分至 `composer.json` 文件，或者您可以使用 `composer require` 命令如下所示：

{{$include /help/_includes/server-login.md}}

您可以选择以下选项：

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

Composer正在更新依赖项并安装模块，请稍候。

## 添加 `require` composer.json文件的部分

1. 打开 `composer.json` 在文本编辑器中。

1. 添加 `require` 部分。

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. 将更改保存到 `composer.json` 并退出文本编辑器。

1. 解决依赖关系并将确切版本写入 `composer.lock` 文件。

   ```bash
   composer update
   ```
