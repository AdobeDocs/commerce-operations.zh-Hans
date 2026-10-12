---
title: 管理模块和扩展（开发人员）
description: 使用命令行界面和编辑器包管理器管理Adobe Commerce模块和扩展。
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
last-update: 2026-04-28
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
subfeature_v2:
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a3c0eba7bdcd8017e88bdb4df1f45d77fe4bb351
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 3%
---
# 管理模块和扩展

参与开发的开发人员通过在Adobe Commerce `composer.json`文件中指定其版本来升级模块和扩展。 如果您不是参与开发人员，请参阅[执行升级](../implementation/perform-upgrade.md)。

您可以将`require`节添加到`composer.json`文件，也可以按如下方式使用`composer require`命令：

{{$include /help/_includes/server-login.md}}

您可以选择以下选项：

## 获取可用的模块版本

命令用法：

```shell
composer show --all <vendor>/<name>
```

例如：

```shell
composer show --all example/module
```

## 使用`composer require`命令

命令用法：

```shell
composer require <vendor>/<name>:<version>
```

例如：

```shell
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

   ```shell
   composer update
   ```

<!-- Last updated from includes: 2026-04-17 13:49:36 -->
