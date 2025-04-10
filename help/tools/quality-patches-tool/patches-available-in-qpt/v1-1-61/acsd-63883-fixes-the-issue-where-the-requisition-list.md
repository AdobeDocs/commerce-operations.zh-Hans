---
title: ACSD-63883：正在修复[!UICONTROL Requisition List]的 [!DNL GraphQL] 响应中错误的“items_count”
description: 应用ACSD-63883修补程序以修复以下问题：[!UICONTROL Requisition List]在 [!DNL GraphQL] 响应中返回错误的“items_count”。
feature: B2B, GraphQL
role: Admin, Developer
source-git-commit: 5d8b78588b11534828a9b925cbab0cc945860367
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# ACSD-63883：修复了[!UICONTROL Requisition List]的[!DNL GraphQL]响应中的错误`items_count`

ACSD-63883修补程序修复了&#x200B;**[!UICONTROL Requisition List]**&#x200B;在[!DNL GraphQL]响应中返回错误的`items_count`的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61时，此修补程序可用。 修补程序ID为ACSD-63883。 请注意，该问题计划在Adobe Commerce B2B 1.5.3中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

**[!UICONTROL Requisition List]**&#x200B;在[!DNL GraphQL]响应中返回错误的`items_count`。


<u>重现步骤</u>：

1. 启用B2B **[!UICONTROL Requisition List]**&#x200B;功能。
1. 创建几个产品。
1. 创建客户帐户。
1. 单击&#x200B;**[!UICONTROL Create new Requisition List]**。
1. 发送带有产品的`addProductsToRequisitionList` [!DNL GraphQL]突变请求以将其添加到[!UICONTROL Requisition List]。

   ```
   mutation addProductsToRequisitionList(
   $requisitionListUid: ID!
   $requisitionListItems: [RequisitionListItemsInput!]!
   ) {
   addProductsToRequisitionList(
   requisitionListUid: $requisitionListUid
   requisitionListItems: $requisitionListItems
   ) {
   requisition_list
   { uid name description items_count }
   }
   }
   ```

1. 发送带有三个其他产品的`addProductsToRequisitionList` [!DNL GraphQL]突变请求以将其添加到[!UICONTROL Requisition List]。
1. 检查响应中的`items_count`。

**预期的结果**：

* `items_count`：响应中应返回4。

**实际结果**：

* `items_count`：响应中返回了2。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
