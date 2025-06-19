---
title: MDVA-38852：目录清单锁定了降低性能的表
description: MDVA-38852修补程序解决了目录清单为更新锁定表的问题，该问题会在发出多个并行订单时显着降低性能。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-38852。 请注意，Adobe Commerce 2.3.6中已修复此问题。
feature: Catalog Management, Inventory, Orders
role: Admin
exl-id: ce93130b-8d96-47b8-96c6-da5988b34ae0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-38852：目录清单锁定了降低性能的表

MDVA-38852修补程序解决了目录清单为更新锁定表的问题，该问题会在发出多个并行订单时显着降低性能。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-38852。 请注意，Adobe Commerce 2.3.6中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.3.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

目录库存会为更新锁定表，这会在同时下达多个订单时显着降低性能。

<u>重现步骤</u>：

1. 将产品添加到购物车。
1. 继续结帐并尝试下订单。

<u>预期的结果</u>：

* 没有死锁。
* 同时下多个订单时，性能不会降低。

<u>实际结果</u>：

* 当有多个并发用户时，下达订单的速度会非常慢。
* 出现死锁错误，如下所示：

```SQL
"SQLSTATE[40001]: Serialization failure: 1213 Deadlock found when trying to get lock; try restarting transaction, query was:
INSERT INTO `quote_payment` (`quote_id`, `method`, `additional_information`) VALUES (?, ?, ?)"
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
