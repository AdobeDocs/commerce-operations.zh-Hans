---
title: 'ACSD-46617：小计大于配置的最小订单量时，**[!UICONTROL Continue to Checkout]**按钮灰显'
description: 应用ACSD-46617修补程序以解决Adobe Commerce问题，该问题导致**[!UICONTROL Continue to Checkout]**按钮灰显，即使小计大于配置的最小订单量也是如此。
feature: Checkout, Orders
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-46617：小计大于&quot;[!UICONTROL Minimum Order Amount]&quot;时，&quot;[!UICONTROL Continue to Checkout]&quot;按钮灰显

此ACSD-46617修补程序解决了&#x200B;**[!UICONTROL Continue to Checkout]**&#x200B;按钮灰显的问题，即使小计大于配置的最小订单量也是如此。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24时，此修补程序可用。 修补程序ID为ACSD-46617。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

即使小计大于配置的最小订单量，**[!UICONTROL Continue to Checkout]**&#x200B;按钮也会呈灰显状态。

<u>重现步骤</u>：

1. 转到Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]**&#x200B;并设置以下内容：
   * [!UICONTROL Enable]： *[!UICONTROL Yes]*
   * 
     [!UICONTROL Minimum Amount]: *2*

1. 创建一个[!UICONTROL Cart Price Rule]。
   * [!UICONTROL Coupon Code]： *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]： *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]：
      * [!UICONTROL Apply]： *[!UICONTROL Percent of product price discount]*
      * 
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]： *[!UICONTROL Yes]*
1. 创建价格为$25的产品。
1. 将产品添加到购物车。
1. 转到购物车，选择$5 **[!UICONTROL Flat Rate shipping]**&#x200B;方法并应用优惠券代码。
1. 转到结帐，完成送货，然后导航到&#x200B;**[!UICONTROL Paytment]**&#x200B;分区。
1. 返回购物车。

<u>预期的结果</u>：

最小订单金额没有错误，因为总计$2.4大于所需金额$2。

<u>实际结果</u>：

* 即使总计$2.4大于最小订单金额$2，最小订单金额仍然存在错误。
* **[!UICONTROL Continue to Checkout]**&#x200B;按钮呈灰显状态。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。