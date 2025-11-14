---
title: 设置配置值
description: 了解如何在Adobe Commerce中设置配置值和更改锁定的管理员值。 了解高级配置命令和技术。
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 5e2d11330d3334df36ba8b3d176fbe2d8bfe0486
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 0%

---

# 设置配置值

{{file-system-owner}}

本主题讨论可用于以下操作的高级配置命令：

- 从命令行设置任何配置选项
- （可选）锁定任何配置选项，使其值无法在管理员中更改
- 更改在Admin中锁定的配置选项

您可以使用这些命令手动或使用脚本设置Commerce配置。 您使用&#x200B;_配置路径_&#x200B;设置配置选项，该路径是一个以`/`分隔的字符串，用于唯一标识该配置选项。 您可在以下引用中找到配置路径：

- [敏感且特定于系统的配置路径参考](../reference/config-reference-sens.md)
- [支付配置路径参考](../reference/config-reference-payment.md)
- [常规配置路径引用](../reference/config-reference-general.md)
- [Commerce Enterprise B2B扩展配置路径参考](../reference/config-reference-b2b.md)

您可以在以下时间设置值：

- 在安装Commerce之前，您只能为默认范围设置配置值，因为它是唯一的有效范围。

- 安装Commerce后，您可以为任何网站或商店视图范围设置配置值。

使用以下命令：

- `bin/magento config:set`通过其配置路径设置任何非敏感配置值
- `bin/magento config:sensitive:set`根据其配置路径设置任何敏感配置值
- `bin/magento config:show`显示已保存的配置值；加密设置的值显示为星号

## 先决条件

要设置配置值，您必须至少知道以下内容之一：

- 配置路径
- 要设置特定范围的配置值，必须知道范围代码。

  要设置默认范围的配置值，您无需执行任何操作。

### 查找配置路径

请参阅以下引用：

- [敏感且特定于系统的配置路径参考](../reference/config-reference-sens.md)
- [支付配置路径参考](../reference/config-reference-payment.md)
- [其他配置路径参考](../reference/config-reference-general.md)
- [Commerce Enterprise B2B扩展配置路径参考](../reference/config-reference-b2b.md)

### 查找范围代码

您可以在Commerce数据库或Commerce管理员中找到范围代码。

**要在管理员中查找范围代码**：

1. 以可以查看网站和商店视图的用户身份登录到管理员。
1. 单击&#x200B;**[!UICONTROL Stores]** >设置> **[!UICONTROL All Stores]**。
1. 在右侧窗格中，单击网站或商店视图的名称以查看其代码。

   下图显示了一个示例网站代码。

   ![从管理员获取网站或商店视图代码](../../assets/configuration/website-code.png)

