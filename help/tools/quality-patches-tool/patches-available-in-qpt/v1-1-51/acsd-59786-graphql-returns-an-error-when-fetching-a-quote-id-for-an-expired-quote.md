---
title: “ACSD-59786：GraphQL在获取过期报价的`quote_id`时返回错误”
description: 应用ACSD-59786修补程序以修复Adobe Commerce问题，该问题导致GraphQL查询在获取过期报价的“quote_id”时返回错误。
feature: GraphQL, Quotes, Companies
role: Admin, Developer
source-git-commit: fec2ee4a047d8b33fa1cb3b2c4d9364f925fa028
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-59786：GraphQL在获取过期报价的`quote_id`时返回错误

ACSD-59786修补程序修复了GraphQL查询在获取过期报价的`quote_id`时返回错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51时，此修补程序可用。 修补程序ID为ACSD-59786。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

GraphQL查询在获取过期报价的`quote_id`时返回错误。

<u>重现步骤</u>：

1. 启用&#x200B;**[!UICONTROL Companies]**&#x200B;和&#x200B;**[!UICONTROL Purchase Orders]**。
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**&#x200B;并将&#x200B;**[!UICONTROL Enable Company]**&#x200B;设置为&#x200B;*是*。
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** > **[!UICONTROL Order Approval Configuration]**&#x200B;并将&#x200B;**[!UICONTROL Enable Purchase Orders]**&#x200B;设置为&#x200B;*是*。
1. 创建新公司并将&#x200B;**[!UICONTROL Enable Purchase Orders]**&#x200B;设置为&#x200B;*是*。
1. 创建简单产品并将其分配给类别。
1. 使用公司管理员帐户登录Storefront，并使用&#x200B;**[!UICONTROL Purchase Order]**&#x200B;作为付款方式创建新订单。
1. 更改&#x200B;**[!UICONTROL Quote Lifetime (days)]**。
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Shopping Cart]** > **[!UICONTROL Quote Lifetime (days)]** = *0*。
1. 运行命令`bin/magento c:f`。
1. 转到DB `quote_table`并使用过去一天更改`created_at`和`updated_at`值。
1. 运行命令`bin/magento cron:run --group="sales_clean_quotes`。
1. 使用创建&#x200B;**[!UICONTROL Purchase Order]**&#x200B;的管理员的授权令牌执行下面给定的GraphQL请求：

   ```GraphQL
   {
       customer {
           purchase_order(uid: "MQ==") {
               quote {
                   id
               }
           }
       }
   } 
   ```

<u>预期的结果</u>：

GraphQL查询返回`quote_id`。

<u>实际结果</u>：

GraphQL查询返回内部服务器错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
