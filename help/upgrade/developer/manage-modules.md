---
title: 管理模块和扩展（开发人员）
description: 使用命令行界面和编辑器包管理器管理Adobe Commerce模块和扩展。
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 3%

---

# 管理模块和扩展

参与开发的开发人员通过在Adobe Commerce `composer.json`文件中指定其版本来升级模块和扩展。 如果您不是参与开发人员，请参阅[执行升级](../implementation/perform-upgrade.md)。

您可以将`require`节添加到`composer.json`文件，也可以按如下方式使用`composer require`命令：

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

## 使用`composer require`命令

命令用法：

```bash
composer require <vendor>/<name>:<version>
```

例如：

```bash
composer require example/module:1.0.0
```

Composer正在更新依赖项并安装模块，请稍候。

## 向composer.json文件中添加`require`部分

1. 在文本编辑器中打开`composer.json`。

1. 添加`require`分区。

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. 保存对`composer.json`文件所做的更改并退出文本编辑器。

1. 解决依赖关系并将精确版本写入`composer.lock`文件。

   ```bash
   composer update
   ```

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