1. 继续设置[设置值](#set-values)。

**在数据库中查找作用域代码**：

网站和商店视图的范围代码分别存储在`store_website`和`store`表的Commerce数据库中。

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

   ```
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   使用`code`列中的值。

1. 继续下一部分。

## 设置值

**要设置系统特定的配置值**：

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**要设置敏感配置值**：

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path
```

下表描述了`set`命令参数：

| 参数 | 描述 |
| --- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `--scope` | 配置的范围。 可能的值为`default`、`website`或`store`。 默认值为`default`。 |
| `--scope-code` | 配置的范围代码（网站代码或商店视图代码） |
| `-e or --lock-env` | 锁定该值以便无法在管理员中对其进行编辑，或者更改已在管理员中锁定的设置。 该命令将该值写入`<Commerce base dir>/app/etc/env.php`文件。 |
| `-c or --lock-config` | 锁定该值以便无法在管理员中对其进行编辑，或者更改已在管理员中锁定的设置。 该命令将该值写入`<Commerce base dir>/app/etc/config.php`文件。 如果同时指定两个选项，`--lock-config`选项将覆盖`--lock-env`。 |
| `path` | _必需_。 配置路径 |
| `value` | _必需_。 配置的值。 虽然可以在CLI命令中将其作为单独的参数传递，但Adobe建议不要在原始命令中指定该参数。 相反，运行不带值的命令，然后在出现提示时输入值。 使用此方法可防止将敏感访问值写入bash_history ，这是设置配置的最安全方法。 |

>[!INFO]
>
>自Commerce 2.2.4起，`--lock-env`和`--lock-config`选项将替换`--lock`选项。 如果使用这两个选项中的任何一个，该值将直接写入`app/etc/env.php`或`app/etc/config.php`文件，并在管理员中变为只读。 要将配置更改从这些文件导入数据库，请运行`bin/magento app:config:import`命令 — 例如，在手动编辑或重新部署这些文件之后。

如果输入的配置路径不正确，此命令将返回错误

```text
The "wrong/config/path" does not exist
```

有关更多信息，请参阅以下部分之一：

- [设置可在管理员中编辑的配置值](#set-configuration-values-that-can-be-edited-in-the-admin)
- [设置无法在管理员中编辑的配置值](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### 设置可在管理员中编辑的配置值

使用`bin/magento config:set` _（不带_ `--lock-env`或`--lock-config`）将该值写入数据库。 您通过这种方式设置的值可以在管理员中进行编辑。

下面是设置商店基本URL的一些示例：

为默认范围设置基本URL：

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

为`base`网站设置基本URL：

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

设置`test`存储视图的基本URL：

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### 设置无法在管理员中编辑的配置值

如果按如下方式使用`--lock-env`选项，则该命令会将配置值保存在`<Commerce base dir>/app/etc/env.php`中，并禁用该字段以在管理员中编辑该值。

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

如果未安装Commerce，则可以使用`--lock-env`选项设置配置值。 但是，只能为默认范围设置值。

>[!INFO]
>
>`env.php`文件特定于系统。 请勿将其传输到其他系统。 您可以使用它覆盖数据库中的配置值。 例如，您可以从另一个系统获取数据库转储并覆盖`base_url`和其他值，这样您就不必修改数据库。

如果按如下方式使用`--lock-config`选项，则配置值保存在`<Commerce base dir>/app/etc/config.php`中。 管理员中用于编辑此值的字段已禁用。

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

如果未安装Commerce，则可以使用`--lock-config`设置配置值。 但是，只能为默认范围设置值。

>[!INFO]
>
>您可以将`config.php`传输到另一个系统，以便在该处使用相同的配置值。 例如，如果您有一个测试系统，则使用相同的`config.php`意味着您不必再次设置相同的配置值。

## 显示配置设置的值

命令选项：

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

位置

- `--scope`是配置的范围（默认、网站、商店）。 默认值为`default`
- `--scope-code`是配置的范围代码（网站代码或商店视图代码）
- `path`是格式为first_part/second_part/third_part/etc的配置路径(_required_)

>[!INFO]
>
>`bin/magento config:show`命令将任何[加密值](../reference/config-reference-sens.md)的值显示为一系列星号： `******`。

### 示例

**显示所有保存的配置**：

```bash
bin/magento config:show
```

结果：

```
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**要显示`base`网站**&#x200B;的所有已保存配置，请执行以下操作：

```bash
bin/magento config:show --scope=websites --scope-code=base
```

结果：

```
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**显示默认作用域**&#x200B;的基本URL：

```bash
bin/magento config:show web/unsecure/base_url
```

结果：

```
web/unsecure/base_url - http://example.com/
```

**要显示`base`网站**&#x200B;的基本URL，请执行以下操作：

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

结果：

```
web/unsecure/base_url - http://example-for-website.com/
```

**要显示`default`存储**&#x200B;的基本URL：

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

结果：

```
web/unsecure/base_url - http://example-for-store.com/
```

>[!INFO]
>
>范围代码只能包含字母（a-z或A-Z）、数字(0-9)和下划线(_)。 此外，第一个字符必须是字母。 如果在创建网站或商店视图时使用大写或驼峰式大小写，则在内部匹配不区分大小写，以适应通过环境变量覆盖配置设置。 请参阅[使用环境变量覆盖配置设置](../reference/override-config-settings.md#environment-variables)。

