---
title: “ACSD-59865：由于产品数量不足，[!UICONTROL Cart Price Rule]无法取消以前的规则”
description: 应用ACSD-59865修补程序以修复Adobe Commerce问题，其中*固定金额折扣*、* *产品价格折扣百分比*和*购买X获取Y* [!UICONTROL Cart Price Rules]中的*折扣数量步骤*值不再取消以前规则的操作。
feature: Price Rules
role: Admin, Developer
source-git-commit: 602a839708eab2551bd99a4f24e66edbde511150
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-59865：由于产品数量不足，[!UICONTROL Cart Price Rule]无法取消以前的规则

ACSD-59865修补程序修复了&#x200B;*[!UICONTROL Fixed amount discount]、* *[!UICONTROL Percent of product price discount]、*&#x200B;和&#x200B;*[!UICONTROL Buy X get Y]* [!UICONTROL Cart Price Rules]中的&#x200B;*[!UICONTROL Discount quantity step]*&#x200B;值不再取消以前规则的操作的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52时，此修补程序可用。 修补程序ID为ACSD-59865。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

由于购物车中的产品数量不足，[!UICONTROL Cart Price Rule]无法取消以前应用的规则。

<u>重现步骤</u>：

1. 以管理员身份登录。
1. 转到&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**&#x200B;并单击&#x200B;**[!UICONTROL Add New rule]**。
   * 设置&#x200B;**[!UICONTROL Rule Name]** = *测试 — 1*
   * 选择所有&#x200B;*网站*&#x200B;和&#x200B;*客户组*
   * 设置&#x200B;**[!UICONTROL Priority]** = *0*
   * 转到&#x200B;**[!UICONTROL Actions]**&#x200B;部分：
      * 设置&#x200B;**[!UICONTROL Apply]** = *产品价格折扣百分比*
      * 设置&#x200B;**[!UICONTROL Discount amount]** = *10*
      * 设置&#x200B;**[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * 设置&#x200B;**[!UICONTROL Discount Qty Step (Buy X)]** = *0*
      * 将&#x200B;**[!UICONTROL Discard subsequent rules]**&#x200B;设置为&#x200B;*否*
1. 清除缓存。
1. 转到店面，将一个项目添加到购物车，然后转到&#x200B;*结帐/购物车*。
1. 验证购物车是否应用了&#x200B;*10%*&#x200B;折扣。
1. 返回&#x200B;**[!UICONTROL Cart Price Rules]**&#x200B;并创建新规则。
   * 设置&#x200B;**[!UICONTROL Rule Name]** = *测试 — 2*
   * 选择所有&#x200B;**[!UICONTROL Websites]**&#x200B;和&#x200B;**[!UICONTROL Customer Groups]**
   * 设置&#x200B;**[!UICONTROL Priority]** = *2*
   * 导航到&#x200B;**[!UICONTROL Actions]**&#x200B;部分：
      * 设置&#x200B;**[!UICONTROL Apply]** = *产品价格折扣百分比*
      * 设置&#x200B;**[!UICONTROL Discount amount]** = *20*
      * 设置&#x200B;**[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * 设置&#x200B;**[!UICONTROL Discount Qty Step (Buy X)]** = *3*
1. 清除缓存。
1. 再回店面去。
1. 更新购物车以刷新规则。 验证是否不再应用&#x200B;*10%*&#x200B;折扣。
1. 将项目添加到购物车，直到数量达到第二个规则所需的&#x200B;*Step*&#x200B;值。

<u>预期的结果</u>：

当满足第二个规则的条件时，将应用第一个[!UICONTROL Cart Price Rule]。

<u>实际结果</u>：

价格规则按照在管理员功能板中的配置应用。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
