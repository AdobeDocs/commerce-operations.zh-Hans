---
title: MDVA-42046：为产品属性分配的值不正确
description: MDVA-42046修补程序修复了在更新具有日期输入字段的产品时，为产品属性分配的值不正确的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-42046。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Attributes, Products
role: Admin
exl-id: ff5903ff-70b3-4274-a8a1-450c2fde9750
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-42046：为产品属性分配的值不正确

MDVA-42046修补程序修复了在更新具有日期输入字段的产品时，为产品属性分配的值不正确的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13后，即可使用此修补程序。 修补程序ID为MDVA-42046。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.4 - 2.3.5-p2和2.4.0 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

保存具有`news_from_date`和/或`news_to_date`字段的产品后，这些字段中的值将重置为默认值。

<u>重现步骤</u>：

1. 创建一个简单的产品。
1. 导出在第一步中创建的产品。
1. 在导出的CSV文件中，在`news_from_date`和`news_to_date`字段中放置一些值。 例如，2021-05-15和2021-06-18。
1. 使用修改后的CSV文件导入产品。
1. 向产品网格中添加其他列“将产品设置为新的开始日期”和“将产品设置为新的结束日期”。
1. 打开产品的编辑页面，如果不进行任何更改，请单击&#x200B;**保存**。
1. 返回产品网格，然后检查产品的数据。

<u>预期的结果</u>：

“将产品设置为新的开始日期”和“将产品设置为新的结束日期”都与保存前相同。

<u>实际结果</u>：

* “将产品设置为新起始日期”和“将产品设置为新起始日期”列中的值已更改。

* “将产品设置为新起始日期”列显示当前日期，“将产品设置为新起始日期”列为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
