---
title: 单机部署
description: 了解如何使用命令行在生产服务器上部署商务更新。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 单机部署

本主题提供了使用命令行在生产服务器上部署商务更新的说明。 此过程适用于负责在安装了某些主题和区域设置的单个计算机上运行存储的技术用户。

## 假设

- 您使用 [编辑器].
- 您将直接将更新应用到服务器。

>[!WARNING]
>
>如果您使用 `git clone` 来安装Commerce。
>参与开发人员应使用 [本指南][install] 以更新其Commerce安装。

## 部署步骤

1. 作为或切换到 [文件系统所有者][file-owner].

1. 将目录更改为Commerce基目录：

   ```bash
   cd <Commerce base directory>
   ```

1. 使用命令启用维护模式：

   ```bash
   bin/magento maintenance:enable
   ```

1. 使用以下命令模式将更新应用于商务或其组件：

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **软件包**:要更新的包的名称。

   例如：

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **版本**:要更新的包的目标版本。

1. 使用编辑器更新组件：

   ```bash
   composer update
   ```

1. 更新数据库模式和数据：

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

1. 清除缓存：

   ```bash
   bin/magento cache:clean
   ```

1. 退出维护模式：

   ```bash
   bin/magento maintenance:disable
   ```

<!-- link definitions -->

[install]: https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/
[composer]: ../../installation/composer.md
[file-owner]: ../../installation/prerequisites/file-system/overview.md
