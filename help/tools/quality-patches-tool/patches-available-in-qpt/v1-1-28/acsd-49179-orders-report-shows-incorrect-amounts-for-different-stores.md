---
title: “ACSD-49179：订单报表显示不同商店的错误金额。”
description: 应用ACSD-49179修补程序以修复Adobe Commerce问题：如果不同商店使用不同的货币，订单报表会显示不正确的金额。
feature: Admin Workspace, Orders
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-49179：订单报表显示不同商店的错误金额

ACSD-49179修补程序修复了订单报表在不同商店使用不同货币时显示不正确金额的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28时，此修补程序可用。 修补程序ID为ACSD-49179。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果不同商店使用不同的币种，订单报表会显示不正确的金额。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]**&#x200B;并设置[!UICONTROL Catalog Price Scope] = [!UICONTROL Website]。
1. 创建其他网站、商店和商店视图。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL General]** > **[!UICONTROL Currency Setup]** > **[!UICONTROL Currency Options]**&#x200B;并设置：
   * 默认配置：
      * 基本货币：USD
      * 默认显示币种：USD
      * 允许的货币：欧元、美元和泰铢（泰铢）
   * 主网站：
      * 基础货币： EUR
      * 默认显示货币：EUR
      * 允许的币种：EUR
   * 其他新网站：
      * 基本货币：泰铢（泰铢）
      * 默认显示币种：THB（泰铢）
      * 允许的货币：泰铢（泰铢）
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Currency]** > **[!UICONTROL Currency Rates]**&#x200B;并设置THB的空转化率（将比率设置为1.0000）。
1. 创建一个产品，将其分配给两个网站，然后在之前创建的其他网站中订购此产品。
1. 确保订单处于&#x200B;*正在处理*&#x200B;状态（对其开票）。
1. 在后端，转到&#x200B;**[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**。
1. 单击&#x200B;**[!UICONTROL Yellow]**&#x200B;警告以刷新统计信息。
1. 在之前创建的其他网站上设置报告的范围，并设置过滤器，如下所示：
   * [!UICONTROL Date Used]： [!UICONTROL Created]
   * [!UICONTROL Period]： [!UICONTROL Day]
   * [!UICONTROL From and To]：发出测试订单的同一天
   * [!UICONTROL Order Status]： [!UICONTROL Any]
   * [!UICONTROL Empty rows]： [!UICONTROL No]
   * [!UICONTROL Show Actual Values]： [!UICONTROL No]

<u>预期的结果</u>：

销售总额显示折算为网站币种的正确金额。

<u>实际结果</u>：

总数为零。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
