---
title: 概述：[!DNL Quality Patches Tool] (QPT) v1.1.85
description: 此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.85中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 59431a80af552bd266da55fb49e489453cc64e71
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
