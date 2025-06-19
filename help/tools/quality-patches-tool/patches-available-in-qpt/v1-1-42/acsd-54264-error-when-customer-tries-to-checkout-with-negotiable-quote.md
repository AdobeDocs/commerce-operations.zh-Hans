---
title: ACSD-54264：客户尝试使用可转让报价结帐时出错
description: 应用ACSD-54264修补程序以修复Adobe Commerce问题，该问题导致出现错误消息“您无法更新所请求的属性。 当客户尝试从其他商店视图中用可转让报价结帐时，将显示行ID：store_id。
feature: B2B, Checkout
role: Admin, Developer
exl-id: b1696228-b2ed-44eb-9e75-bf25ccf2f1cd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-54264：客户尝试使用可转让报价结帐时出现错误

ACSD-54264修补程序修复了错误消息&#x200B;*无法更新请求的属性的问题。 当客户尝试从其他商店视图中用可转让报价结帐时，将显示行ID：store_id*。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42时，此修补程序可用。 修补程序ID为ACSD-54264。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

错误消息&#x200B;*您无法更新请求的属性。 当客户尝试从其他商店视图中用可转让报价结帐时，将显示行ID：store_id*。

<u>先决条件</u>：

Adobe Commerce B2B模块已安装和启用。

<u>重现步骤</u>：

1. 为默认网站创建其他商店视图。
1. 在配置中启用&#x200B;*[!UICONTROL B2B Quote]*。
1. 以公司客户身份登录其中一个商店视图。
1. 将产品添加到&#x200B;*[!UICONTROL Shopping Cart]*。
1. 提交报价以供审查。
1. 作为管理员用户，转到&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Quotes]**&#x200B;并提交已批准的报价。
1. 作为公司客户，将商店视图更改为其他商店视图。
1. 试试看吧。

<u>预期的结果</u>：

客户使用此报价单下订单。

<u>实际结果</u>：

* 保存配送信息时出现错误：

  `You cannot update the request attribute. Row ID: store_id =#`

* 将记录以下错误：

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
