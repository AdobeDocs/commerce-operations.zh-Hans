---
title: ACSD 49843：使用[!UICONTROL Payment Action]自动开票后产品下载链接不可用= [!UICONTROL Intent Sale]
description: 应用ACSD-49843修补程序以修复Adobe Commerce问题：当[!UICONTROL Payment Action]设置为[!UICONTROL Intent Sale]时，通过在线付款方式自动对订购项目开票后，产品下载链接不可用。
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: e990b550-fb32-48d2-9c39-2176d7ab34c9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-49843：使用[!UICONTROL Payment Action]自动开票后产品下载链接不可用= [!UICONTROL Intent Sale]

ACSD-49843修补程序修复了以下问题：当[!UICONTROL Payment Action]设置为[!UICONTROL Intent Sale]时，订购项目通过在线付款方式自动开票后，产品下载链接不可用。 安装[!DNL Quality Patches Tool (QPT)] 1.1.37时，此修补程序可用。 修补程序ID为ACSD-49843。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.3.7-p4、2.4.1 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当[!UICONTROL Payment Action]设置为[!UICONTROL Intent Sale]时，通过联机付款方法自动对订购项目开票后，产品下载链接不可用。

<u>重现步骤</u>：

1. 登录到Adobe Commerce管理员并导航到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**。

   * 在[!UICONTROL Payment Action]下拉列表中，选择&#x200B;**[!UICONTROL Intent Sale]**，并将&#x200B;*[!UICONTROL Enable Card Payments]*&#x200B;设置为&#x200B;*是*。

1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]**，并确保它设置为&#x200B;*“已开发票”*。
1. 在店面，以客户身份登录。

   * 将任何可下载的产品和简单产品添加到购物车。
   * 使用[!DNL Braintree Pay]可使用卡片选项下订单。

1. 转到&#x200B;**[!UICONTROL My Orders]**&#x200B;并查看是否已自动为订单创建发票，且两个项目状态为&#x200B;*“已开票”*。
1. 转到&#x200B;**[!UICONTROL My Downloadable Products]**&#x200B;并观察下载链接是否不可用。
1. 在“管理员”中，转至该订单并为其创建装运。
1. 在店面，转到&#x200B;**[!UICONTROL My Downloadable Products]**&#x200B;并观察下载链接现已可用。

<u>预期的结果</u>：

当可下载的产品状态为&#x200B;*“已开发票”*&#x200B;时，下载链接可用。

<u>实际结果</u>：

即使可下载的产品状态显示为&#x200B;*“已开发票”*，下载链接也不可用。 只有在为实物产品创建装运后，它才可用。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
