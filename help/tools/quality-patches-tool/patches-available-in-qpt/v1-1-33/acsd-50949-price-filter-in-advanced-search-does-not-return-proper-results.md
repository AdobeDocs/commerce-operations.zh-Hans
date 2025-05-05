---
title: ACSD-50949：高级搜索中的价格过滤器在与SKU过滤器一起使用时未返回正确结果
description: 应用ACSD-50949补丁以修复Adobe Commerce问题，该问题导致高级搜索中的价格过滤器在与SKU过滤器一起使用时无法返回正确结果。
feature: Orders, Search
role: Admin
exl-id: 89e54940-e763-4554-8641-a162516bcabd
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 1%

---

# ACSD-50949：与SKU过滤器一起使用时，高级搜索中的价格过滤器未返回正确结果

ACSD-50949修补程序修复了高级搜索中的价格过滤器在与SKU过滤器一起使用时无法返回正确结果的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33时，此修补程序可用。 修补程序ID为ACSD-50949。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans>)上检查兼容性。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 问题

高级搜索中的价格过滤器在与SKU过滤器一起使用时未返回正确结果。

<u>重现步骤</u>：

1. 创建多个产品，例如：

   | SKU | 名称 | 价格 | 数量 |
   |-----|-----------|-------|----------|
   | 麦芽1 | 产品1 | 10美元 | 10 |
   | MJ2 | 产品2 | 15美元 | 10 |
   | 马航3型 | 产品3 | 21美元 | 10 |
   | 麦角四号 | 产品4 | 32美元 | 10 |
   | 马绍尔群岛航空 | 产品5 | 33美元 | 10 |
   | 麦剑6 | 产品6 | 34美元 | 10 |
   | 麦剑7 | 产品7 | 44美元 | 10 |

1. 在店面中打开&#x200B;**[!UICONTROL Advanced Search]**&#x200B;并按SKU搜索：“MJ”。
1. 单击&#x200B;**[!UICONTROL Modify your search]**&#x200B;链接。
1. 将价格范围添加到&#x200B;*1*&#x200B;到&#x200B;*21*&#x200B;的条件中，然后单击&#x200B;**[!UICONTROL Search]**&#x200B;按钮。

<u>预期的结果</u>：

只返回价格在定义范围内的产品。

<u>实际结果</u>：

返回价格高于&#x200B;*$21*&#x200B;的产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans>)。
