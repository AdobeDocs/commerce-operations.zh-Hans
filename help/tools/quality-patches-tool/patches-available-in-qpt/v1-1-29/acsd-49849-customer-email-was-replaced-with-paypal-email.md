---
title: ACSD-49849：客户电子邮件已替换为PayPal电子邮件
description: 应用ACSD-49849修补程序以修复Adobe Commerce问题，该问题导致在通过GraphQL向PayPal Express下订单时，客户电子邮件被替换为PayPal电子邮件。
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 1d7a2bde-892a-4ded-a4b4-9450989c8aee
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-49849：客户电子邮件已替换为[!DNL PayPal]电子邮件

ACSD-49849修补程序修复了在通过GraphQL向[!DNL PayPal Express]下订单时，客户的电子邮件被替换为[!DNL PayPal's]电子邮件的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29时，此修补程序可用。 修补程序ID为ACSD-49849。 请注意，Adobe Commerce 2.4.6中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

通过GraphQL向[!DNL PayPal Express]下达订单时，客户的电子邮件将替换为[!DNL PayPal's]电子邮件。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**。
1. 启用并配置[!DNL PayPal Express]并将&#x200B;**[!UICONTROL Payment Action]**&#x200B;设置为&#x200B;**[!UICONTROL Sale]**。
1. 转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]**，然后创建一个简单的产品。
1. 使用GraphQL完成访客签出。 有关更多信息，请参阅Adobe Commerce开发人员文档中的[GraphQL签出教程](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/)。
1. 使用[!DNL PayPal Express]作为付款方式。
1. 请记下Adobe Commerce开发人员文档中您在[设置购物车](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/)的电子邮件步骤中使用的电子邮件。
1. 下订单后，转到Adobe Commerce管理员，然后查看已创建订单中的电子邮件。

<u>预期的结果</u>：

电子邮件与结账时设置的相同。

<u>实际结果</u>：

签出期间设置的电子邮件将被[!DNL PayPal]帐户中设置的电子邮件覆盖。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
