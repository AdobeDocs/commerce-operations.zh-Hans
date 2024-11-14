---
title: “ACSD-61553：应用具有不同优先级的多个折扣时，[!UICONTROL Cart Price Rule]计算不正确”
description: 应用ACSD-61553修补程序以解决在应用具有不同优先级的多个折扣时，未正确计算[!UICONTROL Cart Price Rule]的Adobe Commerce问题。
feature: Shopping Cart, Price Rules
role: Admin, Developer
source-git-commit: 299cdaaeb1a97697125cd990a9387d5245226f1d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-61553：应用具有不同优先级的多个折扣时，[!UICONTROL Cart Price Rule]计算不正确

ACSD-61553修补程序修复了在应用具有不同优先级的多个折扣时[!UICONTROL Cart Price Rule]被错误计算的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.53时，此修补程序可用。 修补程序ID为ACSD-61553。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.5-p8

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当应用具有不同优先级的多个折扣时，[!UICONTROL Cart Price Rule]计算不正确。

<u>重现步骤</u>：

1. 创建一个价格为$9,000的简单产品。
1. 创建一个[!UICONTROL Cart Price Rule]：固定折扣为$700的规则A，不附带任何条件且不放弃后续规则。
1. 创建另一个[!UICONTROL Cart Price Rule]：固定折扣为$1000的规则B，不附带任何条件且不放弃后续规则。
1. 将数量为13的产品添加到购物车。
1. 使用以下任意方案更新规则：

   场景01

       规则A
       优先级： 1
       最大数量折扣应用于： 1
       
       规则B
       优先级： 0
       最大数量折扣应用于： 0
   
   方案02

       规则A
       优先级： 0
       最大数量折扣应用于： 0
       
       规则B
       优先级： 1
       最大数量折扣应用于： 1
   
   场景03

       规则A
       优先级： 0
       最大数量折扣应用于： 0
       
       规则B
       优先级： 0
       最大数量折扣应用于： 1
   
1. 单击&#x200B;**[!UICONTROL Update Shopping Cart]**&#x200B;按钮以重新计算折扣。

<u>预期的结果</u>：

您可以看到不同方案的以下总折扣：

    方案01：$13,700
    方案02：$10,100
    方案03：$10,100

<u>实际结果</u>：

在这三种情况下，总折扣为$9,000。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!DNL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
