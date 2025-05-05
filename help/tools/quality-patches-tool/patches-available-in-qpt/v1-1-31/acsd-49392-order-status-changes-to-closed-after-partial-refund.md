---
title: ACSD-49392：部分退款后订单状态更改为“已关闭”
description: 应用ACSD-49392修补程序以修复Adobe Commerce问题，该问题导致捆绑产品的部分退款后，订单状态更改为“已关闭”。
feature: Orders
role: Admin
exl-id: e12cbf2d-219e-4cb5-a226-6c7ae4929549
source-git-commit: 67e050b4ceccc3f30bf8cd49125525b2e8d8b0dd
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49392：部分退款后订单状态更改为“已关闭”

>[!NOTE]
>
>对于版本2.4.6-p7到2.4.6-p10，修补程序ACSD-49392被替换为修补程序[ACSD-57003](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-57003-order-status-changed-to-complete-instead-of-processing)。

ACSD-49392修补程序修复了在对捆绑产品进行部分退款后，订单状态更改为closed的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.31时，此修补程序可用。 修补程序ID为ACSD-49392。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.3.7-p4和2.4.1 - 2.4.6-p6

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对捆绑产品进行部分退款后，订单状态更改为closed。

<u>重现步骤</u>：

1. 登录到Adobe Commerce并创建任何捆绑产品，或使用现有的捆绑产品。
1. 订购数量大于1的捆绑产品。
1. 转到“管理员”，从&#x200B;**[!UICONTROL Sales]** > **[!UICONTROL Order]**&#x200B;中打开在步骤2中创建的订单并创建发票。 观察订单状态。 它将在处理中。
1. 创建部分贷项通知单（不要为捆绑包中的所有产品退款）。
1. 检查订单状态。

<u>预期的结果</u>

在为捆绑产品创建部分贷项通知单后，订单状态为正在处理。

<u>实际结果</u>

为捆绑产品创建部分贷项通知单后，订单状态为完成。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
