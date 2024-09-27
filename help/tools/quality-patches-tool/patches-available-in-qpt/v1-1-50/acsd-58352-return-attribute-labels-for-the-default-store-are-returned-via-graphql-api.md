---
title: 'ACSD-58352：通过 [!DNL GraphQL] API返回默认存储的属性标签'
description: 应用ACSD-58352修补程序以修复Adobe Commerce问题，该问题导致在请求标头中指定了非默认存储视图时，通过 [!DNL GraphQL] API返回默认存储的属性标签。
feature: GraphQL, Returns
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---


# ACSD-58352：通过[!DNL GraphQL] API返回默认存储的属性标签

ACSD-58352修补程序修复了在请求标头中指定非默认存储视图时，通过[!DNL GraphQL] API返回默认存储的返回属性标签的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50时，此修补程序可用。 修补程序ID为ACSD-58352。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过[!DNL GraphQL] API返回默认存储的属性标签。

<u>重现步骤</u>：

1. 启用&#x200B;**[!UICONTROL Return Merchandising Authorization]**。
1. 在默认网站下创建&#x200B;*[!UICONTROL Additional Store]*&#x200B;和&#x200B;*[!UICONTROL Store View]*。
1. 编辑&#x200B;**[!UICONTROL Reason for Return]**&#x200B;返回属性并为所有存储视图添加标签。
1. 创建一个&#x200B;*[!UICONTROL Order]*。
1. 为该订单创建一个&#x200B;*[!UICONTROL Return]*。 确保&#x200B;*[!UICONTROL Return]*&#x200B;处于&#x200B;*[!UICONTROL Pending]*&#x200B;状态。
1. 在标头中使用指定的非默认[!UICONTROL Store View]发送客户[!DNL GraphQL]查询：

   ```
   query {
       customer {
           returns {
               items {
                   items {
                       custom_attributes {
                           label
                           value
                       }
                   }
               }
           }
       }
   }
   ```

1. 观察响应。

<u>预期的结果</u>

[!DNL GraphQL]响应中的返回标签针对的是请求标头中设置的[!UICONTROL Store View]。

<u>实际结果</u>：

[!DNL GraphQL]响应中的返回标签适用于默认[!UICONTROL Store View]。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
