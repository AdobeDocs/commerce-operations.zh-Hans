---
title: ACSD-47910：各个实体网格中缺少的订单、发票、发运和贷项通知单
description: 应用ACSD-47910补丁程序，以修复相应实体网格中缺少订单、发票、装运和贷项通知单的Adobe Commerce问题。
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 09115cf3-62c3-425e-bc99-e8971398dd20
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47910：各个实体网格中缺少订单、发票、装运和贷项通知单

ACSD-47910修补程序修复了各实体网格中缺少订单、发票、装运和贷项通知单的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25时，此修补程序可用。 修补程序ID为ACSD-47910。 将修复此问题的版本尚不可用。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
* Adobe Commerce（所有部署方法） 2.4.4-p1

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在各自的实体网格中缺少订单、发票、装运和贷项通知单。

<u>重现步骤</u>：

1. 在&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]**&#x200B;处启用&#x200B;**[!UICONTROL Asynchronous indexing]**。
1. 下两份订单。
1. 运行cron将这些订单同步到网格。
1. 打开其中一个订单，使其准备开票。 不要提交发票。
1. 做好新订单的准备工作，准备在前端投放。 不要单击“下单”按钮。
1. 在`foreach`的`NotSyncedDataProvider::L43`处添加`sleep(30)`。
1. 运行`bin/magento cron:run`。
1. 现在下新订单。
1. 为上一订单开票。
1. 再次运行cron，期待同步新订单。
1. 转到管理员中的订单网格。

<u>预期的结果</u>：

新订单应显示在订单网格上。

<u>实际结果</u>：

上一个订单更新已同步到网格(**[!UICONTROL status: Processing]**)。 新订单永远不会出现在网格上。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
