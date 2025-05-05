---
title: ACSD-60673：在结账时修复了多个付款方法的[!UICONTROL Cart Price Rule]问题
description: 应用ACSD-60673修补程序以修复Adobe Commerce问题，该问题导致总计中并非总是列出使用付款方法条件的[!UICONTROL Cart Price Rule]的折扣。
feature: Price Rules
role: Admin, Developer
exl-id: 2fe27959-5e5f-4d25-9f56-b0f8319fd562
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-60673：在结账时修复了多个付款方法的[!UICONTROL Cart Price Rule]问题

ACSD-60673修补程序修复了使用付款方法条件的[!UICONTROL Cart Price Rule]的折扣并不总是列在合计中的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52时，此修补程序可用。 修补程序ID为ACSD-60673。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

结账时多个付款方式的[!UICONTROL Cart Price Rule]无法正确应用于特定付款方式。

<u>先决条件</u>

确保在&#x200B;**[!UICONTROL Multiple Payment Methods]** > **[!UICONTROL Money Order]**&#x200B;和&#x200B;**[!UICONTROL Bank Transfer]**&#x200B;中已启用。

<u>重现步骤</u>：

1. 启用&#x200B;**[!UICONTROL Multiple Payment Methods]**。
1. 创建一个&#x200B;*[!UICONTROL Cart Price Rule]*。
   * 设置&#x200B;**[!UICONTROL Conditions]**：付款方式为&#x200B;**[!UICONTROL Money Order]**（或银行转帐）
   * 在所有产品上选择&#x200B;**[!UICONTROL Actions]** = *25%*&#x200B;折扣
1. 创建虚拟产品。
1. 要复制新的报价和来宾客户&#x200B;*[!UICONTROL Status]*，请转到店面并清除Cookie。
1. 将虚拟产品添加到购物车。
1. 继续执行&#x200B;*签出*。
1. 单击&#x200B;*[!UICONTROL Cart Price Rule]*&#x200B;中定义的付款方式。
1. 更新您的&#x200B;*[!UICONTROL Billing Address]*。
1. 确保在总金额中显示折扣。
1. 单击此复选框可更改付款方式。
1. 验证折扣是否可见。

<u>预期的结果</u>：

单击此复选框以切换到适用的付款方式后，折扣将显示在&#x200B;*总计*&#x200B;中。

<u>实际结果</u>：

折扣未显示在&#x200B;*总计*&#x200B;中。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
