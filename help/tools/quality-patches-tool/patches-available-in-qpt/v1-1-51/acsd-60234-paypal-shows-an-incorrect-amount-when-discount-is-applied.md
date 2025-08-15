---
title: ACSD-60234： [!DNL PayPal] 在应用折扣时显示不正确的金额
description: 应用ACSD-60234修补程序以修复Adobe Commerce问题，该问题导致在通过付款方式应用折扣时， [!DNL PayPal] 显示不正确的金额。
feature: Products, Configuration
role: Admin, Developer
exl-id: 2ce7bde5-02a4-4989-80d6-ab1be0ca5fe9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-60234：应用折扣时，[!DNL PayPal]显示不正确的金额

ACSD-60234修补程序修复了在通过付款方式应用折扣时[!DNL PayPal]显示不正确金额的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.51时，此修补程序可用。 修补程序ID为ACSD-60234。 请注意，该问题计划在Adobe Commerce 2.5.0中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过付款方式应用折扣时，[!DNL PayPal]显示不正确的金额。

<u>重现步骤</u>：

1. 在&#x200B;*[!DNL PayPal Express]* > **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment methods]** > **[!DNL PayPal]**&#x200B;中配置&#x200B;**[!UICONTROL Express checkout]**。
   * [!UICONTROL Enable In-Context Checkout]可以是[!UICONTROL Yes]或[!UICONTROL NO]，在这两种情况下问题都会重现。
1. 在&#x200B;*[!UICONTROL Cart Rule]* > **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]**&#x200B;中创建一个&#x200B;**[!UICONTROL Add New Rule]**。
   * 条件：如果所有这些条件都为true： *[!UICONTROL Payment Method]*&#x200B;为&#x200B;*[!DNL PayPal Express Checkout]*。
   * 操作：任何操作。
1. 创建产品。
1. 转到店面，将产品添加到购物车，然后转到结帐中的&#x200B;**[!UICONTROL Payment Method]**&#x200B;步骤。
1. 确保选择&#x200B;*[!DNL PayPal Express]*&#x200B;并验证是否正确应用了折扣。
1. 单击&#x200B;**[!DNL PayPal]**&#x200B;按钮。
1. 登录并观察弹出窗口的内容。

<u>预期的结果</u>：

要支付给[!DNL PayPal]的金额包括购物车中的折扣。

<u>实际结果</u>：

要支付的总金额不包括折扣。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!DNL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
