---
title: 技术详细信息
description: 有关管道部署、配置类型和推荐的工作流的技术详细信息，请参阅。
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 0%

---


# 技术详细信息

本主题讨论有关Commerce 2.2及更高版本中管道部署的技术实施详细信息。 改进可分为以下几个方面：

- [配置管理](#configuration-management)
- [管理员中的更改](#changes-in-the-admin)
- [安装和删除cron](#install-and-remove-cron)

本主题还讨论了 [推荐的工作流](#recommended-workflow) ，并提供了一些示例来帮助您了解管道部署的工作方式。

开始之前，请查看 [开发、构建和生产系统的先决条件](../deployment/prerequisites.md).

## 配置管理

要使您能够同步和维护开发和生产系统的配置，请使用以下覆盖方案。

![如何确定配置变量值](../../assets/configuration/override-flow-diagram.png)

如图所示，配置值按以下顺序使用：

1. 环境变量（如果存在）会覆盖所有其他值。
1. 从共享的配置文件 `env.php` 和 `config.php`. 中的值 `env.php` 覆盖值 `config.php`.
1. 从数据库中存储的值。
1. 如果这些源中不存在值，则使用默认值或NULL。

### 管理共享配置

共享配置存储在 `app/etc/config.php`，它应位于源代码管理中。

在开发的管理员(或在云基础架构上的Adobe Commerce上)中设置共享配置 _集成_)系统并将配置写入 `config.php` 使用 [`magento app:config:dump` 命令](../cli/export-configuration.md).

### 管理特定于系统的配置

特定于系统的配置存储在 `app/etc/env.php`，应为 _not_ 在源代码管理中。

在开发(或云基础架构集成上的Adobe Commerce)系统的管理员中设置特定于系统的配置，并将配置写入 `env.php` 使用 [`magento app:config:dump` 命令](../cli/export-configuration.md).

此命令还会将敏感设置写入 `env.php`.

### 管理敏感配置

敏感配置也存储在 `app/etc/env.php`.

您可以通过以下任一方式管理敏感配置：

- 环境变量
- 将敏感配置保存在 `env.php` 使用 [`magento config:set:sensitive` 命令](../cli/set-configuration-values.md)

### 管理员中锁定的配置设置

中的任何配置设置 `config.php` 或 `env.php` 被锁定在管理员中；也就是说，这些设置在管理员中无法更改。
使用 [`magento config:set` 或 `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) 命令更改 `config.php` 或 `env.php` 文件。

## 商务管理员

在生产模式下，管理员会显示以下行为：

- 在“管理员”中，不能启用或禁用缓存类型
- 开发人员设置不可用(**商店** >设置> **配置** >高级> **开发人员**)，包括：

   - 缩小CSS、JavaScript和HTML
   - 合并CSS和JavaScript
   - 服务器端或客户端LESS编译
   - 内联翻译
   - 如前所述， `config.php` 或 `env.php` 已锁定，无法在管理员中编辑。
   - 您只能将管理员区域设置更改为已部署主题所使用的语言

      下图显示了 **帐户设置** > **界面区域设置** 在管理员中列出，仅显示两个部署的区域设置：

      ![您只能将管理员区域设置更改为已部署的区域设置](../../assets/configuration/split-deploy-admin-locale.png)

- 不能使用“管理员”更改任何范围的区域设置配置。

   我们建议您在切换到生产模式之前进行这些更改。

   您仍可以使用环境变量或 `config:set` 具有路径的CLI命令 `general/locale/code`.

## 安装和删除cron

在版本2.2中，我们首次通过提供 [`magento cron:install` 命令](../cli/configure-cron-jobs.md). 此命令将crontab设置为运行该命令的用户。

此外，您还可以使用 `magento cron:remove` 命令。

## 建议的管道部署工作流

下图显示了我们建议您如何使用管道部署来管理配置。

![建议的管道部署工作流](../../assets/configuration/split-deploy-workflow.png)

### 开发系统

在开发系统上，您在管理员中进行配置更改并生成共享配置， `app/etc/config.php` 和系统特定配置， `app/etc/env.php`. 将商务代码和共享配置选中到源控件中，然后将其推送到生成服务器。

您还应在开发系统上安装扩展并自定义商务代码。

在您的开发系统上：

1. 在管理员中设置配置。

1. 使用 `magento app:config:dump` 命令将配置写入文件系统。

   - `app/etc/config.php` 是共享配置，其中包含所有设置 _除外_ 敏感和特定于系统的设置。 此文件应在源代码管理中。
   - `app/etc/env.php` 是特定于系统的配置，其中包含特定系统（例如，主机名和端口号）所特有的设置。 此文件应 _not_ 在源代码管理中。

1. 将修改的代码和共享配置添加到源代码管理。

1. 要在开发过程中删除生成的php代码和静态资产文件，请运行以下命令：

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

运行清除资产的命令后，Commerce会生成工作文件。

>[!WARNING]
>
>注意上述方法。 删除 `.htacces`s文件 `generated` 或 `pub` 文件夹可能会导致问题。

### 构建系统

构建系统编译代码并为商务中注册的主题生成静态视图文件。 它不需要与商务数据库建立连接；它只需要商务代码库。

在您的构建系统上：

1. 从源代码管理中提取共享配置文件。
1. 使用 `magento setup:di:compile` 命令来编译代码。
1. 使用 `magento setup:static-content:deploy -f` 命令更新静态文件视图文件。
1. 在源代码管理中检查更新。

>[!INFO]
>
>请参阅 [静态视图文件的部署策略](../cli/static-view-file-strategy.md).

### 生产系统

在生产系统（即Live Store）上，您可以从源代码管理中提取生成的资产和代码更新，并使用命令行或环境变量设置特定于系统的敏感配置设置。

在您的生产系统上：

1. 启动维护模式。
1. 从源代码管理中提取代码和配置更新。
1. 如果您使用Adobe Commerce，请停止排队工作程序。
1. 使用 `magento app:config:import` 命令导入生产系统中的配置更改。
1. 如果安装了更改数据库架构的组件，请运行 `magento setup:upgrade --keep-generated` 更新数据库模式和数据，保留生成的静态文件。
1. 要设置特定于系统的设置，请使用 `magento config:set` 命令或环境变量。
1. 要设置敏感设置，请使用 `magento config:sensitive:set` 命令或环境变量。
1. Clean(也称为 _刷新_)缓存。
1. 结束维护模式。

## 配置管理命令

我们提供以下命令来帮助您管理配置：

- [`magento app:config:dump`](../cli/export-configuration.md) 将管理员配置设置写入 `config.php` 和 `env.php` （敏感设置除外）
- [`magento config:set`](../cli/set-configuration-values.md) 来设置生产系统中特定于系统的设置值。

   使用可选 `--lock` 选项来锁定“管理员”中的选项（即，使设置不可编辑）。 如果设置已锁定，请使用 `--lock` 选项来更改设置。

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) 来设置生产系统中敏感设置的值。
- [`magento app:config:import`](../cli/import-configuration.md) 从导入配置更改 `config.php` 和 `env.php` 到生产系统。

## 配置管理示例

此部分显示了管理配置的示例，以便您查看对 `config.php` 和 `env.php`.

### 更改默认区域设置

此部分显示对 `config.php` 当您使用管理员(**商店** >设置> **配置** >常规> **常规** > **区域设置选项**)。

在管理员中进行更改后，运行 `bin/magento app:config:dump` 将值写入 `config.php`. 值将写入 `general` 数组 `locale` 作为以下代码片段 `config.php` 显示：

```php
'general' =>
    array (
        'locale' =>
        array (
            'code' => 'en_US',
            'timezone' => 'America/Chicago',
            'weight_unit' => 'kgs'
        )
    )
```

### 更改多个配置设置

本节讨论如何进行以下配置更改：

- 添加网站、商店和商店视图(**商店** >设置> **所有商店**)
- 更改默认电子邮件域(**商店** >设置> **配置** >客户> **客户配置**)
- 设置PayPal API用户名和API密码(**商店** >设置> **配置** >销售> **付款方法** > **PayPal** > **必需的PayPal设置**)

在管理员中进行更改后，运行 `bin/magento app:config:dump` 在您的开发系统上。 这次，并非所有更改都写入 `config.php`;事实上，只有网站、存储和存储视图才会像以下代码片段所示写入该文件。

### config.php

`config.php` 包含：

- 对网站、存储和存储视图的更改。
- 非系统特定的搜索引擎设置
- 非敏感PayPal设置
- 通知您中忽略的敏感设置的注释 `config.php`

`websites` 数组：

```php
      'new' =>
      array (
        'website_id' => '2',
        'code' => 'new',
        'name' => 'New website',
        'sort_order' => '0',
        'default_group_id' => '2',
        'is_default' => '0',
      ),
```

`groups` 数组：

```php
      2 =>
      array (
        'group_id' => '2',
        'website_id' => '2',
        'code' => 'newstore',
        'name' => 'New store',
        'root_category_id' => '2',
        'default_store_id' => '2',
      ),
```

`stores` 数组：

```php
     'newview' =>
      array (
        'store_id' => '2',
        'code' => 'newview',
        'website_id' => '2',
        'group_id' => '2',
        'name' => 'New store view',
        'sort_order' => '0',
        'is_active' => '1',
      ),
```

`payment` 数组：

```php
      'payment' =>
      array (
        'paypal_express' =>
        array (
          'active' => '0',
          'in_context' => '0',
          'title' => 'PayPal Express Checkout',
          'sort_order' => NULL,
          'payment_action' => 'Authorization',
          'visible_on_product' => '1',
          'visible_on_cart' => '1',
          'allowspecific' => '0',
          'verify_peer' => '1',
          'line_items_enabled' => '1',
          'transfer_shipping_options' => '0',
          'solution_type' => 'Mark',
          'require_billing_address' => '0',
          'allow_ba_signup' => 'never',
          'skip_order_review_step' => '1',
        ),
```

### env.php

默认的电子邮件域系统特定配置设置将写入 `app/etc/env.php`.

PayPal设置不会写入任何文件，因为 `bin/magento app:config:dump` 命令不写入敏感设置。 您必须使用以下命令在生产系统上设置PayPal设置：

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
