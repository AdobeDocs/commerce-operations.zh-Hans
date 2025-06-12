---
title: ACSD-51630：大量系统消息导致管理员页面下载缓慢
description: 应用ACSD-51630修补程序以修复大量系统消息导致下载管理页面变慢的Adobe Commerce性能问题。
feature: Admin Workspace, System
role: Admin
exl-id: 8f39afea-551a-4306-994a-cb8ce5bd5b4a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-51630：大量系统消息导致管理员页面下载缓慢

ACSD-51630修补程序修复了大量系统消息导致下载管理页面变慢的性能问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.34时，此修补程序可用。 修补程序ID为ACSD-51630。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 &lt; 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

大量系统消息导致管理员页面下载缓慢

<u>重现步骤</u>：

1. 向DELETE`/rest/async/v1/products/ {sku}`发出大量请求（约50k）。
1. 访问任何&#x200B;**管理页面**。

<u>预期的结果</u>：

页面会在适当的时间加载。 只应加载正在显示的消息。

<u>实际结果</u>：

页面加载时间过长。 所有现有消息都将从数据库加载。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
