---
title: MDVA-37897：从“最近查看的项目”添加产品时重定向不正确
description: MDVA-37897修补程序解决了当用户尝试使用最近查看的构件中的选项添加产品时，重定向不正确的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1后，即可使用此修补程序。 修补程序ID为MDVA-37897。 请注意，该问题计划在Adobe Commerce版本2.4.4中修复。
feature: Products
role: Admin
exl-id: d4d1d735-38e4-455e-9045-a2443ce33851
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37897：从“最近查看的项目”添加产品时重定向不正确

MDVA-37897修补程序解决了当用户尝试使用最近查看的构件中的选项添加产品时，重定向不正确的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1时，此修补程序可用。 修补程序ID为MDVA-37897。 请注意，该问题计划在Adobe Commerce版本2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* 云基础架构上的Adobe Commerce 2.4.1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当用户尝试从“最近查看”部分添加具有所需选项的产品时，用户被重定向到产品列表页面而不是产品详细信息页面。

<u>重现步骤</u>：

1. 使用可自定义的选项（类型：单选按钮）创建简单产品。
1. 配置“最近查看的项目”小组件以显示产品。
1. 访问具有可自定义选项的产品，以便这些产品显示在“最近查看的项目”小组件中。
1. 在“最近查看的项目”小组件中，单击某个产品上的&#x200B;**添加到购物车**。

<u>预期的结果</u>：

您将被重定向到产品详细信息页面以选择相关选项。

<u>实际结果</u>：

您将被重定向到产品列表页面。

## 应用修补程序

要应用单个修补程序，请根据您的部署类型使用以下链接：

* 在我们的开发人员文档中，将Adobe Commerce内部部署：[软件更新指南>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。
* 我们的云基础架构上的Adobe Commerce：开发人员文档中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)。

## 相关阅读

要了解有关Adobe Commerce质量修补程序的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)中可用的[修补程序部分。
