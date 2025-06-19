---
title: MDVA-39229：更新目录规则暂存更新开始时间时出错
description: MDVA-39229修补程序修复了用户在更新目录规则暂存更新的开始时间后收到错误的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5后，即可使用此修补程序。 修补程序ID为MDVA-39229。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: Catalog Management, Staging
role: Admin
exl-id: 633123bc-634c-4943-a2f1-9a48999774f4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-39229：更新目录规则暂存更新开始时间时出错

MDVA-39229修补程序修复了用户在更新目录规则暂存更新的开始时间后收到错误的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5时，此修补程序可用。 修补程序ID为MDVA-39229。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.3.4-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户更新目录规则暂存更新的开始时间后收到错误。

<u>重现步骤</u>：

1. 创建目录价格规则。
1. 创建并执行任何暂存更新。
1. 运行查询并验证是否已创建暂存标志。


   `select * from flag;`


1. 创建新的暂存更新，以在5分钟后开始。
1. 打开&#x200B;**内容** > **暂存** > **仪表板** > **新更新**，并将开始时间延迟一分钟。
1. 等六分钟。
1. 运行cron。

<u>预期的结果</u>：

更新开始时间已更改，并且应用了更新。 从`staging_update`表中删除旧更新。

<u>实际结果</u>：

用户收到以下错误：

*report.ERROR： Cron作业staging_synchronize_entities_period出错：无法删除活动更新。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅QPT[&#128279;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)中可用的修补程序部分。
