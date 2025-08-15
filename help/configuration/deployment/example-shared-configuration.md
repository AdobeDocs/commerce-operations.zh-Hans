---
title: 使用共享配置的示例
description: 请参阅有关如何使用共享配置文件更改开发系统中的设置的示例。
exl-id: c980ec01-ca2d-43db-b68d-8e9435e07e6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# 使用共享配置的示例

此示例说明如何在开发系统中更改以下设置，在生成系统中更新共享配置文件`config.php`，以及在生产系统中实施相同的设置：

- 时区
- 重量单位

这些设置可在&#x200B;**商店** >设置> **配置** >常规> **常规**&#x200B;中的管理员中使用。

您可以使用相同的过程来配置以下引用中的任何非敏感、非系统特定的设置：

- [其他配置路径参考](../reference/config-reference-general.md)
- [支付配置路径参考](../reference/config-reference-payment.md)
- [Commerce Enterprise B2B扩展配置路径参考](../reference/config-reference-b2b.md)

## 开始之前

在开始之前，请按照[开发、生成和生产系统的先决条件](../deployment/prerequisites.md)中所述设置文件系统权限和所有权。

## 假设

本主题提供了修改生产系统配置的示例。 您可以根据需要选择不同的配置选项。

在本例中，我们假定：

- 您使用Git源代码控制
- 开发系统在名为`mconfig`的Git远程存储库中可用
- 您的Git工作分支名为`m2.2_deploy`

## 步骤1：在开发系统中设置配置

要在开发系统中设置时区和重量单位，请执行以下操作：

1. 登录到管理员。
1. 单击“**存储**”>“设置”>“**配置**”>“常规”>“**常规”**。
1. 在右窗格中，展开&#x200B;**区域设置选项**。

   下图显示了一个示例。

   ![在开发系统中设置区域设置选项](../../assets/configuration/split-deploy-set-locale.png)

1. 从&#x200B;**时区**&#x200B;列表中，单击&#x200B;**GMT+00:00 (UTC)**。
1. 清除&#x200B;**重量单位**&#x200B;字段旁边的&#x200B;**使用系统值**&#x200B;复选框。
1. 从&#x200B;**重量单位**&#x200B;列表中，单击&#x200B;**公斤**。
1. 单击&#x200B;**保存配置**。
1. 如果出现提示，请刷新缓存。

## 第2步：更新共享配置

在开发系统中生成共享配置文件`app/etc/config.php`，并使用源代码管理将其传输到生成系统，如本节所述。

{{$include /help/_includes/config-save-config.md}}

## 步骤3：更新构建系统并生成文件

现在，您已将共享配置的更改提交到源代码管理，您可以在构建系统中提取这些更改，编译代码并生成静态文件。 最后一步是将这些更改拉入您的生产系统。 因此，生产系统的配置将与开发系统匹配。

{{$include /help/_includes/config-update-build-system.md}}

## 步骤4：更新生产系统

该流程的最后一步是从源代码管理更新您的生产系统。 这会拉取您在开发和构建系统时所做的所有更改，这意味着您的生产系统处于完全最新状态。

{{$include /help/_includes/config-update-prod-system.md}}

### 验证管理员中的更改

**验证这些设置在Admin**&#x200B;中不可编辑：

1. 登录到管理员。
1. 单击“**存储**”>“设置”>“**配置**”>“常规”>“**常规”**。
1. 在右窗格中，展开&#x200B;**区域设置选项**。

   您刚刚设置的选项显示如下：

   ![配置选项在管理员中不可编辑](../../assets/configuration/split-deploy-not-editable.png)

>[!INFO]
>
>要更改管理员中锁定的设置，请使用[`magento config:set --lock`命令](../cli/set-configuration-values.md)。
