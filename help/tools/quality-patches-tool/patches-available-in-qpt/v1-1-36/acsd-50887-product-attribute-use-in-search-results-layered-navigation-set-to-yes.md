---
title: 'ACSD-50887： *[!UICONTROL Use in Search Results Layered Navigation]*设置为“是”，不使用*[!UICONTROL Use in Search]*选项'
description: 应用ACSD-50887修补程序以修复Adobe Commerce问题，在该问题中，产品属性属性*[!UICONTROL Use in Search Results Layered Navigation]*可以设置为*是*，而选项*[!UICONTROL Use in Search]*也可以设置为*是*。
feature: Attributes, Products, Search, Storefront
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-50887： *[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;设置为&#x200B;*是*，不带&#x200B;*[!UICONTROL Use in Search]*&#x200B;选项

ACSD-50887修补程序修复了产品属性属性&#x200B;*[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;可以设置为&#x200B;*是*&#x200B;而同时不将&#x200B;*[!UICONTROL Use in Search]*&#x200B;选项设置为&#x200B;*是*&#x200B;的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.36时，此修补程序可用。 修补程序ID为ACSD-50887。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

产品属性属性&#x200B;*[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;可以设置为&#x200B;*是*，而同时不将&#x200B;*[!UICONTROL Use in Search]*&#x200B;选项设置为&#x200B;*是*。

这些设置旨在一起使用。 应用修补程序后，当&#x200B;*[!UICONTROL Use in Search]*&#x200B;选项设置为&#x200B;*No*&#x200B;时，*[!UICONTROL Use in Search Results Layered Navigation]*&#x200B;选项将隐藏，以像也设置为&#x200B;*No*&#x200B;一样工作。

<u>重现步骤</u>：

1. 在管理员中，导航到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Attribute]** > **[!UICONTROL Product]**&#x200B;并创建具有多选类型的属性，然后设置以下内容：

   * *[!UICONTROL Use in Search]=否*
   * *[!UICONTROL Use in Layered Navigation]= （任何选项）*
   * *[!UICONTROL Use in Search Results Layered Navigation]=是*
   * *名称= Test_attribute*
   * *选项*：
      * *贴纸*
      * *选取器*

1. 将新属性添加到默认属性集。
1. 创建两个产品：

   1. 第一个产品：
      * 名称=贴纸
      * 将价格、数量、重量设置为1
      * Test_attribute =选择选项&#x200B;*贴纸*

   1. 第二个产品：
      * 名称=选取器
      * 将价格、数量、重量设置为1
      * Test_attribute =同时选择两个选项

1. 运行`catalogsearch_fulltext`重新索引：

   `bin/magento indexer:reindex catalogsearch_fulltext`

1. 按店面上的单词&#x200B;*贴纸*&#x200B;搜索。

<u>预期的结果</u>：

只返回产品&#x200B;*贴纸*，因为&#x200B;*[!UICONTROL Use in Search]*&#x200B;设置为&#x200B;*No*&#x200B;时，[!DNL Elasticsearch]不会为Test_attribute编制索引。

<u>实际结果</u>：

这两种产品都会被退回。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
