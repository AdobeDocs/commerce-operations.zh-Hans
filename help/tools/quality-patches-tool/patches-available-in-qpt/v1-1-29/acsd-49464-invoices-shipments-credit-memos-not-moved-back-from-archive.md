---
title: ACSD-49464：未从存档中移回的发票、发运和贷项通知单
description: 应用ACSD-49464修补程序以修复Adobe Commerce问题，该问题导致在orderId不同时，发票、发运和贷项通知单不会从存档中移回。
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: d9ccd043-cbd3-4be5-ab29-c5351da53030
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49464：未从存档中移回的发票、发运和贷项通知单

ACSD-49464修补程序修复了以下问题：当orderId不同时，发票、发运和贷项通知单不会从存档中移回。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29时，此修补程序可用。 修补程序ID为ACSD-49464。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当orderId不同时，不会将发票、发运和贷项通知单从存档中移回。

<u>重现步骤</u>：

1. 启用订单、发票、发运和贷项通知单存档。
1. 创建并完成订单，包括发运、发票和贷项通知单。
1. 确保发运、发票和贷项通知单ID与订单编号不同。
1. 移动订单以进行存档。
1. 将已存档的订单恢复至订单管理。
1. 在相应的[!UICONTROL Invoice]、[!UICONTROL Shipping]和[!UICONTROL Credit Memo]网格页下查看发票、运费和贷项通知单详细信息。

<u>预期的结果</u>：

将订单从存档列表移至订单管理后，将恢复原始相关记录。

<u>实际结果</u>：

* 如果所有ID不同，则没有发运、发票和贷项通知单记录。
* 如果订单和相关记录具有相同的ID，则会返回这些记录。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
