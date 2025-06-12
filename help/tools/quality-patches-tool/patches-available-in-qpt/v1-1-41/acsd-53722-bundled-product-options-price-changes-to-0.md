---
title: ACSD-53722：捆绑产品选项价格更改为$0
description: 应用ACSD-53722修补程序以修复Adobe Commerce问题：当针对不同领域的计划更新生效时，捆绑产品选项的价格将更改为$0。
feature: Products
role: Admin, Developer
exl-id: 2e974a6a-0c79-442f-9b45-b4edf831a052
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-53722：捆绑产品选项价格更改为$0

ACSD-53722修补程序修复了当不同范围的计划更新生效时，捆绑产品选项的价格更改为$0的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41时，此修补程序可用。 修补程序ID为ACSD-53722。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当不同范围的计划更新生效时，捆绑产品选项的价格将更改为$0。

<u>重现步骤</u>：

1. 创建两个网站A和B。
1. 在&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** = **[!UICONTROL Website]**&#x200B;下设置配置。
1. 在网站A和B上创建固定价格的捆绑产品：

   * 捆绑产品价格=固定= *0*

1. 添加一个简单产品作为捆绑包的下拉选项。 设置以下价格：

   * 捆绑选项中简单产品的所有商店视图价格= *120*
   * 简单产品网站A price inside bundled option = *130*
   * 捆绑选项中简单产品网站B的价格= *140*

1. 计划更新以禁用网站A上的捆绑产品。

<u>预期的结果</u>：

网站A的计划更新不会影响网站B的价格。

<u>实际结果</u>：

在计划更新后，网站B上捆绑产品选项的价格更改为&#x200B;**$0**。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
