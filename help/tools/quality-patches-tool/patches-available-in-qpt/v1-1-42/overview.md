---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.42
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.42中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
exl-id: 40db5196-0ba3-49c4-97b7-32f146c67f95
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.42

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.42中提供的修补程序所修复的问题。

QPT v1.1.42包含以下修补程序：

1. **ACSD-53658**：修复了&#x200B;*[!UICONTROL Recently Viewed]*&#x200B;产品数据未在商店视图中正确更新的问题。
1. **ACSD-54626**：修复了无法通过GraphQL创建具有`createPurchaseOrderApprovalRule`属性的新采购订单规则(`NUMBER_OF_SKUS`)的问题。
1. **ACSD-53845**：修复了`consumer max_messages` = 0时的MySQL连接超时问题。
1. **ACSD-54890**：修复了`aggregate_sales_report_bestsellers_data`由于`/tmp`磁盘空间不足而导致MySQL错误的问题。
1. **ACSD-55112**：修复了在没有&#x200B;*[!UICONTROL Submit review]*&#x200B;验证的情况下多次单击[!DNL Google reCAPTCHA v3]按钮的问题。
1. **ACSD-54264**：修复了错误消息&#x200B;*无法更新请求的属性的问题。 当客户尝试从其他商店视图中用可转让报价结帐时，将显示行ID：store_id*。
1. **ACSD-54418**：修复了将固定折扣额错误地应用于动态定价捆绑包的每个子产品的问题。
1. **ACSD-55238**：修复了保存空的产品元描述时出现的问题。
1. **ACSD-54966**：修复了在上一个订单失败时，无法重用每个客户限量使用的优惠券代码的问题。
1. **ACSD-54060**：修复了受限制的管理员无法保存某个产品的问题，如果该产品是分配给其他范围的另一个产品的子产品。
1. **ACSD-48910**：修复了在为订单开票和发运订单后，分配给多个来源的捆绑产品缺货的问题，即使订单具有非零数量也是如此。
1. **ACSD-55381**：修复了通过GraphQL从B2B `configurable_product_option_uid`查询`configurable_product_option_value_uid`和&#x200B;*[!UICONTROL Requisition list]*&#x200B;字段时出现的内部服务器错误。
1. **ACSD-55628**：修复了在公司注册表中上传文件的问题，以及替换店面中客户属性的文件的问题。

使用左侧的菜单导航到特定的修补程序页面。
