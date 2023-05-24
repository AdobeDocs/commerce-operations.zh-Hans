---
title: 技术详细信息
description: 阅读有关管道部署、配置类型和推荐工作流程的技术详细信息。
exl-id: a396d241-f895-4414-92af-3abf3511e62a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 0%

---

# 技术详细信息

本主题讨论有关Commerce 2.2及更高版本中管道部署的技术实施详细信息。 改进可以分为以下几个方面：

- [配置管理](#configuration-management)
- [管理员中的更改](#changes-in-the-admin)
- [安装和删除cron](#install-and-remove-cron)

本主题还将讨论 [推荐的工作流](#recommended-workflow) ，并提供了一些示例来帮助您了解它的工作方式。

在开始之前，请查看 [开发、构建和生产系统的先决条件](../deployment/prerequisites.md).

## 配置管理

要让您同步和维护开发和生产系统的配置，请使用以下覆盖方案。

![如何确定配置变量值](../../assets/configuration/override-flow-diagram.png)

如图所示，配置值的使用顺序如下：

1. 环境变量（如果存在）将覆盖所有其他值。
1. 从共享配置文件 `env.php` 和 `config.php`. 中的值 `env.php` 覆盖中的值 `config.php`.
1. 从数据库中存储的值。
1. 如果这些源的任何一个中都不存在值，则使用默认值或NULL。

### 管理共享配置

共享配置存储在中 `app/etc/config.php`，它应位于源代码控制中。

在开发的管理员(或云基础架构上的Adobe Commerce)中设置共享配置 _集成_)系统并将配置写入 `config.php` 使用 [`magento app:config:dump` 命令](../cli/export-configuration.md).

### 管理特定于系统的配置

系统特定的配置存储在中 `app/etc/env.php`，应 _非_ 在源代码管理中。

在开发系统的管理员(或Adobe Commerce on cloud infrastructure集成)中设置系统特定的配置，并将配置写入 `env.php` 使用 [`magento app:config:dump` 命令](../cli/export-configuration.md).

此命令还会将敏感设置写入 `env.php`.

### 管理敏感配置

敏感配置还存储在中 `app/etc/env.php`.

您可以通过以下任意方式管理敏感配置：

- 环境变量
- 将敏感配置保存在 `env.php` 在生产系统上使用 [`magento config:set:sensitive` 命令](../cli/set-configuration-values.md)

### 配置设置已在Admin中锁定

中的任何配置设置 `config.php` 或 `env.php` 在Admin中锁定；也就是说，无法在Admin中更改这些设置。
使用 [`magento config:set` 或 `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) 命令以更改 `config.php` 或 `env.php` 文件。

## 商务管理员

在生产模式下，管理员会显示以下行为：

- 您不能在“管理员”中启用或禁用缓存类型
- 开发人员设置不可用(**商店** >设置> **配置** >高级> **开发人员**)，包括：

   - 缩小CSS、JavaScript和HTML
   - 合并CSS和JavaScript
   - 服务器端或客户端LESS编译
   - 内联翻译
   - 如前所述，中的任意配置设置 `config.php` 或 `env.php` 已锁定，无法在管理员中进行编辑。
   - 您只能将管理员区域设置更改为已部署主题使用的语言

      下图显示了 **帐户设置** > **界面区域设置** 管理员中的列表，仅显示两个已部署的区域设置：

      ![您只能将“管理员”区域设置更改为已部署的区域设置](../../assets/configuration/split-deploy-admin-locale.png)

- 不能使用Admin更改任何范围的区域设置配置。

   我们建议在切换到生产模式之前进行这些更改。

   您仍然可以使用环境变量或 `config:set` 带有路径的CLI命令 `general/locale/code`.

## 安装和删除cron

在版本2.2中，我们首次通过提供 [`magento cron:install` 命令](../cli/configure-cron-jobs.md). 此命令将crontab设置为运行该命令的用户。

此外，您还可以使用 `magento cron:remove` 命令。

## 建议的管道部署工作流

下图显示了我们建议您如何使用管道部署来管理配置。

![建议的管道部署工作流](../../assets/configuration/split-deploy-workflow.png)

### 开发系统

在开发系统中，您可在管理员中进行配置更改并生成共享配置， `app/etc/config.php` 以及系统特定的配置， `app/etc/env.php`. 将Commerce代码和共享配置检查到源代码管理中，并将其推送到构建服务器。

您还应在开发系统上安装扩展和自定义Commerce代码。

在您的开发系统上：

1. 在“管理员”中设置配置。

1. 使用 `magento app:config:dump` 命令将配置写入文件系统。

   - `app/etc/config.php` 是共享配置，包含所有设置 _排除_ 敏感和系统特定的设置。 此文件应在源代码管理中。
   - `app/etc/env.php` 是特定于系统的配置，其中包含特定系统特有的设置（例如，主机名和端口号）。 此文件应 _非_ 在源代码管理中。

1. 将修改后的代码和共享配置添加到源代码管理。

1. 要在开发过程中删除生成的php代码和静态资源文件，请运行以下命令：

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

运行命令清除资产后，Commerce会生成工作文件。

>[!WARNING]
>
>谨慎使用上述方法。 正在删除 `.htacces`s文件位于 `generated` 或 `pub` 文件夹可能会导致问题。

### 构建系统

构建系统编译代码并为在Commerce中注册的主题生成静态视图文件。 它不需要连接到Commerce数据库；它只需要Commerce代码库。

在您的构建系统上：

1. 从源代码管理中提取共享配置文件。
1. 使用 `magento setup:di:compile` 编译代码的命令。
1. 使用 `magento setup:static-content:deploy -f` 用于更新静态文件视图文件的命令。
1. 将更新签入源代码管理。

>[!INFO]
>
>参见 [静态视图文件的部署策略](../cli/static-view-file-strategy.md).

### 生产系统

在生产系统（即实时商店）中，您可以从源代码管理中提取生成的资源和代码更新，并使用命令行或环境变量设置系统特定的敏感配置设置。

在您的生产系统上：

1. 启动维护模式。
1. 从源代码管理中获取代码和配置更新。
1. 如果您使用Adobe Commerce，请停止队列工作程序。
1. 使用 `magento app:config:import` 命令导入生产系统中的配置更改。
1. 如果安装了更改数据库模式的组件，请运行 `magento setup:upgrade --keep-generated` 更新数据库架构和数据，保留生成的静态文件。
1. 要设置系统特定的设置，请使用 `magento config:set` 命令或环境变量。
1. 要设置敏感设置，请使用 `magento config:sensitive:set` 命令或环境变量。
1. 清理(也称为 _刷新_)缓存。
1. 结束维护模式。

## 配置管理命令

我们提供以下命令帮助您管理配置：

- [`magento app:config:dump`](../cli/export-configuration.md) 将管理员配置设置写入 `config.php` 和 `env.php` （敏感设置除外）
- [`magento config:set`](../cli/set-configuration-values.md) 在生产系统上设置系统特定的设置的值。

   使用可选 `--lock` 选项来锁定管理员中的选项（即，使设置不可编辑）。 如果设置已锁定，请使用 `--lock` 选项更改设置。

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) 在生产系统上设置敏感设置的值。
- [`magento app:config:import`](../cli/import-configuration.md) 要从中导入配置更改 `config.php` 和 `env.php` 到生产系统。

## 配置管理示例

此部分显示管理配置的示例，以便您查看如何对进行更改 `config.php` 和 `env.php`.

### 更改默认区域设置

此部分显示对所做的更改 `config.php` 当您使用管理员(**商店** >设置> **配置** >常规> **常规** > **区域设置选项**)。

在“管理员”中进行更改后，运行 `bin/magento app:config:dump` 将值写入 `config.php`. 该值会写入 `general` 数组位于 `locale` 作为以下代码片段 `config.php` 显示：

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
- 设置PayPal API用户名和API密码(**商店** >设置> **配置** >销售> **支付方式** > **PayPal** > **必需的PayPal设置**)

在“管理员”中进行更改后，运行 `bin/magento app:config:dump` 在您的开发系统上。 这次，并非您的所有更改都写入 `config.php`；实际上，只有网站、商店和商店视图会写入该文件，如下面的代码段所示。

### config.php

`config.php` 包含：

- 对网站、商店和商店视图的更改。
- 非系统特定的搜索引擎设置
- 不敏感的PayPal设置
- 通知您从中省略的敏感设置的注释 `config.php`

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

默认电子邮件域系统特定的配置设置会写入 `app/etc/env.php`.

PayPal设置不会写入这两个文件，因为 `bin/magento app:config:dump` 命令不写入敏感设置。 您必须使用以下命令在生产系统上设置PayPal设置：

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
