---
title: ACSD-48044：应用多张礼品卡可防止下订单
description: 应用ACSD-48044补丁以修复Adobe Commerce的问题，该问题导致在多次发运的情况下一次订购多张礼品卡会导致订单无法下达。
feature: Admin Workspace, Gift, Orders
role: Admin
exl-id: c7b72b1f-2f1b-4445-b842-5847d05d5ae9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-48044：应用多张礼品卡可防止下订单

ACSD-48044修补程序修复了以下问题：在包含多发服务的单张订单上应用多张礼品卡会阻止下单。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25时，此修补程序可用。 修补程序ID为ACSD-48044。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将多个礼品卡应用到包含多个发运的单个订单中，可防止下达订单。

<u>重现步骤</u>：

1. 安装Adobe Commerce的干净版本。
1. 创建一个价格为$100的简单产品和一个价格为$10的简单产品。
1. 登录到[!UICONTROL Admin panel]并创建两张礼品卡。

   * 02KB8M0H0GRD = $50
   * 00GXM6SUGBLW = 25美元

1. 创建具有两个地址的客户。
1. 将两个产品添加到购物车。

   * 首先添加$10的产品，然后添加$100的产品。 如果首先添加$100产品，则无法重现问题。

1. 转到购物车并添加您创建的两个礼品卡。
1. 在购物车页面上单击&#x200B;**[!UICONTROL Ship to Multiple Addresses]**。
1. 将每个产品分配给不同的地址。
1. 转到&#x200B;**[!UICONTROL Shipping information]**&#x200B;页面。
1. 转到&#x200B;**[!UICONTROL Billing information]**&#x200B;页面。
1. 转到&#x200B;**[!UICONTROL Review Your Order]**&#x200B;页面，您可以在其中看到问题。
1. 尝试下订单。

<u>预期的结果</u>：

* 礼品卡正确计入总金额。
* 下订单。

<u>实际结果</u>：

礼品卡金额混有错误&#x200B;*“请更正礼品卡代码。”下订单时*。

* 第一个产品：

   * 删除礼品卡(00GXM6SUGBLW) - 15.00美元
   * 删除礼品卡(02KB8M0H0GRD) - $0.00

* 第二个产品：

   * 删除礼品卡(00GXM6SUGBLW) - 25.00美元
   * 删除礼品卡(02KB8M0H0GRD) - $35.00

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
