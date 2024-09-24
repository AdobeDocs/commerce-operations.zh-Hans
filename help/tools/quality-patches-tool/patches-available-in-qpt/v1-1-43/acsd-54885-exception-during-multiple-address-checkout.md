---
title: 'ACSD-54885：管理员以客户身份登录时，在多个地址签出期间出现异常'
description: 应用ACSD-54885修补程序以修复Adobe Commerce问题，该问题导致在管理员使用*[!UICONTROL Login as Customer]*功能执行多个地址签出期间发生错误。
feature: Checkout
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-54885：当管理员以客户身份登录时，在多个地址签出期间出现异常

ACSD-54885修补程序修复了以下问题：当管理员使用&#x200B;*[!UICONTROL Login as Customer]*&#x200B;功能时，在多个地址签出过程中发生错误。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43时，此修补程序可用。 修补程序ID为ACSD-54885。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当管理员使用&#x200B;*[!UICONTROL Login as Customer]*&#x200B;功能时，在多个地址签出过程中出错。

<u>重现步骤</u>：

1. 确保已启用&#x200B;*[!UICONTROL Login as Customer]*。 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]**。
1. 创建一个简单的产品。
1. 创建一个具有地址的新客户帐户。
1. 转到后端中的客户帐户：

   * 转到&#x200B;**[!UICONTROL Account Information]**&#x200B;选项卡，并将&#x200B;*[!UICONTROL Allow remote shopping assistance]* = *是*。
   * 单击&#x200B;**[!UICONTROL Login as Customer]**。

1. 将产品添加到购物车并转到&#x200B;*[!UICONTROL Checkout with multiple addresses]*。
1. 更新产品数量。
1. 尝试返回购物车。

<u>预期的结果</u>：

您可以更新购物车并使用多个地址结帐。

<u>实际结果</u>：

返回购物车时出现以下错误。

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
