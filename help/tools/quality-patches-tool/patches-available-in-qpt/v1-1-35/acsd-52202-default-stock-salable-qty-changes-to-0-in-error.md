---
title: 'ACSD-52202：当非默认库存顺序设置为0数量时，默认库存可销售数量错误地更改为0'
description: 应用ACSD-52202修补程序以修复Adobe Commerce问题，该问题导致当订单中的非默认库存数量设置为0数量时，默认库存可销售数量错误地更改为0。
feature: Inventory, Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-52202：当订单中的非默认库存设置为0数量时，默认库存可销售数量错误地更改为0

ACSD-52202修补程序修复了当非默认库存设置为订单中的0数量时，默认库存可销售数量（数量）错误地更改为0的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.35时，此修补程序可用。 修补程序ID为ACSD-52202。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当订单中的非默认库存设置为0数量时，默认库存可销售数量错误地更改为0。

<u>重现步骤</u>：

1. 登录到[!DNL Admin]。
1. 创建&#x200B;**网站2**。
1. 创建自定义&#x200B;**源2**。
1. 创建自定义&#x200B;**stock2**。
1. 将&#x200B;**source2**&#x200B;和&#x200B;**stock2**&#x200B;分配给&#x200B;**website1**，并将默认源和库存分配给默认网站。
1. 创建简单产品并为默认源分配&#x200B;**qty** = *10*，为&#x200B;**source2**&#x200B;源分配&#x200B;**qty** = *1*。
1. 为&#x200B;**website2**&#x200B;下达含&#x200B;**数量** = *1*&#x200B;的订单。
1. 创建发票和装运。
1. 检查简单产品&#x200B;**可销售数量**。

<u>预期的结果</u>：

**源2**&#x200B;的&#x200B;**可销售数量** = *10*。

<u>实际结果</u>：

两个源的&#x200B;**可销售数量** = *0*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
