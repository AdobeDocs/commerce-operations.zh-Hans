---
title: MDVA-43983：设置为“单独不可见”的产品将显示在搜索结果中
description: MDVA-43983修补程序解决了设置为“不可见”的产品仍然显示在目录高级搜索结果中的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14后，即可使用此修补程序。 修补程序ID为MDVA-43983。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Catalog Management, Products, Search
role: Admin
exl-id: d494d263-016b-43fd-aa87-0d74eadc4a6a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-43983：设置为“单独不可见”的产品将显示在搜索结果中

MDVA-43983修补程序解决了设置为“不可见”的产品仍然显示在目录高级搜索结果中的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14时，此修补程序可用。 修补程序ID为MDVA-43983。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

设置为“单独不可见”的产品仍会显示在目录高级搜索结果中。

<u>重现步骤</u>：

1. 为存储区所有者&#x200B;**创建具有**&#x200B;目录输入类型的属性作为&#x200B;**下拉列表**&#x200B;或&#x200B;**可视化样本**（例如，颜色）。
1. 将&#x200B;**在搜索中使用**&#x200B;设置为&#x200B;**是**，将&#x200B;**在高级搜索中可见**&#x200B;设置为&#x200B;**是**。
1. 添加一些属性选项。
1. 创建具有&#x200B;**可见性**&#x200B;的产品，因为&#x200B;**不可单独显示**。
1. 指定颜色属性选项。
1. 转到店面上的&#x200B;**目录高级搜索**&#x200B;页面。
1. 从“颜色”属性字段中仅选择“颜色”属性选项，并将其余字段留空或保持原样。
1. 提交高级搜索表单。
1. 观察搜索结果。

<u>预期的结果</u>：

设置为“不可见”的产品不会出现在目录高级搜索结果中。

<u>实际结果</u>：

设置为“单独不可见”的产品将显示在目录高级搜索结果中。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
