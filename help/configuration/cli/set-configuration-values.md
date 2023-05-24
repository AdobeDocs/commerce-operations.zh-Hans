---
title: 设置配置值
description: 了解如何设置配置值并更改管理员中锁定的值。
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 0%

---

# 设置配置值

{{file-system-owner}}

本主题讨论可用于以下操作的高级配置命令：

- 从命令行设置任何配置选项
- （可选）锁定任何配置选项，使其值无法在Admin中更改
- 更改在Admin中锁定的配置选项

您可以使用这些命令手动或使用脚本设置Commerce配置。 使用设置配置选项 _配置路径_，即 `/`唯一标识该配置选项的分隔字符串。 您可以在以下引用中找到配置路径：

- [敏感和系统特定的配置路径引用](../reference/config-reference-sens.md)
- [支付配置路径参考](../reference/config-reference-payment.md)
- [常规配置路径参考](../reference/config-reference-general.md)
- [Commerce Enterprise B2B扩展配置路径参考](../reference/config-reference-b2b.md)

可以在以下时间设置值：

- 在安装Commerce之前，您可以仅为默认范围设置配置值，因为它是唯一的有效范围。

- 安装Commerce后，您可以为任何网站或商店视图范围设置配置值。

使用以下命令：

- `bin/magento config:set` 按其配置路径设置任何非敏感配置值
- `bin/magento config:sensitive:set` 按其配置路径设置任何敏感配置值
- `bin/magento config:show` 显示已保存的配置值；加密设置的值显示为星号

## 先决条件

要设置配置值，您必须至少知道以下内容之一：

- 配置路径
- 要设置特定范围的配置值，您必须知道范围代码。

   要设置默认范围的配置值，您无需执行任何操作。

### 查找配置路径

请参阅以下引用：

- [敏感和系统特定的配置路径引用](../reference/config-reference-sens.md)
- [支付配置路径参考](../reference/config-reference-payment.md)
- [其他配置路径参考](../reference/config-reference-general.md)
- [Commerce Enterprise B2B扩展配置路径参考](../reference/config-reference-b2b.md)

### 查找范围代码

您可以在Commerce数据库或Commerce管理员中找到范围代码。

**在“管理员”中查找范围代码**：

1. 以可以查看网站和商店查看的用户身份登录到管理员。
1. 单击 **[!UICONTROL Stores]** >设置> **[!UICONTROL All Stores]**.
1. 在右侧窗格中，单击网站或商店视图的名称以查看其代码。

   下图显示了一个示例网站代码。

   ![从管理员获取网站或商店视图代码](../../assets/configuration/website-code.png)

1. 继续使用 [设置值](#set-values).

**在数据库中查找范围代码**：

网站和商店视图的范围代码存储在Commerce数据库中的 `store_website` 和 `store` 表。

1. 连接到Commerce数据库。

   ```bash
   mysql -u <Commerce database username> -p
   ```

1. 输入以下命令：

   ```shell
   use <Commerce database name>;
   ```

   ```shell
   SELECT * FROM store;
   ```

   ```shell
   SELECT * FROM store_website;
   ```

   以下是示例结果：

   ```terminal
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   使用中的值 `code` 列。

1. 继续下一部分。

## 设置值

**设置系统特定的配置值**：

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**设置敏感配置值**：

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

下表描述了 `set` 命令参数：

| 参数 | 描述 |
| --- | --- |
| `--scope` | 配置的范围。 可能的值包括 `default`， `website`，或 `store`. 默认为 `default`. |
| `--scope-code` | 配置的范围代码（网站代码或商店视图代码） |
| `-e or --lock-env` | 锁定值以便无法在管理员中编辑它，或者更改已在管理员中锁定的设置。 该命令将该值写入 `<Commerce base dir>/app/etc/env.php` 文件。 |
| `-c or --lock-config` | 锁定值以便无法在管理员中编辑它，或者更改已在管理员中锁定的设置。 该命令将该值写入 `<Commerce base dir>/app/etc/config.php` 文件。 此 `--lock-config` 选项覆盖 `--lock-env` 如果同时指定这两个选项，则不会出现这种情况。 |
| `path` | _必需_. 配置路径 |
| `value` | _必需_. 配置的值 |

>[!INFO]
>
>从Commerce 2.2.4开始， `--lock-env` 和 `--lock-config` 选项替换 `--lock` 选项。
>
>如果您使用 `--lock-env` 或 `--lock-config` 选项来设置或更改值，您必须使用 [`bin/magento app:config:import` 命令](../cli/import-configuration.md) 以在访问管理员或店面之前导入设置。

如果输入的配置路径不正确，此命令将返回错误

```text
The "wrong/config/path" does not exist
```

有关更多信息，请参阅以下部分之一：

- [设置可在管理员中编辑的配置值](#set-configuration-values-that-can-be-edited-in-the-admin)
- [设置无法在管理员中编辑的配置值](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### 设置可在管理员中编辑的配置值

使用 `bin/magento config:set` _不含_ `--lock-env` 或 `--lock-config` 将值写入数据库。 您通过这种方式设置的值可以在管理员中进行编辑。

下面是一些设置存储基本URL的示例：

设置默认范围的基本URL：

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

设置基本URL `base` 网站：

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

设置基本URL `test` 存储视图：

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### 设置无法在管理员中编辑的配置值

如果您使用 `--lock-env`  选项，该命令将配置值保存在 `<Commerce base dir>/app/etc/env.php` 和禁用字段以在管理员中编辑此值。

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

您可以使用 `--lock-env` 如果未安装Commerce，则用于设置配置值的选项。 但是，只能为缺省范围设置值。

>[!INFO]
>
>此 `env.php` 文件特定于系统。 您不应将其传输到其他系统。 您可以使用它覆盖数据库中的配置值。 例如，您可以从另一个系统中获取数据库转储并覆盖 `base_url` 和其他值，因此您不必修改数据库。

如果您使用 `--lock-config` 选项，配置值将保存在 `<Commerce base dir>/app/etc/config.php`. 管理员中用于编辑此值的字段已禁用。

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

您可以使用 `--lock-config` 以设置配置值（如果未安装Commerce）。 但是，只能为缺省范围设置值。

>[!INFO]
>
>您可以传输 `config.php` 到另一个系统以使用相同的配置值。 例如，如果您有一个测试系统，则使用相同的 `config.php` 意味着您不必再次设置相同的配置值。

## 显示配置设置的值

命令选项：

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

位置

- `--scope` 是配置的范围（默认、网站、商店）。 默认值为 `default`
- `--scope-code` 是配置的范围代码（网站代码或商店视图代码）
- `path` 是格式为first_part/second_part/third_part/etc的配置路径(_必需_)

>[!INFO]
>
>此 `bin/magento config:show` 命令显示任意值 [加密值](../reference/config-reference-sens.md) 以星号表示： `******`.

### 示例

**显示所有保存的配置**：

```bash
bin/magento config:show
```

结果：

```terminal
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**要显示的所有已保存配置，请执行以下操作 `base` 网站**：

```bash
bin/magento config:show --scope=websites --scope-code=base
```

结果：

```terminal
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**显示默认范围的基本URL**：

```bash
bin/magento config:show web/unsecure/base_url
```

结果：

```terminal
web/unsecure/base_url - http://example.com/
```

**显示基本URL `base` 网站**：

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

结果：

```terminal
web/unsecure/base_url - http://example-for-website.com/
```

**显示基本URL `default` 存储**：

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

结果：

```terminal
web/unsecure/base_url - http://example-for-store.com/
```
