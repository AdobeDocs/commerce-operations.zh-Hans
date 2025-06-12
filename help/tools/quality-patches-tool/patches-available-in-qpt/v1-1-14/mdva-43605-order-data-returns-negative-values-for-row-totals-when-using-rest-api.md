---
title: MDVA-43605：使用Rest API时，订单数据返回行总计的负值
description: MDVA-43605修补程序修复了在使用Rest API时，订单数据返回行总计的负值的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14后，即可使用此修补程序。 修补程序ID为MDVA-43605。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: REST, Orders
role: Admin
exl-id: f27439a6-eeee-4176-9ac9-98220752db3f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-43605：使用Rest API时，订单数据返回行总计的负值

MDVA-43605修补程序修复了在使用Rest API时，订单数据返回行总计的负值的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14时，此修补程序可用。 修补程序ID为MDVA-43605。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.1 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用Rest API时，订单数据会返回行总计的负值。

<u>重现步骤</u>：

1. 启用免费送货。
1. 导航到&#x200B;**配置** > **目录** > **价格** >并设置目录价格范围=网站。
1. 导航到&#x200B;**配置** > **销售** > **税**&#x200B;并更新：
   * 发运的税类=应纳税货物
   * 计算设置：
      * 目录价格=含税
      * 运费=包括价格
      * 应用价格折扣=含税
   * 价格显示设置：含税（所有字段）
   * 购物车显示设置：含税（所有字段）
   * 订单、发票、贷项通知单：
      * 显示发运额=含税
1. 为美国创建税率（州=“*”），税率百分比= 24.00
1. 创建具有上述税率的税则。
1. 创建具有特定优惠券的购物车价格规则，并且折扣=整个购物车的固定金额的$50。
1. 创建四个产品，价格如下：8.90美元、5.90美元、6.90美元和5.95美元。
1. 使用上一步创建的优惠券代码创建一个管理订单，包括其中四个产品。 使用免运费。
1. 由于优惠券代码涵盖购物车总计，因此无需付款。
1. 检索刚刚通过Rest API端点创建的订单：

   ```json
   GET rest/V1/orders/1
   ```

<u>预期的结果</u>：

响应中的`base_row_total`和`base_row_total_incl_tax`的值为零。

<u>实际结果</u>：

响应中的`base_row_total`和`base_row_total_incl_tax`字段具有负值。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
