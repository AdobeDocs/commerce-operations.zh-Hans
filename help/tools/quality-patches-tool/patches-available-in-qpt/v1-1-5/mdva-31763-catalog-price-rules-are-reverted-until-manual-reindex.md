---
title: MDVA-31763：将还原目录价格规则，直到手动重新编入索引
description: MDVA-31763修补程序解决了在手动重新索引之前恢复目录价格规则的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5后，即可使用此修补程序。 修补程序ID为MDVA-31763。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: Catalog Management, Orders, Price Rules
role: Admin
exl-id: 1d144bfc-c26b-43d0-a80c-26a9c2d8ef32
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-31763：将还原目录价格规则，直到手动重新编入索引

MDVA-31763修补程序解决了在手动重新索引之前恢复目录价格规则的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5时，此修补程序可用。 修补程序ID为MDVA-31763。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.3.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对可配置产品执行`catalogrule_product`部分索引器时，目录规则消失。

<u>重现步骤</u>：

1. 登录到管理员后端。
1. 转到&#x200B;**商店** > **属性** > **产品**&#x200B;并搜索“制造商”属性。
   * 添加几个选项并将“用于促销规则条件”设置为&#x200B;*是*。
1. 转到&#x200B;**存储** > **属性** > **属性集**。
   * 选择默认属性集并添加“manufacturer”属性。
1. 创建具有几个变体的可配置产品。
1. 为之前创建的可配置产品设置“制造商”属性值。
1. 创建目录规则：
   * 活动=是
   * 网站=主网站
   * 客户组=未登录
   * 条件：制造商= \&lt;可配置产品的选定值>
   * 操作：任何折扣
1. 执行完整索引。
1. 检查PDP上的产品价格，并确保价格正确。
1. 更新已创建的可配置产品的“权重”属性。
1. 检查PDP上的产品价格。

<u>预期的结果</u>：

在部分重新索引期间，不会删除针对可配置产品设置的目录价格规则。

<u>实际结果</u>：

对可配置产品设置的目录价格规则在部分重新索引期间消失。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的修补程序部分。
