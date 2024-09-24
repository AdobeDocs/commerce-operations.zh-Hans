---
title: 'MDVA-40488：带缺货子产品的可配置产品未显示在正确的价格范围内'
description: MDVA-40488修补程序解决了具有缺货子产品的可配置产品无法在其正确的价格范围内显示的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9后，即可使用此修补程序。 修补程序ID为MDVA-40488。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# MDVA-40488：带缺货子产品的可配置产品未显示在正确的价格范围内

MDVA-40488修补程序解决了具有缺货子产品的可配置产品无法在其正确的价格范围内显示的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9时，此修补程序可用。 修补程序ID为MDVA-40488。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

包含缺货子产品的可配置产品未显示在它们的正确价格范围内。

<u>先决条件</u>：

转到Commerce管理员> **商店** > **配置** > **目录** > **库存** > **库存选项**，并将&#x200B;**显示缺货产品**&#x200B;配置设置为&#x200B;*是*。

<u>重现步骤</u>：

1. 创建具有两个关联产品的可配置产品。 例如：简单产品Red和Brown。
1. 将简单产品的库存设置为“红色”，将“库存状态”设置为&#x200B;*库存中*，然后将“启用产品”状态设置为&#x200B;*否*。
1. 设置简单产品Brown的库存，然后将Enable Product状态设置为&#x200B;*是*。
1. 确保可配置产品的库存状态为&#x200B;*库存*。
1. 将简单产品Brown的库存更改为0，并将库存状态设置为&#x200B;*缺货*。
1. 此时，可配置的产品库存状态仍为&#x200B;*库存*。
1. 执行重新索引。
1. 检查`catalog_product_index_price`数据库表中可配置产品的`min_price`和`max_price` — 这两个值设置为0。
1. 但是，如果将可配置产品的库存状态设置为&#x200B;*缺货*&#x200B;并进行重新索引，则可以看到可配置产品的非零`min_price`和`max_price`值。

<u>预期的结果</u>：

如果所有子产品均为&#x200B;*缺货*，而可配置产品本身也为&#x200B;*缺货*，则使用所有子产品来计算价格。

<u>实际结果</u>：

当可配置库存状态为&#x200B;*库存*&#x200B;时，`catalog_product_index_price`数据库表中可配置产品的`min_price`和`max_price`值设置为0，但如果为&#x200B;*缺货*，则它们变为非零值。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
