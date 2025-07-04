---
title: ACSD-51294：价格、数量、税额、运输、作为字符串发送到 [!DNL Google Analytics] 的收入和GTM
description: 应用ACSD-51294修补程序以修复Adobe Commerce问题，该问题导致价格、数量、税务、运费和收入作为字符串发送到 [!DNL Google Analytics] 和GTM。
feature: Orders, Shipping/Delivery, Variables
role: Admin
exl-id: 99d2a311-2543-4007-99fd-6c34a2950773
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51294：价格、数量、税、运输、收入作为字符串发送到[!DNL Google Analytics]和GTM

ACSD-51294修补程序修复了将价格、数量、税务、运输和收入作为字符串发送到[!DNL Google Analytics]和GTM的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.32时，此修补程序可用。 修补程序ID为ACSD-51294。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans>)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

价格、数量、税、运费和收入将作为字符串发送到[!DNL Google Analytics]和GTM。

<u>重现步骤</u>：

1. 导航到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** > **[!UICONTROL Google GTag]** > **[!UICONTROL Google Analytics4]**&#x200B;以配置[!DNL Google Tag Manager]。
2. 创建一个简单的产品。
3. 使用该产品完成结帐。
4. 在签出成功页面上检查`dataLayer` JavaScript变量。

<u>预期的结果</u>

价格和数量值为数字。

<u>实际结果</u>

价格和数量值为字符串。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans>)。
