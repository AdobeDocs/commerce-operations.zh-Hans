---
title: ACSD-56280：未完成礼品注册购买
description: 应用ACSD-56280补丁以修复未完成礼品注册购买的Adobe Commerce问题
feature: Checkout
role: Admin
exl-id: a79f789f-999f-4d11-b7ee-2c065b681efb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-56280：未完成礼品注册购买

>[!NOTE]
>
>此修补程序已被[ACSD-63283](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/acsd-63283-resolving-gift-registry-email-and-order-placement-issues-in-adobe-commerce.md)替换。

ACSD-56280修补程序修复了礼品注册购买未完成的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44时，此修补程序可用。 修补程序ID为ACSD-56280。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

未完成礼品注册购买。

<u>重现步骤</u>：

1. 以客户身份登录，并将&#x200B;**[!UICONTROL product]**&#x200B;添加到礼品注册表。
1. 共享礼品注册表链接。
1. 在另一个浏览器/无痕窗口中打开礼品注册链接。
1. 添加数量，然后将项目添加到购物车。
1. 转到&#x200B;**[!UICONTROL Checkout Page]**，选择&#x200B;**[!UICONTROL shipping method]**（因为已选择送货地址，由注册者提供）。
1. 选择付款方式。
1. 单击“下单”按钮。

<u>预期的结果</u>：

应该下订单。

<u>实际结果</u>：

未下订单，显示的错误为`Call to a member function getUpdatedQty() on null`。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
