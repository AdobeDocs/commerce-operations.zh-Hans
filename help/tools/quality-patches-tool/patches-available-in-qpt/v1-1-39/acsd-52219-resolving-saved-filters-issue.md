---
title: ACSD-52219：解决书签视图切换中的管理网格过滤器问题
description: 应用ACSD-52219修补程序以修复在书签视图之间频繁切换时，管理员网格的已保存过滤器无法按预期工作的Adobe Commerce问题。
feature: Admin Workspace
role: Admin
exl-id: 3f1af6ba-88a0-480c-b16e-c00c655e346f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-52219：解决书签视图切换中的管理网格过滤器问题

ACSD-52219修补程序修复了在书签视图之间频繁切换时，管理员网格的已保存过滤器无法按预期工作的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39时，此修补程序可用。 修补程序ID为ACSD-52219。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当经常在书签视图之间切换时，管理网格中保存的筛选器无法按预期运行。

<u>重现步骤</u>：

1. 在“管理员”中访问[!DNL Sales Order]网格。
1. 创建两到三个过滤器。
1. 通过切换视图来验证筛选器设置，以确保准确保存它们。
1. 转到Filter1或Filter2。
1. 刷新页面以更新显示的数据。
1. 切换到其他视图，并注意筛选器保持不变。
1. 请注意，默认视图现在显示过滤的结果，即使没有为其设置特定过滤器也是如此。

<u>预期的结果</u>：

过滤器不会互换并保留其原始状态。

<u>实际结果</u>：

修改视图时，过滤器会混合在一起，并且不会保存正确的视图。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)：搜索修补程序[!DNL Quality Patches Tool]。
