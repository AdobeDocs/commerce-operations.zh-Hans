---
title: MDVA-37364：日期类型的自定义客户属性破坏了网格UI
description: MDVA-37364修补程序解决了日期类型的自定义客户属性破坏客户网格UI的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-37364。 请注意，该问题计划在Adobe Commerce版本2.4.4中修复。
feature: Attributes, Cache
role: Developer
exl-id: 5bd64004-06c4-49fd-8e56-e2c44008ca82
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-37364：日期类型的自定义客户属性破坏了网格UI

MDVA-37364修补程序解决了日期类型的自定义客户属性破坏客户网格UI的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-37364。 请注意，该问题计划在Adobe Commerce版本2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0-2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

日期类型的自定义客户属性破坏了客户网格UI。

<u>重现步骤</u>：

1. 创建具有日期类型的自定义属性：
   * 转到&#x200B;**商店** > **属性** > **添加属性**。
   * 将“输入类型”设置为“日期”。
   * 将“添加至列选项”设置为“是”。
   * 保存属性。
1. 转到&#x200B;**管理员** > **客户** > **所有客户**。
   * 将新添加的自定义属性从列选项添加到网格。
1. 创建/编辑客户并设置已创建的自定义日期属性字段的值。
1. 保存、重新索引和清除缓存。
1. 转到&#x200B;**客户** > **所有客户**。
   * 检查客户网格。

<u>预期的结果</u>：

管理客户网格显示包括新日期自定义属性在内的所有数据，而不破坏客户网格UI。

<u>实际结果</u>：

管理客户网格UI已损坏。

## 应用修补程序

要应用单个修补程序，请根据您的部署类型使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布质量修补程序工具：用于自助提供质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查是否有可用于Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT[中可用的](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)修补程序部分。
