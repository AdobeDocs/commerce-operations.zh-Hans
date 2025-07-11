---
title: MDVA-43091：无法从管理员处订购捆绑产品
description: MDVA-43091修补程序解决了用户无法从Commerce管理员订购捆绑产品的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10后，即可使用此修补程序。 修补程序ID为MDVA-43091。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: d2812f97-107c-4db9-93cc-7004344fcc95
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-43091：无法从管理员处订购捆绑产品

MDVA-43091修补程序解决了用户无法从Commerce管理员订购捆绑产品的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10时，此修补程序可用。 修补程序ID为MDVA-43091。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

尝试从管理员处订购捆绑产品时，会引发以下错误： *不能对此产品使用小数数量。*

<u>重现步骤</u>：

1. 安装干净的Adobe Commerce。
1. 创建两个简单的产品。
1. 创建具有两个选项的捆绑产品。
1. 在前端创建客户帐户。
1. 转到&#x200B;**管理员** > **销售** > **订单** > **创建新订单**。
   * 选择刚刚创建的客户帐户。
   * 尝试将捆绑的产品添加到购物车。

<u>预期的结果</u>：

管理员用户能够将具有一个数量的产品添加到购物车。

<u>实际结果</u>：

管理员用户收到以下错误： *不能对此产品使用小数数量。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
