---
title: 执行升级
description: 按照以下步骤升级Adobe Commerce的内部部署。
exl-id: 9183f1d2-a8dd-4232-bdee-7c431e0133df
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---


# 执行升级

您可以升级 _内部部署_ 部署Adobe Commerce或Magento Open Source应用程序（如果通过以下方式安装软件）：

- 使用下载编辑器metapackage `composer create-project` 命令。
- 正在安装压缩的归档文件。

>[!NOTE]
>
>- 有关云基础架构项目的Adobe Commerce，请参阅 [升级Commerce版本](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html) （在云指南中）。
>- 如果您克隆GitHub存储库，请勿使用此方法进行升级。 请参阅 [升级基于Git的安装](../developer/git-installs.md).

以下说明说明了如何使用编辑器包管理器进行升级。 Adobe Commerce 2.4.2引入了对Composer 2的支持。 如果您尝试从&lt;2.4.1升级，则必须首先使用编辑器1升级到与编辑器2兼容的版本（例如，2.4.2） _早于_ 升级到Composer 2以进行2.4.2以上升级。 此外，您必须运行 [支持的版本](../../installation/system-requirements.md) PHP的。

>[!WARNING]
>
>升级Adobe Commerce的过程已更改。 您必须安装新版本的 `magento/composer-root-update-plugin` 包(请参阅 [先决条件](../prepare/prerequisites.md))。 此外，用于升级的命令已从 `composer require magento/<package_name>` 到 `composer require-commerce magento/<package_name>`.

## 开始之前

您必须完成 [升级先决条件](../prepare/prerequisites.md) 以在开始升级过程之前准备环境。

## 管理包

>[!NOTE]
>
>请参阅本节末尾的示例，以获取指定不同版本级别的帮助。 例如，高质量的修补程序和安全修补程序。 如果您在编辑器中找不到这些包，请联系Adobe Commerce支持。

1. 切换到维护模式以防止在升级过程中访问存储区。

   ```bash
   bin/magento maintenance:enable
   ```

   请参阅 [启用或禁用维护模式](../../installation/tutorials/maintenance-mode.md) 以获取其他选项。 或者，您可以创建 [自定义维护模式页面](../troubleshooting/maintenance-mode-options.md).

1. 在异步进程（如消息队列使用者）运行时启动升级过程可能会导致数据损坏。 要防止数据损坏，请禁用所有cron作业。

   _云基础架构上的Adobe Commerce：_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source：_

   ```bash
   bin/magento cron:remove
   ```

1. 手动启动所有消息队列使用者，以确保使用所有消息。

   ```bash
   bin/magento cron:run --group=consumers
   ```

   等待cron作业完成。 您可以使用进程查看器或通过运行 `ps aux | grep 'bin/magento queue'` 多次命令，直到所有进程完成。

1. 创建备份 `composer.json` 文件。

   ```bash
   cp composer.json composer.json.bak
   ```

1. 根据您的需求添加或删除特定包。

   例如，如果您要从Magento Open Source升级到Adobe Commerce，请删除Magento Open Source包。

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   您还可以升级示例数据。

   ```bash
   composer require <sample data module-1>:<version> ... <sample data module-n>:<version> --no-update
   ```

   - _Adobe Commerce：_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
     ```

   - _Magento Open Source：_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
     ```

1. 使用以下方式升级您的实例 `composer require-commerce` 命令语法：

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   命令选项包括：

   - `<product>`  — （必需）要升级的包。 对于内部部署，此值必须为 `product-community-edition` 或 `product-enterprise-edition`.

   - `<version>`  — （必需）要升级到的Adobe Commerce或Magento Open Source的版本。 例如， `2.4.3`.

   - `--no-update`  — （必需）禁用依赖关系的自动更新。

   - `--interactive-root-conflicts`  — （可选）允许您以交互方式查看和更新先前版本的任何过期值，或与要升级到的版本不匹配的任何自定义值。

   - `--force-root-updates`  — （可选）使用预期的Commerce值覆盖所有冲突的自定义值。

   - `--help`  — （可选）提供有关插件的使用详细信息。

   如果两者均不 `--interactive-root-conflicts` 也不 `--force-root-updates` 指定时，该命令将保留冲突的现有值并显示警告消息。 要了解有关插件的更多信息，请参阅 [插件使用情况自述文件](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

1. 更新依赖关系。

   ```bash
   composer update
   ```

### 示例 — 列出可用版本

要查看可用2.4.x版本的完整列表，请执行以下操作：

_Magento Open Source_：

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_：

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### 示例 — 质量修补程序

质量补丁主要包含功能性 _和_ 安全修复。 但是，它们有时可以包含向后兼容的新功能。 使用Composer下载质量修补程序。

_Adobe Commerce_：

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6 --no-update
```

_Magento Open Source_：

```bash
composer require-commerce magento/product-community-edition 2.4.6 --no-update
```

### 示例 — 安全修补程序

安全修补程序仅包含安全修补程序。 它们旨在使升级过程更快、更轻松。 安全修补程序使用编辑器命名约定 `2.4.x-px`.

_Adobe Commerce_：

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6-p3 --no-update
```

_Magento Open Source_：

```bash
composer require-commerce magento/product-community-edition 2.4.6-p3 --no-update
```

## 更新元数据

1. 更新 `"name"`， `"version"`、和 `"description"` 中的字段 `composer.json` 文件。

   >[!NOTE]
   >
   >在中更新元数据 `composer.json` 文件完全是表面的，无法正常运行。

1. 应用更新。

   ```bash
   composer update
   ```

1. 清除 `var/` 和 `generated/` 子目录：

   ```bash
   rm -rf var/cache/*
   ```

   ```bash
   rm -rf var/page_cache/*
   ```

   ```bash
   rm -rf generated/code/*
   ```

   >[!NOTE]
   >
   >如果您使用文件系统以外的缓存存储，如Redis或Memcached，则也必须手动清除其中的缓存。

1. 更新数据库架构和数据。

   ```bash
   bin/magento setup:upgrade
   ```

1. 禁用维护模式。

   ```bash
   bin/magento maintenance:disable
   ```

1. _（可选）_ 重新启动Varnish。

   如果将Varnish用于页面缓存，请重新启动它：

   ```bash
   service varnish restart
   ```

## 检查您的工作

要检查升级是否成功，请在Web浏览器中打开店面URL。 如果升级不成功，您的店面将无法正确加载。

如果应用程序失败，  `We're sorry, an error has occurred while generating this email.` 错误：

1. 重置 [文件系统所有权和权限](../../installation/prerequisites/file-system/configure-permissions.md) 作为用户，具有 `root` 权限。
1. 清除以下目录：
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. 再次在Web浏览器中查看您的店面。
