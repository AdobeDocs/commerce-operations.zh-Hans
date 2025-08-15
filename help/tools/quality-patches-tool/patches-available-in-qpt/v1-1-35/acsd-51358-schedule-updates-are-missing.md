---
title: ACSD-51358：缺少计划更新
description: 应用ACSD-51358修补程序以修复Adobe Commerce问题，该问题导致在没有结束日期的情况下对计划更新所做的更改删除同一实体上的其他计划更新。
feature: Staging
role: Admin, Developer
exl-id: 6e2e598b-72f1-4f00-a989-3f75bf65f8f0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51358：缺少计划更新

ACSD-51358修补程序修复了以下问题：在没有结束日期的计划更新中的更改导致删除同一实体上的其他计划更新。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35时，此修补程序可用。 修补程序ID为ACSD-51358。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果没有结束日期，则计划更新中的更改会导致删除同一实体上的其他计划更新。

<u>重现步骤</u>：

1. 创建不带结束日期的&#x200B;**[!UICONTROL scheduled update]** （*更新1*）。
1. 创建开始日期与首次更新相同的新&#x200B;**[!UICONTROL scheduled update]**，但添加第二天和结束日期（*更新2*）。
1. 编辑在第1步创建的&#x200B;**[!UICONTROL scheduled update]** （*更新1*）并保存更改。

<u>预期的结果</u>

编辑(*update 1*)时，(**[!UICONTROL schedule update]** update 2 *)应保留在*&#x200B;列表中。

<u>实际结果</u>

编辑(*update 1*)时，(**[!UICONTROL schedule update]** update 2 *)已从*&#x200B;列表中删除。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)：搜索修补程序[!DNL Quality Patches Tool]。
