---
title: ACSD-66441：分层导航在多存储设置中显示不正确的属性选项
description: 应用ACSD-66441修补程序以修复分层导航在多存储设置中错误地显示来自其他存储的属性的Adobe Commerce问题。
feature: Catalog Management, Search
role: Admin, Developer
type: Troubleshooting
exl-id: d61c6b9e-bbcf-4285-b97b-b1fee67048e5
source-git-commit: 515e6d1f00c910455a2ffddf70c4a450184e7e81
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-66441：分层导航在多存储设置中显示不正确的属性选项

ACSD-66441修补程序修复了在多存储设置中，分层导航错误地显示来自其他存储的属性的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67时，此修补程序可用。 修补程序ID为ACSD-66441。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

店面上的分层导航包含来自其他商店的属性值，即使这些产品在当前商店视图中不可用。

<u>重现步骤</u>：

1. 创建辅助网站、商店和商店视图。
1. 使用自定义属性（例如，大小）创建可配置产品。
1. 将可配置产品分配给主网站和类别。
1. 重新索引所有数据。
1. 导航到店面上的已分配类别。 所有大小选项在分层导航中均可正确显示。
1. 从主网站中取消分配两个简单产品，并将它们分配给辅助网站，或从主网站中删除它们。
1. 重新索引所有数据。
1. 重新访问店面类别页面并检查分层导航。

<u>预期的结果</u>：

分层导航仅显示分配给当前商店或网站的产品中的属性选项。

<u>实际结果</u>：

分层导航显示分配给其他商店或网站的产品的属性选项（大小）。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
