---
title: 概述：[!DNL Quality Patches Tool] (QPT) v1.1.85
description: 此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.85中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
TQID: 'https://experienceleague.adobe.com/OmF7Ctss9khE5ONHNnfea0dTaN-1-wGTH-EN-gx5jvo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a094ba2e1af14f7139524bf5fa3ee55b169770d2
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%
---
# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.85

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.85中提供的修补程序所修复的问题。

QPT v1.1.85包含以下修补程序：

1. **ACP2E-4929**：修复了&#x200B;**[!UICONTROL Compare Products]**&#x200B;页面上的属性标签显示来自其他商店视图（而非当前商店视图）的翻译的问题。
1. **ACP2E-5075**：修复了类别条件为的固定金额购物车价格规则在规则仅与捆绑包父产品匹配时将折扣错误地应用于动态价格捆绑包产品的所有子项的问题。
1. **ACP2E-5077**：修复了并发的`customerCart`个GraphQL查询或`POST /V1/carts/mine`个REST请求为尚未拥有有效购物车的客户创建重复的活动购物车的问题。
1. **ACP2E-5088**：修复了会话过期时客户永久购物车被清除的问题。
1. **ACP2E-3991**：修复了未正确确定客户端IP地址的问题。
1. **ACP2E-5092**：修复了以下问题：**[!UICONTROL Company Profile]**&#x200B;页面和“管理员客户编辑”页面在保存的公司地址之后没有区域时显示错误时，将区域添加到其国家/地区。
1. **ACP2E-5124**：修复了当&#x200B;**[!UICONTROL Validation Strategy]**&#x200B;设置为&#x200B;**[!UICONTROL Stop on Error]**&#x200B;时，验证失败后，**[!UICONTROL Import]**&#x200B;按钮在验证结果中保持可用的问题。
1. **AC-17456**：修复了在管理面板的&#x200B;**[!UICONTROL Design Configuration]**&#x200B;页面上编辑&#x200B;**[!UICONTROL Global]**&#x200B;作用域时，在PHP 8.4和8.5上返回&#x200B;*HTTP 500*&#x200B;错误的问题。
1. **ACP2E-5212**：修复了&#x200B;**[!UICONTROL Quick Order]**&#x200B;接受使用`.csv`扩展名重命名的非CSV文件的问题。
1. **ACP2E-5300**：修复了在管理面板&#x200B;**[!UICONTROL Orders]**&#x200B;网格中搜索多个以空格分隔或逗号分隔的订单号时，关键字未返回匹配订单的问题。
1. **ACP2E-5354**：修复了通过REST API更新客户导致与公司帐户关联的客户在管理员&#x200B;**[!UICONTROL Customers]**&#x200B;网格中出现多次的问题。
1. **ACP2E-5208**：修复了在每个Storefront页面导航中重新加载&#x200B;**[!UICONTROL Requisition List]**&#x200B;部分的问题，即使未进行任何更改也是如此。

使用左侧的菜单导航到特定的修补程序页面。
