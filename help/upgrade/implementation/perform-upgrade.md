---
title: 执行升级
description: 按照以下步骤升级Adobe Commerce或Magento Open Source项目。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 0%

---


# 执行升级

如果通过以下方式安装了软件，则可以从命令行升级您的Adobe Commerce或Magento Open Source应用程序：

- 下载 [元包](https://glossary.magento.com/metapackage) 使用 `composer create-project` 命令。
- 安装压缩的存档。

>[!NOTE]
>
>如果克隆了GitHub存储库，请勿使用此方法进行升级。 相反，请参阅 [升级基于git的安装](../developer/git-installs.md) ，以了解升级说明。

以下说明将向您展示如何使用编辑器进行升级。 Adobe Commerce 2.4.2引入了对编辑器2的支持。 如果您尝试从&lt;2.4.1升级，则必须首先使用编辑器1升级到与编辑器2兼容的版本（例如，2.4.2） _之前_ 升级到编辑器2以升级超过2.4.2。 此外，您必须运行 [受支持版本](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) PHP的。

>[!WARNING]
>
>升级Adobe Commerce和Magento Open Source的过程已更改。 您必须安装 `magento/composer-root-update-plugin` 包(请参阅 [先决条件](../prepare/prerequisites.md))。 此外，升级命令已从 `composer require magento/<package_name>` to `composer require-commerce magento/<package_name>`.

## 开始之前

您必须完成 [升级先决条件](../prepare/prerequisites.md) 以在开始升级过程之前准备环境。

## 管理资源包

>[!NOTE]
>
>有关指定不同发行级别的帮助，请参阅本节末尾的示例。 例如，次要版本、质量修补程序和安全修补程序。 Adobe Commerce客户可以在正式发布(GA)日期前两周访问修补程序。 预发行包仅可通过编辑器使用。 在GA之前，无法在下载门户或GitHub上找到它们。 如果在编辑器中找不到这些包，请联系Adobe Commerce支持。

1. 切换到维护模式，以防止在升级过程中访问您的存储。

   ```bash
   bin/magento maintenance:enable
   ```

   请参阅 [启用或禁用维护模式](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html) 的其他选项。 （可选）您可以创建 [“自定义维护模式”页](https://devdocs.magento.com/guides/v2.4/comp-mgr/trouble/cman/maint-mode.html).

1. 创建备份 `composer.json` 文件。

   ```bash
   cp composer.json composer.json.bak
   ```

1. 根据您的需求添加或删除特定包。

   例如，如果您从Magento Open Source升级到Adobe Commerce，请删除Magento Open Source包。

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   您还可以升级示例数据。

   ```bash
   composer require <sample data module-1>:<version> ... <sample data module-n>:<version> --no-update
   ```

   - _Adobe Commerce:_

      ```bash
      composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
      ```

   - _Magento Open Source:_

      ```bash
      composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
      ```

1. 使用以下方法升级您的实例 `composer require-commerce` 命令语法：

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   命令选项包括：

   - `<product>`  — （必需）要升级的包。 对于本地安装，此值必须是 `product-community-edition` 或 `product-enterprise-edition`.

   - `<version>`  — （必需）您要升级到的Adobe Commerce或Magento Open Source版本。 例如， `2.4.3`.

   - `--no-update`  — （必需）禁用依赖项的自动更新。

   - `--interactive-root-conflicts`  — （可选）允许您以交互方式查看和更新以前版本中任何过期的值，或任何与您升级到的版本不匹配的自定义值。

   - `--force-root-updates`  — （可选）使用预期的Magento值覆盖所有冲突的自定义值。

   - `--help`  — （可选）提供有关插件的使用情况详细信息。
   如果两者都不 `--interactive-root-conflicts` nor `--force-root-updates` ，则命令会保留冲突的现有值，并显示警告消息。 要进一步了解该插件，请参阅 [插件使用自述文件](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

1. 更新依赖项。

   ```bash
   composer update
   ```

### 示例 — 列出可用版本

要查看可用2.4.x版本的完整列表，请执行以下操作：

_Magento Open Source_:

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_:

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### 示例 — 次要版本

次要版本包含新增功能、质量修复和安全修复。 使用编辑器指定次要版本。 例如，要指定Magento Open Source2.4.3元包：

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.0 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.0 --no-update
```

### 示例 — 质量修补程序

质量修补程序主要包含功能 _和_ 安全修复。 但是，它们有时可能包含向后兼容的新功能。 使用编辑器下载质量修补程序。 例如，要指定Magento Open Source2.4.1元包：

```bash
composer require-commerce magento/product-community-edition 2.4.3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3 --no-update
```

### 示例 — 安全修补程序

安全修补程序仅包含安全修补程序。 它们旨在使升级过程更快、更轻松。

安全修补程序使用编辑器命名约定 `2.4.x-px`. 使用编辑器指定修补程序。

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3-p1 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3-p1 --no-update
```

## 更新元数据

1. 更新 `"name"`, `"version"`和 `"description"` 字段 `composer.json` 文件。

   >[!NOTE]
   >
   >更新 `composer.json` 文件完全肤浅，无法正常工作。

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
   >如果您使用文件系统以外的缓存存储（如Redis或Memcached），则还必须手动清除那里的缓存。

1. 更新数据库模式和数据。

   ```bash
   bin/magento setup:upgrade
   ```

1. 禁用维护模式。

   ```bash
   bin/magento maintenance:disable
   ```

1. _（可选）_ 重新启动清漆。

   如果使用清漆进行页面缓存，请重新启动它：

   ```bash
   service varnish restart
   ```

## 检查您的工作

在Web浏览器中打开您的店面URL，以检查升级是否成功。 如果升级失败，您的店面将无法正确加载。

如果应用程序在  `We're sorry, an error has occurred while generating this email.` 错误：

1. 重置 [文件系统所有权和权限](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html) 用户 `root` 权限。
1. 清除以下目录：
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. 再次在Web浏览器中检查您的店面。
