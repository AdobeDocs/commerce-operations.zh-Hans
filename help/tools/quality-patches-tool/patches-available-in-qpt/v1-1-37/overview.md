---
title: 概述：[!DNL Quality Patches Tool] (QPT) v1.1.37
description: 此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.37中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
exl-id: 92338019-d71c-4fe8-984f-879d551b418f
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
source-wordcount: '300'
ht-degree: 0%
---
# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.37

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.37中提供的修补程序所修复的问题。

QPT v1.1.37包含以下修补程序：

1. **ACSD-52613**：修复了即使rest API没有对`Inventory_source`个项目进行任何更新，缓存和索引也会刷新的问题。
1. **ACSD-51884**：修复了在运行resize命令后，产品图像缓存路径不正确的问题。
1. **ACSD-53628**：修复了CSV销售订单报表显示错误的特殊字符的问题。
1. **ACSD-49843**：修复了在启用&#x200B;*[!UICONTROL Payment Action]* = *[!UICONTROL Sale]*&#x200B;设置的情况下通过在线付款方法自动对订购项目开票后，产品下载链接不可用的问题。
1. **ACSD-53148**：修复了GraphQL中有关将同一可配置产品添加到购物车的两个并行请求在购物车上导致具有相同产品SKU的两个单独项目的问题。
1. **ACSD-47054**：修复了预览重新索引为所有存储区运行重新索引，从而导致速度缓慢的问题。
1. **ACSD-52606**：修复了以下问题：用户单击&#x200B;**[!UICONTROL Notify Order is Ready for Pickup]**&#x200B;时，显示错误消息&#x200B;*您的订单未做好取货准备*。
1. **ACSD-51574**：修复了将图像替换为具有相同名称的其他图像后，未在前端更新图像的问题。
1. **ACSD-53728**：修复了产品EAV索引器完成时间较长的问题。
1. **ACSD-53979**：修复了在欢迎消息包含单引号时主页出现的JS问题。
1. **ACSD-52143**：修复了在产品导入后删除自定义选项的问题。
1. **ACSD-53750**：修复了在多线程`catalog_product_price`重新索引期间出现&#x200B;*管道断开或连接关闭*&#x200B;错误的问题。

使用左侧的菜单导航到特定的修补程序页面。
