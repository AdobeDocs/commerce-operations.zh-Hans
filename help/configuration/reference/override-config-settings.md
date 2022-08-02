---
title: 覆盖配置设置
description: 了解如何使用环境变量覆盖配置设置。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 0%

---


# 覆盖配置设置

本主题讨论如何通过配置路径获取环境变量名称。 您可以使用环境变量覆盖Adobe Commerce配置设置。 例如，您可以覆盖生产系统上支付处理者的实时URL的值。

您可以覆盖 _any_ 使用环境变量进行配置设置；但是，Adobe建议您使用共享配置文件来保持一致的设置， `config.php`，以及特定于系统的配置文件、 `env.php`，在中讨论 [部署常规概述](../deployment/overview.md).

>[!TIP]
>
>查看 [配置环境](https://devdocs.magento.com/cloud/env/variables-intro.html) 主题 _Commerce Cloud指南_ 有关在云基础架构上使用Adobe Commerce中的变量的详细信息。

## 环境变量

环境变量名称由其范围以及特定格式的配置路径组成。 以下各节将更详细地讨论如何确定变量名称。

您可以将变量用于以下任一项：

- [敏感值](config-reference-sens.md) 必须使用环境变量或 [`magento config:sensitive:set`](../cli/set-configuration-values.md) 命令。
- 系统特定的值必须使用：

   - 环境变量
   - 的 [`magento config:set`](../cli/set-configuration-values.md) 命令
   - 管理员后跟 [`magento app:config:dump` 命令](../cli/export-configuration.md)

配置路径可在以下位置找到：

- [敏感和特定于系统的配置路径引用](config-reference-sens.md)
- [付款配置路径参考](config-reference-payment.md)
- [商务B2B扩展配置路径参考](config-reference-b2b.md)
- [其他配置路径引用](config-reference-general.md)

### 变量名称

系统设置变量名称的常规格式如下：

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` 可以是：

- 全局范围(即 _全部_ 范围)

   全局范围变量具有以下格式：

   `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- 特定范围（即，设置仅影响指定的商店视图或网站）

   例如，存储视图范围变量具有以下格式：

   `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

   有关作用域的更多信息，请参阅：

   - [步骤1:查找网站或商店视图范围值](#step-1-find-the-website-or-store-view-scope-value)
   - [有关范围的商务用户指南主题](https://docs.magento.com/user-guide/configuration/scope.html)
   - [范围快速参考](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` 是使用双下划线字符替换的配置路径 `/`. 有关更多信息，请参阅 [步骤2:设置系统变量](#step-2-set-global-website-or-store-view-variables).

### 变量格式

`<SCOPE>` 从 `<SYSTEM__VARIABLE__NAME>` 下划线字符。

`<SYSTEM__VARIABLE__NAME>` 派生自配置设置的 _配置路径_, `/` 用于唯一标识特定设置的分隔字符串。 替换 `/` 配置路径中的字符，带有两个下划线字符以创建系统变量。

如果配置路径包含下划线字符，则下划线字符仍保留在变量中。

配置路径的完整列表可在中找到：

- [敏感和特定于系统的配置路径引用](config-reference-sens.md)
- [付款配置路径参考](config-reference-payment.md)
- [商务企业B2B扩展配置路径参考](config-reference-b2b.md)
- [其他配置路径引用](config-reference-general.md)

## 步骤1:查找网站或商店视图范围值

本节将讨论如何查找和设置每个 _范围_ （存储视图或网站）。 要设置全局范围变量，请参阅 [步骤2:设置全局、网站或存储视图变量](#step-2-set-global-website-or-store-view-variables).

范围值来自 `store`, `store_group`和 `store_website` 表格。

- 的 `store` 表指定存储视图名称和代码
- 的 `store_website` 表指定网站名称和代码

您还可以使用管理员查找代码值。

如何阅读表格：

- `Path in Admin` 列

   逗号前面的值是“管理员”导航中的路径。 逗号后面的值是右侧窗格中的选项。

- `Variable name` column是相应环境变量的名称。

   您可以根据需要选择将这些配置参数的系统值指定为环境变量。

   - 整个变量名称始终为ALL CAPS
   - 以 `CONFIG__` （注意两个下划线字符）
   - 您可以在 `<STORE_VIEW_CODE>` 或 `<WEBSITE_CODE>` 管理员或商务数据库中变量名称的一部分，如以下部分所示。
   - 您可以找到 `<SYSTEM__VARIABLE__NAME>` 如 [步骤2:设置全局、网站或存储视图变量](#step-2-set-global-website-or-store-view-variables).

### 在“管理员”中查找网站或存储视图范围

下表概述了如何在管理员中查找网站或存储视图值。

| 描述 | 管理中的路径 | 变量名称 |
|--------------|--------------|----------------------|
| 创建、编辑、删除存储视图 | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| 创建、编辑、删除网站 | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

例如，要在“管理员”中查找网站或存储视图范围值，请执行以下操作：

1. 以有权查看网站的用户身份登录到管理员。
1. 单击 **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. 单击网站或商店视图的名称。

   右窗格显示如下所示。

   ![查找网站代码](../../assets/configuration/website-code.png)

1. 范围名称显示在 **[!UICONTROL Code]** 字段。
1. 继续 [步骤2:设置全局、网站或存储视图变量](#step-2-set-global-website-or-store-view-variables).

### 在数据库中查找网站或存储视图范围

要从数据库获取这些值，请执行以下操作：

1. 登录到您的开发系统，作为 [文件系统所有者](https://glossary.magento.com/magento-file-system-owner) 如果您尚未这样做，请执行此操作。
1. 输入以下命令：

   ```bash
   mysql -u <database-username> -p
   ```

1. 在 `mysql>` 提示符下，按所示顺序输入以下命令：

   ```shell
   use <database-name>;
   ```

1. 使用以下SQL查询来查找相关值：

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   示例如下：

   ```shell
   mysql> SELECT * FROM STORE_WEBSITE;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

1. 使用 `code` 列作为作用域名称，而不是 `name` 值。

   例如，要为测试网站设置配置变量，请使用以下格式：

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   where `<SYSTEM__VARIABLE__NAME>` 来自下一部分。

## 步骤2:设置全局、网站或存储视图变量

本节将讨论如何设置系统变量。

- 要设置全局范围（即，所有网站、商店和存储视图）的值，请以 `CONFIG__DEFAULT__`.

- 要为特定商店视图或网站设置值，请启动变量名称，如 [步骤1:查找范围值](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- 变量名称的最后一部分是配置路径，每个配置设置都具有唯一性。

[查看一些示例](#examples).

下表显示了一些示例变量。

| 描述 | 管理中的路径(省略 **商店** > **设置** > **配置**) | 变量名称 |
|--------------|--------------|----------------------|
| Elasticsearch服务器主机名 | 目录> **目录**, **Elasticsearch服务器主机名** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Elasticsearch服务器端口 | 目录> **目录**, **Elasticsearch服务器端口** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| 装运国原产地 | 销售> **装运设置** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| 自定义管理员URL | 高级> **管理员** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| 自定义管理路径 | 高级> **管理员** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## 示例

本节将介绍如何查找某些示例变量的值。

### Elasticsearch服务器主机名

要查找用于全局HTML缩小的变量名称，请执行以下操作：

1. 确定范围。

   它是全局范围，因此变量名称以 `CONFIG__DEFAULT__`

1. 变量名称的其余部分为 `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **结果**:变量名称为 `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### 装运国原产地

要查找发运国家/地区来源的变量名称，请执行以下操作：

1. 确定范围。

   在 [数据库](#find-a-website-or-store-view-scope-in-the-database) 如步骤1中所述：查找网站或商店视图范围值。 (您还可以在管理员中找到值，如 [步骤2中的表：设置全局、网站或存储视图变量](#step-2-set-global-website-or-store-view-variables)

   例如，范围可能为 `CONFIG__WEBSITES__DEFAULT`.

1. 变量名称的其余部分为 `SHIPPING__ORIGIN__COUNTRY_ID`.

   **结果**:变量名称为 `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## 如何使用环境变量

使用PHP将配置值设置为变量 [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) 关联阵列。 您可以在运行商务时运行的任何PHP脚本中设置值。

>[!TIP]
>
>在中设置变量值 `index.php` 或 `pub/index.php` 并非始终按预期运行，因为可根据web服务器配置使用不同的应用程序入口点。 通过放置 `$_ENV` 指令 `app/bootstrap.php` 文件，而不考虑不同的应用程序入口点 `$_ENV` 自从 `app/bootstrap.php` 文件作为商务架构的一部分加载。

设置2的示例 `$_ENV` 值如下：

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

分步示例如 [使用环境变量设置配置值](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- 使用您在 `$_ENV` 数组，必须设置 `variables_order = "EGPCS"`（环境、获取、发布、Cookie和服务器） `php.ini` 文件。 有关详细信息，请参阅 [PHP文档](https://www.php.net/manual/en/ini.core.php).
>
>- 对于云基础架构上的Adobe Commerce，如果您尝试使用 [项目Web界面](https://devdocs.magento.com/cloud/project/project-webint-basic.html#project-conf-env-var)，则必须在变量名称的前面添加 `env:`. 例如：
>
>![环境变量示例](https://devdocs.magento.com/common/images/cloud/cloud_env_var_example.png)
