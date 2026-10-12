---
title: 概述：[!DNL Quality Patches Tool] (QPT) v1.1.53
description: 此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.53中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e7c8d45-dc0c-4182-8cd0-727b28294d58
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%
---
# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.53

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.53中提供的修补程序所修复的问题。

QPT v1.1.53包含以下修补程序：

1. **ACSD-48318**：修复了不允许环境模拟嵌套的问题。 现在，模拟在`send()`调用期间启动，一旦模拟在`getInfoBlockHtml()`调用期间停止。
1. **ACSD-59930**：改进公司的&#x200B;*[!UICONTROL Create]*、*[!UICONTROL Save]*&#x200B;和&#x200B;*[!UICONTROL Delete]*&#x200B;流的性能。
1. **ACSD-60584**：修复了一个网站上为用户创建的访问令牌被允许访问或更改其他网站上的客户信息的问题。
1. **ACSD-60804**：修复了以下问题：编辑链接到已删除公司的客户会导致错误&#x200B;*在null*&#x200B;上调用成员函数`getSuperUserId()`。
1. **ACSD-61133**：修复了`sales_clean_quotes` cron从未批准的采购订单中删除报价的问题。
1. **ACSD-61528**：修复了使用GraphQL从[!UICONTROL Admin]检索角色时未返回任何结果的问题。
1. **ACSD-61553**：修复了在将具有不同优先级的多个折扣和&#x200B;*[!UICONTROL Maximum Qty Discount is Applied To]*&#x200B;应用于产品时，*[!UICONTROL Cart Price Rule]*&#x200B;折扣计算错误的问题。
1. **ACSD-61667**：改进库存性能，以便在使用&#x200B;*店内提货*&#x200B;的来源的情况下创建装运。
1. **ACSD-61969**：修复了要求用户键入与配置的优惠券代码完全匹配的区分大小写的优惠券代码的问题。

使用左侧的菜单导航到特定的修补程序页面。
