---
title: ACSD-47704：捆绑产品仅显示库存产品的价格
description: 应用ACSD-47704补丁以修复Adobe Commerce问题，该问题导致捆绑产品仅显示库存产品的价格。
feature: Admin Workspace, Customer Service, Orders, Products
role: Admin
exl-id: 7f05ceed-869c-4d1a-91fd-0122dc98e65e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# ACSD-47704：捆绑产品仅显示库存产品的价格

ACSD-47704修补程序修复了在客户组之间错误地缓存客户区段价格的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28时，此修补程序可用。 修补程序ID为ACSD-47704。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.1-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

由于仅包含库存项目，因此启用了动态定价的捆绑产品的价格不正确。

<u>重现步骤</u>：

1. 转到Commerce管理面板。
1. 转到&#x200B;**[!UICONTROL CATALOG]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Bundle Product]**。
1. 将&#x200B;**[UICONROL动态价格]**&#x200B;设置为&#x200B;**[!UICONTROL Yes]**。
1. 捆绑包项目：
   * 将&#x200B;**[!UICONTROL Ship bundle items]**&#x200B;设置为&#x200B;**[!UICONTROL Together]**
   * 选择&#x200B;**[!UICONTROL Add Option]**
      * **[!UICONTROL Title]** = o1
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * 标记所需的复选框
      * 添加任何有现货的简单产品；例如，Joust Duffle Bag SKU 24-MB01。 在添加产品之前，请记下其价格 — 34美元
   * 默认数量：1
   * 选择&#x200B;**[!UICONTROL Add Option]**
      * **[!UICONTROL Option Title]** = o2
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * 标记所需的复选框
      * 添加任何有现货的简单产品（与之前步骤中添加的产品不同）；例如 — Workflow Shall Pack 24-MB04。 在添加产品之前，请记下其价格 — 32美元
      * 默认数量：1
1. 保存产品。
1. 转到店面，找到在之前步骤中创建的产品。 减记价格 — 66美元
(66 = 32 + 34)。
目前，捆绑产品的价格等于其期权价格的总和。
1. 转到Commerce管理面板。 转到&#x200B;**[!UICONTROL CATALOG]** > **[!UICONTROL Products]**。
1. 查找先前作为选项分配给捆绑产品的简单产品之一：
SKU 24-MB01，价格34美元。
1. 将其数量更改为0。
1. 保存产品。
1. 转到店面，找到在之前步骤中创建的捆绑包产品。 记下价格–32美元。 以前定价为66美元，即24-MB01的SKU为34美元，24-MB04的SKU为32美元。 现在24-MB01产品已无库存，捆绑价格为32美元。 它是其他产品的价格，这是一种有股票期权。

<u>预期的结果</u>：

无论期权有价还是无库存，已启用动态定价的捆绑产品的价格计算方式均保持一致。

<u>实际结果</u>：

启用了动态定价的捆绑产品的价格计算错误。 它仅考虑有库存的期权，这样当其中一个期权无库存时，显示的金额就会低于实际金额。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
