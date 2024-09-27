---
title: 'ACSD-54324： GraphQL requisition_lists请求不考虑分页设置'
description: 应用ACSD-54324修补程序以修复Adobe Commerce问题，该问题导致GraphQL“requisition_lists”请求不考虑分页设置并返回所有结果。
feature: B2B, Customers, GraphQL
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# ACSD-54324： GraphQL `requisition_lists`请求不考虑分页设置

ACSD-54324修补程序修复了GraphQL `requisition_lists`请求不考虑分页设置的问题并返回所有结果。 安装[!DNL Quality Patches Tool (QPT)] 1.1.41时，此修补程序可用。 修补程序ID为ACSD-54324。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

GraphQL `requisition_lists`请求不考虑分页设置并返回所有结果。

<u>重现步骤</u>：

1. 登录到管理员，然后导航到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**。

   * 将&#x200B;*[!UICONTROL Enable Requisition List]*&#x200B;设置为&#x200B;*是*。

1. 登录到前端，从顶部菜单或从&#x200B;**[!UICONTROL My Account]**&#x200B;转到&#x200B;**[!UICONTROL My Requisition Lists]**，然后创建多个申请（示例： 7）。
1. 生成客户令牌后，运行以下GraphQL `requisition_lists`客户查询。

   * 确保页面大小小于您创建的申请列表总数（例如：4）

   ```
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. 请注意，`total_count`字段的值显示7，而它应显示4。

   当项目数应与&#x200B;*页面大小*&#x200B;相同时，还显示7。

<u>预期的结果</u>：

* 列为&#x200B;*页面大小*&#x200B;的数字返回到`total_count`下，而不是返回记录总数。
* 项目数与&#x200B;*页面大小*&#x200B;相同。

<u>实际结果</u>：

在`total_count`下返回的总记录数，即使提及&#x200B;*页面大小*&#x200B;也是如此。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
