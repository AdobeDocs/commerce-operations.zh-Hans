---
title: 单个计算机部署
description: 了解如何使用命令行在生产服务器上将更新部署到Commerce。
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '189'
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
>参与开发的开发人员应使用[本指南](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies)更新其Commerce安装。

## 部署步骤

1. 以[文件系统所有者](../../installation/prerequisites/file-system/overview.md)的身份登录或切换到生产服务器。

1. 将目录更改为Commerce基目录：

   ```shell
   cd <Commerce base directory>
   ```

1. 使用命令启用维护模式：

   ```shell
   bin/magento maintenance:enable
   ```

1. 使用以下命令模式将更新应用到Commerce或其组件：

   ```shell
   composer require-commerce <package> <version> --no-update
   ```

   **包**：要更新的包的名称。

   例如：

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **版本**：要更新的包的目标版本。

1. 使用编辑器更新组件：

   ```shell
   composer update
   ```

1. 更新数据库架构和数据：

   ```shell
   bin/magento setup:upgrade
   ```

1. 编译代码：

   ```shell
   bin/magento setup:di:compile
   ```

1. 部署静态内容：

   ```shell
   bin/magento setup:static-content:deploy
   ```

1. 清理缓存：

   ```shell
   bin/magento cache:clean
   ```

1. 退出维护模式：

   ```shell
   bin/magento maintenance:disable
   ```

