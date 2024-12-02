---
title: ACSD-51645：在禁用Magento_OfflineShipping扩展的情况下保存新的购物车价格规则
description: 应用ACSD-51645修补程序以修复在禁用扩展Magento_OfflineShipping的情况下保存新的购物车价格规则时出现错误的Adobe Commerce问题。
exl-id: ce747ae4-6d2f-41c0-ba75-7da72be359c7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-51645：在禁用Magento_OfflineShipping扩展的情况下保存新的购物车价格规则

ACSD-51645修补程序修复了在禁用Magento_OfflineShipping扩展的情况下，保存新的购物车价格规则时出现错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33时，此修补程序可用。 修补程序ID为ACSD-51645。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果扩展`Magento_OfflineShipping`被禁用，则在保存新的购物车价格规则时出错。

<u>重现步骤</u>：

1. 禁用`Magento_OfflineShipping`模块。
1. 登录到&#x200B;**管理员**。
1. 转到&#x200B;**[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**。
1. 创建新&#x200B;**[!UICONTROL Cart Price Rule]**。
1. 填写必填字段。
1. 保存&#x200B;**[!UICONTROL Cart Price Rule]**。

<u>预期的结果</u>：

已成功保存购物车价格规则。

<u>实际结果</u>：

出现以下错误：
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](</help/tools/quality-patches-tool/usage.md>)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)。
