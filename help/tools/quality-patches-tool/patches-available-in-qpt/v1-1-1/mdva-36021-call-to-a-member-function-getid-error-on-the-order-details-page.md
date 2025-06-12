---
title: MDVA-36021：用户在打开订单详细信息时收到错误消息
description: MDVA-36021修补程序解决了用户在尝试打开订单详细信息时收到*成员函数getId()*调用错误消息的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1后，即可使用此修补程序。 修补程序ID为MDVA-36021。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: Orders
role: Admin
exl-id: 737479fe-f363-4974-9c58-7ed9cd113fdb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MDVA-36021：用户在打开订单详细信息时收到错误消息

MDVA-36021修补程序解决了用户在尝试打开订单详细信息时，收到&#x200B;*对成员函数getId()*&#x200B;的调用错误消息的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1时，此修补程序可用。 修补程序ID为MDVA-36021。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云基础架构上的Adobe Commerce 2.4.1、2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当用户尝试打开订单详细信息时，以下错误消息显示在管理员的订单详细信息页面中： *report.CRITICAL： Error：调用/magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml：62*&#x200B;中数组上的成员函数getId()。

<u>先决条件</u>：

系统应具有税设置和具有特定税率的订单。

<u>重现步骤</u>：

1. 登录到Commerce管理员。
1. 转到&#x200B;**Sales** > **Orders** > **Open Order**。

<u>预期的结果</u>：

订单打开时没有出现错误。

<u>实际结果</u>：

您收到类似于以下内容的错误消息： *report.CRITICAL：错误：在/magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml：62*&#x200B;中的数组中调用成员函数getId()。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
