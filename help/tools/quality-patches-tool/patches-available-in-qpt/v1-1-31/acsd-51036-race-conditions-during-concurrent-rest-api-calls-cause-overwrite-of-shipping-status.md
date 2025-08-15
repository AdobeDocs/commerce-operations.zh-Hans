---
title: ACSD-51036：并发REST API调用期间的争用情况会导致发运状态被覆盖
description: 应用ACSD-51036修补程序以修复Adobe Commerce问题，该问题导致在并发REST API调用期间出现争用情况，进而覆盖订购项目表中的发运状态。
feature: REST, Orders, Shipping/Delivery
role: Admin
exl-id: 6150d072-05fe-4010-b31b-8ccde9cab656
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51036：并发REST API调用期间的争用情况会覆盖订购物料表中的发运状态

ACSD-51036修补程序修复了在并发REST API调用期间出现的争用情况导致覆盖订购项目表中的送货状态的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.31时，此修补程序可用。 修补程序ID为ACSD-51036。 请注意，Adobe Commerce 2.4.5中已修复该问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

并发REST API调用期间的争用情况会覆盖订购物料表中的发运状态。

<u>重现步骤</u>：

1. 创建包含两个项目的订单。
1. 发票项目A。
1. 在发送物料B的发运请求的同时，通过REST API同时发送物料A的退款请求。
1. 转到&#x200B;**[!UICONTROL Admin Panel]**&#x200B;中的订单。

<u>预期的结果</u>

在&#x200B;*[!UICONTROL Shipped 1]*&#x200B;排序表中，物料B的状态应为&#x200B;*[!UICONTROL Items]*。

<u>实际结果</u>

*[!UICONTROL Shipped 1]*&#x200B;排序表中项B的&#x200B;*[!UICONTROL Items]*&#x200B;状态不存在。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)：搜索修补程序[!DNL Quality Patches Tool]。
