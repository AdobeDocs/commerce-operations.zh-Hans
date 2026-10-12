---
title: ACSD-60632：每次尝试订购时保存的地址
description: 应用ACSD-60632修补程序以修复Adobe Commerce问题，该问题导致在每次尝试下订单时都保存了新地址，无论是否成功创建了订单。
feature: Orders, Products
role: Admin, Developer
exl-id: 9b623a1c-594f-47ed-82b4-d11ba20f3a58
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%
---
# ACSD-60632：每次尝试订购时保存的地址

ACSD-60632修补程序修复了在每次尝试下订单时都会保存新地址的问题，无论是否成功创建了订单。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.51时，此修补程序可用。 修补程序ID为ACSD-60632。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5-p8 - 2.4.7-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

每次尝试下订单时，无论是否成功创建了订单，都会在系统中保存新的地址条目。

<u>重现步骤</u>：

1. 启用&#x200B;**[!DNL PayPal Payflow Link]**&#x200B;付款方式：
   * 在本地计算机上，如果没有真正的IP，系统无法接收来自[!DNL PayPal Payflow Link]的API调用。
1. 创建一个简单的产品。
1. 创建没有地址的注册客户。
1. 将产品添加到购物车。
1. 继续操作直到进入结账流程。
1. 填写地址。 请确保在此步骤中创建了第一个地址。
1. 在&#x200B;*[!UICONTROL Review and Payments]*&#x200B;页面上，选择&#x200B;**[!UICONTROL Credit Card (Payflow Link)]**&#x200B;单选按钮。
1. 单击&#x200B;**[!UICONTROL Continue]**：
   * 签出页面返回到&#x200B;*[!UICONTROL Review and Payments]*&#x200B;步骤，其中预填充了地址和预期的错误消息。
1. 再次选择&#x200B;*[!UICONTROL Credit Card (Payflow Link)]*&#x200B;单选按钮。
1. 单击&#x200B;**[!UICONTROL Continue]**。

<u>预期的结果</u>：

在第二次尝试下单时，不会创建新地址。

<u>实际结果</u>：

每次尝试下订单后都会创建一个新地址。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
