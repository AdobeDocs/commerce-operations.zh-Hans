---
title: 使用环境变量的示例
description: 请参阅有关如何使用环境变量在开发系统中设置共享的、特定于系统的和敏感值的示例。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '1085'
ht-degree: 0%

---


# 使用环境变量的示例

此示例说明如何在开发系统中设置共享的、特定于系统的和敏感的值，然后使用共享配置的组合在生产系统中设置所有值， `config.php`、和PHP环境变量。

以下配置设置可以在开发系统和生产系统之间共享：

增值税编号和商店名称 **商店** >设置> **配置** >常规> **常规**

这些配置设置是特定于系统的，或是敏感的，如所示：

- 从以下来源向（敏感）发送电子邮件 **商店** >设置> **配置** >常规> **联系人**
- 默认电子邮件域（特定于系统） **商店** >设置> **配置** >客户> **客户配置** > **创建新帐户选项**

您可以使用相同的过程在以下引用中配置任何设置：

- [敏感和特定于系统的配置路径引用](../reference/config-reference-sens.md)
- [付款配置路径参考](../reference/config-reference-payment.md)
- [常规配置路径引用](../reference/config-reference-general.md)
- [商务企业B2B扩展配置路径参考](../reference/config-reference-b2b.md)

## 开始之前

在开始之前，按 [开发、构建和生产系统的先决条件](../deployment/prerequisites.md).

## 假设

本主题提供了修改生产系统配置的示例。 您可以根据需要选择不同的配置选项。

在本例中，我们假定：

- 您使用Git源控件
- 开发系统位于名为的Git远程存储库中 `mconfig`
- 您的Git工作分支已命名 `m2.2_deploy`

## 步骤1:在开发系统中设置配置

要在开发系统中设置默认区域设置和权重单位，请执行以下操作：

1. 登录到管理员。
1. 单击 **商店** >设置> **配置** >常规> **常规**.
1. 如果您有多个网站可用，请使用 **存储视图** 列表，以切换到其他网站，如下图所示。

   ![切换网站](../../assets/configuration/split-deploy-switch-website.png)

1. 在右侧窗格中，展开 **存储信息**.
1. 如有必要，请清除 **使用默认值** 复选框 **增值税号** 字段。
1. 在字段中输入数字(例如， `12345`)。
1. 在 **存储名称** 字段，输入值(例如 `My Store`)。
1. 单击 **保存配置**.
1. 使用 **存储视图** 列表以选择 **默认配置** 如下图所示。

   ![切换到默认配置](../../assets/configuration/split-deploy-default-config.png)

1. 在左侧导航中的“常规”下，单击 **联系人**.
1. 清除 **使用默认值** 复选框 **向发送电子邮件** 字段。
1. 在字段中输入电子邮件地址。
1. 单击 **保存配置**.
1. 在左窗格中，单击客户> **客户配置**.
1. 在右侧窗格中，展开 **创建新帐户选项**.
1. 清除 **使用系统值** 复选框 **默认电子邮件域** 字段。
1. 在字段中输入域名。
1. 单击 **保存配置**.
1. 如果出现提示，请刷新缓存。

## 步骤2:更新配置

现在，您已更改管理员中的配置，请按照本节所述将共享配置写入文件。

{{$include /help/_includes/config-save-config.md}}

请注意，即使 `app/etc/env.php` （系统特定配置）已更新，请勿将其签入到源代码管理。 在此过程的后续步骤中，您将在生产系统上创建相同的配置设置。

## 步骤3:更新内部版本系统并生成文件

现在，您已将对共享配置所做的更改提交到源代码管理，接下来可以在生成系统中提取这些更改、编译代码并生成静态文件。 最后一步是将这些更改提取到您的生产系统。

{{$include /help/_includes/config-update-build-system.md}}

## 步骤4:更新生产系统

该过程的最后一步是更新您的生产系统。 必须分两部分完成：

- 更新敏感和系统特定的设置
- 更新共享设置

