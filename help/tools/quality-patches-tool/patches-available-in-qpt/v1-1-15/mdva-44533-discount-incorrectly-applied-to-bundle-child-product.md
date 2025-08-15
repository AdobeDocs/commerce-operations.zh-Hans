---
title: MDVA-44533：折扣错误地应用于捆绑的子产品
description: MDVA-44533修补程序修复了将折扣错误地应用于捆绑子产品的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15后，即可使用此修补程序。 修补程序ID为MDVA-44533。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Orders, Personalization, Products
role: Admin
exl-id: 150fe577-a61a-451e-838a-d60be7754bf4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-44533：折扣错误地应用于捆绑的子产品

MDVA-44533修补程序修复了将折扣错误地应用于捆绑子产品的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15后，即可使用此修补程序。 修补程序ID为MDVA-44533。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.1 - 2.4.3-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

折扣错误地应用于捆绑的子产品。

<u>重现步骤</u>：

1. 创建一个价格为50美元的简单产品。
1. 创建捆绑产品，并将简单产品指定为捆绑产品的唯一选项。
1. 使用以下方式创建购物车价格规则：

   * 条件：如果总金额大于130$
   * 操作：应用10$的固定金额折扣

1. 转到店面并将捆绑包产品添加到购物车，数量为1。
1. 转到购物车并检查捆绑产品的总成本是否为50$，并且折扣不适用。
1. 将数量更改为2并更新购物车。 捆绑产品的总成本现在应为100$。

<u>预期的结果</u>：

不应用折扣，因为小计为100\$，在规则条件中小于130\$。

<u>实际结果</u>：

将应用折扣。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的Quality Patches Tool[!DNL Quality Patches Tool]，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
