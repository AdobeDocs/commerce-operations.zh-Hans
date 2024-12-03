---
title: ACSD-48293：复合产品缺货时补充库存的子产品
description: 应用ACSD-48293补丁以修复组合产品在缺货子产品恢复库存时缺货的Adobe Commerce问题。
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: 2aa75e97-373e-4e4a-a545-69bce807ca4d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-48293：复合产品缺货时补充库存的子产品

ACSD-48293修补程序修复了将已售出的子产品恢复库存时复合产品缺货的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25时，此修补程序可用。 修补程序ID为ACSD-48293。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

组合产品在售出的子产品返回到库存时缺货。

<u>重现步骤</u>：

1. 创建辅助网站、商店和商店视图。
1. 创建两个源和库存，并将它们分配给每个网站。
1. 在&#x200B;**[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*&#x200B;下启用显示缺货产品选项。
1. 使用主网站的库存来源（设置数量= 1）创建一个带有一个关联产品的可配置产品。
1. 为可配置产品下订单。
1. 快去开箱。
1. 从店面打开可配置产品并确认其缺货。
1. 从[!UICONTROL Admin]中打开可配置产品并将&#x200B;**[!UICONTROL Manage Stock Option]**&#x200B;设置为&#x200B;*[!UICONTROL No]*。
1. 快去开箱。
1. 发送订单并将数量添加到简单产品中，使其备货。
1. 快去开箱。
1. 检查店面上的产品可用性。

<u>预期的结果</u>：

该可配置产品有库存。

<u>实际结果</u>：

可配置产品缺货。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