### 更新敏感和系统特定的设置

要使用环境变量设置敏感的和特定于系统的设置，您必须知道以下信息：

- 每个设置的范围

   如果您按照步骤1中的说明操作，则“发送电子邮件至”的范围是全局的（即默认配置范围），“默认电子邮件域”的范围是网站。

   您必须知道网站的代码才能设置默认电子邮件域配置值。 请参阅 [使用环境变量覆盖配置设置](../reference/override-config-settings.md#environment-variables) 以了解有关查找该域的详细信息。

- 每个设置的配置路径

   此示例中使用的配置路径如下所示：

   | 设置名称 | 配置路径 |
   |--------------|--------------|
   | 向发送电子邮件 | `contact/email/recipient_email` |
   | 默认电子邮件域 | `customer/create_account/email_domain` |

   您可以在 [敏感和特定于系统的配置路径引用](../reference/config-reference-sens.md).

#### 将配置路径转换为变量名称

如 [使用环境变量覆盖配置设置](../reference/override-config-settings.md#environment-variables)，变量的格式为：

```text
<SCOPE>__<SYSTEM__VARIABLE__NAME>
```

的值 `<SCOPE>` is `CONFIG__DEFAULT__` 全局范围或 `CONFIG__WEBSITES__<WEBSITE CODE>` 网站范围。

查找 `<SYSTEM__VARIABLE__NAME>`，替换每个 `/` 配置路径中的字符。

变量名称如下：

| 名称 | 配置路径 | 变量名称 |
|--------------|--------------|--------------|
| 向发送电子邮件 | `contact/email/recipient_email` | `CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL` |
| 默认电子邮件域 | `customer/create_account/email_domain` | `CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN` |

>[!INFO]
>
>上表包含网站代码示例， `BASE`，用于默认电子邮件域配置设置。 替换 `BASE` 和您商店的相应网站代码。

#### 使用环境变量设置变量

您可以在 `index.php` 使用以下格式：

```php
$_ENV['VARIABLE'] = 'value';
```

**设置变量值**:

1. 以文件系统所有者的身份登录到生产系统，或切换到。
1. 打开 `<Commerce root dir>/pub/index.php` 在文本编辑器中。
1. 任意位置 `index.php`，请为变量设置类似于以下内容的值：

   ```php
   $_ENV['CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL'] = 'myname@example.com';
   $_ENV['CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN'] = 'magento.com';
   ```

1. 将更改保存到 `pub/index.php` 并退出文本编辑器。
1. 继续下一节。

### 更新共享设置

本节将讨论如何提取您在开发和构建系统上所做的所有更改，以更新共享配置设置（存储名和增值税号）。

{{$include /help/_includes/config-update-prod-system.md}}

### 验证管理员中的配置设置

本节将讨论如何在生产系统管理员中验证配置设置。

**验证配置设置**:

1. 登录到生产系统的管理员。
1. 单击 **商店** >设置> **配置** >常规> **常规**.
1. 使用 **存储视图** 列表，以切换到其他网站。

   您在开发系统中设置的共享配置选项如下所示。

   ![检查生产系统中的设置](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >的 **存储名称** 字段可在网站范围中编辑，但如果您切换到默认配置范围，则该字段将不可编辑。 这是您在开发系统中设置选项的结果。 的值 **增值税号** 在网站范围中不可编辑。

1. 如果尚未执行此操作，请切换到默认配置范围。
1. 在左侧导航中的“常规”下，单击 **联系人**.

   的 **向发送电子邮件** 字段，如下图所示。 这是一个敏感设置。

   ![检查生产系统中的设置](../../assets/configuration/split-deploy-verify-contacts.png)

1. 在左窗格中，单击客户> **客户配置**.
1. 在右侧窗格中，展开 **创建新帐户选项**.

   的值 **默认电子邮件域** 字段，如下所示。 这是特定于系统的设置。

   ![检查生产系统中的设置](../../assets/configuration/split-default-domain.png)
