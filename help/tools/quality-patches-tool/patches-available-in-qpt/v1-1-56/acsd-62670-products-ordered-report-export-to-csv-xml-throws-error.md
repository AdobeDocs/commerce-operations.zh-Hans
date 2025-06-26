---
title: ACSD-62670： [!UICONTROL Ordered Products Report]导出到CSV，XML返回404错误
description: 应用ACSD-62670修补程序以修复将[!UICONTROL Ordered Products Report]导出为CSV和XML时引发错误的Adobe Commerce问题。
feature: Reporting, Admin Workspace, Data Import/Export
role: Admin, Developer
exl-id: 99d77ddd-4fb3-4eda-8771-62c0e25f49d1
type: Troubleshooting
source-git-commit: 3469da56c15499de4ceb5313c3cc2dfde0f0771c
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# ACSD-62670： *[!UICONTROL Ordered Products Report]*&#x200B;导出到CSV和XML时引发错误

ACSD-62670修补程序修复了将&#x200B;*[!UICONTROL Ordered Products Report]*&#x200B;导出为CSV和XML时会引发错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=zh-Hans) 1.1.56时，此修补程序可用。 修补程序ID为ACSD-62670。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4-p11、2.4.5-p10、2.4.6-p8、2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将&#x200B;*[!UICONTROL Ordered Products Report]*&#x200B;导出为CSV和XML会引发错误。

<u>重现步骤</u>：

1. 转到&#x200B;*管理员*&#x200B;面板，然后导航到&#x200B;**[!UICONTROL Reports]** > **[!UICONTROL Products]** > **[!UICONTROL Ordered]**。
1. 尝试导出CSV或Excel文件。

<u>预期的结果</u>：

导出报告时没有出现错误。

<u>实际结果</u>：

导出&#x200B;*[!UICONTROL Ordered Products Report]*&#x200B;导致错误404。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
