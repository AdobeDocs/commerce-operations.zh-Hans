---
title: ACSD-53658：**[!UICONTROL Recently Viewed Product]**数据未在存储视图中正确更新
description: 应用ACSD-53658修补程序以修复存储视图中无法正确更新**[!UICONTROL Recently Viewed Product]**数据的Adobe Commerce问题。
feature: CMS, Personalization
role: Admin, Developer
exl-id: a91fac3d-cb6f-4f65-aec2-d28cee4fd39f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-53658：未在存储视图中正确更新&#x200B;**[!UICONTROL Recently Viewed Product]**&#x200B;数据

ACSD-53658修补程序修复了存储视图中&#x200B;**[!UICONTROL Recently Viewed Product]**&#x200B;数据未正确更新的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42时，此修补程序可用。 修补程序ID为ACSD-53658。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

存储视图中的&#x200B;**[!UICONTROL Recently Viewed Product]**&#x200B;数据未正确更新。

<u>重现步骤</u>：

1. 登录到“管理”面板。
1. 为默认网站创建第二个商店视图。
1. 创建一个简单的产品。
1. 为新商店视图设置其他产品名称。
1. 创建&#x200B;**[!UICONTROL Recently Viewed Product]**&#x200B;构件。
1. 配置此构件以在主页上显示。
1. 从默认商店视图中打开店面上的产品页面。
1. 打开主页。
1. 通过使用存储切换器，切换到第二个存储视图。

<u>预期的结果</u>：

产品名称将在小部件中更新。

<u>实际结果</u>：

小部件中的产品名称未更新。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)：搜索修补程序[!DNL Quality Patches Tool]。
