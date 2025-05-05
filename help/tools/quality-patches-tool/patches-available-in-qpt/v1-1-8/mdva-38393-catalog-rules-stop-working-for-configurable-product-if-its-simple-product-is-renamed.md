---
title: 'MDVA-38393：如果简单产品被重新命名，目录规则将停止为可配置产品工作'
description: MDVA-38393修补程序修复了当简单产品被重新命名时，目录规则停止为可配置产品工作的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8后，即可使用此修补程序。 修补程序ID为MDVA-38393。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: Catalog Management, Categories, Configuration, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-38393：如果对可配置产品的简单产品进行了重新命名，则目录规则将停止对其工作

MDVA-38393修补程序修复了当简单产品被重新命名时，目录规则停止为可配置产品工作的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8时，此修补程序可用。 修补程序ID为MDVA-38393。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.3.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果对可配置产品的简单产品进行了重新命名，则目录规则将停止使用该产品。

<u>重现步骤</u>：

1. 使用关联的简单产品创建可配置产品。
1. 创建类别。
1. 仅将可配置产品分配给新类别。
1. 创建新目录规则：
   * 条件=类别包含\&lt;新类别ID>
   * 操作= 50%折扣
   * 活动=是
1. 执行重新索引。
1. 检查前端的可配置产品（应应用折扣）。
1. 检查`catalogrule_product`表（简单产品应该有折扣）。
1. 转到管理员并更改简单产品的名称。 这将向`catalogrule_product_cl`表添加记录。
1. 执行cron或`bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`命令。
1. 检查`catalogrule_product`表。

<u>预期的结果</u>：

可配置产品具有折扣。

<u>实际结果</u>：

* `catalogrule_product`表中缺少为简单产品创建的折扣记录。
* 前端的可配置产品具有完整的原始价格。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
