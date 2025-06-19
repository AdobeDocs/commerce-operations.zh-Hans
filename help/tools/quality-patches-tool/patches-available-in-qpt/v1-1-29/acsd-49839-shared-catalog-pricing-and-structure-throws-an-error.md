---
title: ACSD-49839：共享目录定价和结构引发错误
description: 应用ACSD-49839修补程序以修复Adobe Commerce问题，该问题导致当产品在SKU中具有单引号或双引号时，共享目录定价和结构在管理员中引发错误。
feature: Admin Workspace, Catalog Management, Categories
role: Admin
exl-id: b74e3926-16c8-4222-b642-ed1b7095dea4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-49839：共享目录定价和结构引发错误

ACSD-49839修补程序修复了以下问题：当产品在SKU中具有单引号或双引号时，共享目录定价和结构会在管理员中引发错误。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29时，此修补程序可用。 修补程序ID为ACSD-49839。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当SKU中的产品具有单引号或双引号时，共享的目录定价和结构会在管理员中引发错误。

<u>重现步骤</u>：

1. 使用特殊字符（即双引号）设置某些产品SKU，例如：
   *[Product&quot;12， Product&quot;14， Product&quot;15]*。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Add Shared Catalog]**（例如，*[测试共享目录]*）。
1. 分配所有&#x200B;**[!UICONTROL Products and Categories]** > **[!UICONTROL Generate Catalog]** > **[!UICONTROL Save]**。
1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Test Shared Catalog]** > **[!UICONTROL Action]** > **[!UICONTROL Set Pricing and Structure]**。
1. 标记&#x200B;*[!UICONTROL Root Catalog]*&#x200B;以选择所有类别和产品。
1. 在网络面板中观察AJAX请求。

<u>预期的结果</u>：

当产品在SKU中具有单引号或双引号时，共享的目录定价和结构不会在管理员中引发错误。

<u>实际结果</u>：

当SKU中的产品具有单引号或双引号时，共享的目录定价和结构会在管理员中引发错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
