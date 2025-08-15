---
title: 单个计算机部署
description: 了解如何使用命令行在生产服务器上将更新部署到Commerce。
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 1%

---

# 单机部署

本主题提供有关使用命令行在生产服务器上部署对Commerce的更新的说明。 此过程适用于负责在安装了某些主题和区域设置的单个计算机上运行的商店的技术用户。

## 假设

- 您使用[编辑器](../../installation/composer.md)安装了Commerce。
- 您正在将更新直接应用到服务器。

>[!WARNING]
>
>如果您使用`git clone`安装Commerce，则本指南不适用。
>>参与开发的开发人员应使用[本指南][install]更新其Commerce安装。

## 部署步骤

1. 以[文件系统所有者](../../installation/prerequisites/file-system/overview.md)的身份登录或切换到生产服务器。

1. 将目录更改为Commerce基目录：

   ```bash
   cd <Commerce base directory>
   ```

1. 使用命令启用维护模式：

   ```bash
   bin/magento maintenance:enable
   ```

1. 使用以下命令模式将更新应用到Commerce或其组件：

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **包**：要更新的包的名称。

   例如：

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **版本**：要更新的包的目标版本。

1. 使用编辑器更新组件：

   ```bash
   composer update
   ```

1. 更新数据库架构和数据：

   ```bash
   bin/magento setup:upgrade
   ```

1. 编译代码：

   ```bash
   bin/magento setup:di:compile
   ```

1. 部署静态内容：

   ```bash
   bin/magento setup:static-content:deploy
   ```

1. 清理缓存：

   ```bash
   bin/magento cache:clean
   ```

1. 退出维护模式：

   ```bash
   bin/magento maintenance:disable
   ```

<!-- link definitions -->

[install]: https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/
