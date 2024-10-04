---
title: 'MDVA-42855：签出期间未将新客户地址保存到通讯簿'
description: MDVA-42855修补程序修复了在签出期间新客户地址未保存到通讯簿中的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-42855。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-42855：在签出期间新客户地址未保存到通讯簿

MDVA-42855修补程序修复了在签出期间新客户地址未保存到通讯簿中的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-42855。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在结帐时，新客户地址不会保存到通讯簿中。

<u>重现步骤</u>：

1. 创建客户帐户并更新默认的送货地址和帐单地址。
1. 将产品添加到购物车并导航到结帐页面。
1. 在送货时，单击&#x200B;**+新地址**。
1. 输入新地址，并选中&#x200B;**保存在通讯簿**&#x200B;复选框。
1. 在付款时，勾选&#x200B;**我的帐单和送货地址相同**&#x200B;复选框。
1. 下订单。
1. 检查通讯簿。

<u>预期的结果</u>：

新的送货地址保存在通讯簿中。

<u>实际结果</u>：

新的送货地址未保存在通讯簿中。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。