---
title: ACSD-46988：GraphQL货币API请求返回null值
description: ACSD-46988修补程序修复了GraphQL货币API请求为自定义货币返回null值的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21后，即可使用此修补程序。 修补程序ID为ACSD-46988。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
feature: REST, GraphQL
role: Admin
exl-id: 276d2c75-6e7f-4888-b4d2-ac96bea93fc1
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-46988：GraphQL货币API请求返回null值

ACSD-46988修补程序修复了GraphQL货币API请求为自定义货币返回null值的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21时，此修补程序可用。 修补程序ID为ACSD-46988。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

GraphQL货币API请求为自定义货币返回null值。

<u>重现步骤</u>：

1. 在Admin中配置自定义货币。 转到&#x200B;**系统** > **配置** > **常规** > **货币设置**。
1. 发送包含以下有效负载的GraphQL请求：

<pre>
<code class="language-graphql">
{
    currency {
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates {
            currency_to
            rate
        }
    }
}
</code>
</pre>

<u>预期的结果</u>：

该请求返回货币值而不是null值。

<u>实际结果</u>：

该请求返回多个null值。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： Quality Patches Tool指南中的[Quality Patches Tools >用法](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 安装修补程序后所需的其他步骤

对于内部部署用户：

* 运行： `composer require symfony/intl:"~5.4.11"`

对于云用户：

* 运行： `composer require symfony/intl:"~5.4.11"`
* 将`composer.json`和`composer.lock`文件连同修补程序文件一起推送到Git存储库。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅Quality Patches Tool指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
