---
title: MDVA-41236：无法为产品创建新的或编辑现有的计划更新
description: MDVA-41236修补程序修复了以下问题：如果之前删除了“结束日期”，则用户无法为产品创建新的计划更新或编辑现有的计划更新。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5后，即可使用此修补程序。 修补程序ID为MDVA-41236。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Products, Staging
role: Admin
exl-id: 82192778-4f25-40a0-882e-d52d32c433c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-41236：无法为产品创建新的或编辑现有的计划更新

MDVA-41236修补程序修复了以下问题：如果之前删除了“结束日期”，则用户无法为产品创建新的计划更新或编辑现有的计划更新。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5时，此修补程序可用。 修补程序ID为MDVA-41236。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果用户之前删除了“结束日期”，则无法创建新计划或编辑产品的现有计划。

<u>重现步骤</u>：

1. 创建状态设置为&#x200B;*disable*&#x200B;的产品。
1. 添加计划更新以启用此产品。
   * 添加未来的开始和结束日期。
1. 通过删除&#x200B;**结束日期**&#x200B;来编辑计划更新。
1. 再次编辑计划并尝试添加&#x200B;**结束日期**。 将发生错误。
1. 刷新页面，然后再次转到&#x200B;**编辑计划更新**。
1. 单击&#x200B;**从更新中删除** > **删除更新**。
1. 现在，您不应在产品编辑页面顶部看到计划更新。
1. 尝试创建与上一个持续时间重叠的新计划更新。

<u>预期的结果</u>：

* 步骤4中没有错误。 由于计划尚未激活，管理员能够更新计划更新而不会出现任何错误。
* 管理员用户能够删除以前的更新并创建新更新。

<u>实际结果</u>：

用户将收到以下错误消息：

*错误：此时间范围内已存在将来更新。 请设置其他范围，然后重试。*


## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的Quality Patches Tool[!DNL Quality Patches Tool]，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅QPT[中可用的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)修补程序部分。
