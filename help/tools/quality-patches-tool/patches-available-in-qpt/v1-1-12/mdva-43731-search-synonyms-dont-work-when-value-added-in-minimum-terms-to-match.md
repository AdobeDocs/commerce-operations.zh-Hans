---
title: “MDVA-43731：在‘要匹配的最少搜索词’中添加值后，搜索同义词不起作用”
description: MDVA-43731修补程序修复了在“要匹配的最少搜索词”中添加值后搜索同义词停止工作的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-43731。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Cache, Marketing Tools, Search
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# MDVA-43731：在“要匹配的最少搜索词”中添加值时，搜索同义词不起作用

MDVA-43731修补程序修复了在“要匹配的最少搜索词”中添加值后搜索同义词停止工作的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12后，即可使用此修补程序。 修补程序ID为MDVA-43731。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在“要匹配的最少搜索词”中添加值后，搜索同义词将停止工作。

<u>重现步骤</u>：

1. 使用示例数据安装Adobe Commerce。
1. 将Elasticsearch7配置为搜索引擎。
1. 搜索“Jacket”一词。 将显示产品列表。
1. 在&#x200B;**配置** > **目录** > **目录搜索** > **要匹配的最少搜索词**&#x200B;中添加参数[4&lt;60%]。
1. 清除配置缓存并重新索引。
1. 再次搜索“Jacket”一词，会注意到已显示产品列表。
1. 转到&#x200B;**营销** > **SEO和搜索** > **搜索同义词**。
1. 通过添加以下同义词创建搜索同义词：jacket、bagtecs、express plus。
1. 重新索引。
1. 使用任何同义词进行产品搜索。 例如，夹克。

<u>预期的结果</u>：

您获得的产品列表与搜索结果中以前的产品列表相同。

<u>实际结果</u>：

搜索结果中未显示任何产品。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
