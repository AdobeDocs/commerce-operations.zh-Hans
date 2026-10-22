---
title: 概述：[!DNL Quality Patches Tool] (QPT) v1.1.84
description: 此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.84中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
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
source-git-commit: bbbc64cec77399dcff1a28326227858e7bf1f3a4
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%
---
# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.84

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.84中提供的修补程序所修复的问题。

QPT v1.1.84包含以下修补程序：

1. **[ACP2E-4913](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-4913.md)**：修复了数据库死锁后REST API装运和发票创建永久失败的问题。
1. **ACP2E-5005**：修复了在管理员中重新配置捆绑产品并编辑数量时，可转让报价中的捆绑产品选项的数量恢复到其以前值的问题。
1. **ACP2E-5009**：修复了将数据从Magento Open Source迁移到Adobe Commerce时无法正确迁移类别计划设计更改和产品&#x200B;**[!UICONTROL Special Price]**&#x200B;计划更新，从而导致迁移期间缺少或跳过某些计划更新的问题，并提高了迁移性能。
1. **[ACP2E-5017](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5017.md)**：修复了在客户未分配给公司时通过GraphQL查询客户`role`返回&#x200B;*内部服务器错误*&#x200B;的问题。
1. **ACP2E-5027**：修复了在启用文件锁定时，索引器停滞在循环中并且重新索引未完成的问题。
1. **ACP2E-5029**：修复了在执行手动重新同步之前&#x200B;**[!DNL Live Search]**&#x200B;中未显示目录价格规则更改的问题。
1. **ACP2E-5041**：修复了在计划更新期间保存产品导致店面在更新结束后显示正常价格而不是&#x200B;**[!UICONTROL Special Price]**&#x200B;的问题。
1. **[ACP2E-5059](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5059.md)**：修复了客户收到同一订单的重复订单确认电子邮件的问题。
1. **[ACP2E-5122](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5122.md)**：修复了GraphQL购物车请求中处理的错误作为应用程序错误错误错误错误错误记录在异常日志中的问题。
1. **[ACP2E-5143](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5143.md)**：修复了在仅请求路由元数据时GraphQL `route`查询呈现完整的CMS页面内容的问题，从而增加包含页面生成器小组件的CMS页面的数据库查询次数。
1. **ACP2E-5183**：修复了在编译使用`@magento_import`指令的`LESS`文件时，静态内容部署在PHP 8.5上失败的问题。
1. **ACP2E-5242**：修复了在将项目添加到购物车时检查产品可用性显示错误（指示无法找到网站）的问题。
1. **ACP2E-5263**：修复了在包含所有产品之前可以停止将产品导出到CSV文件，从而导致文件不完整的问题。
1. **ACP2E-5034**：修复了在选择配送方式后重新计算报价时，可转让报价管理错误地将合计重置为&#x200B;*零*，丢弃通过Admin中的&#x200B;**[!UICONTROL Configure]**&#x200B;操作进行的捆绑产品选件数量的更新，并且未在报价小计中正确反映应用于动态捆绑价格产品的物料级折扣的问题。
1. **[ACP2E-4741](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-4741.md)**：修复了在使用非默认库存和来源时，保存作为[!UICONTROL Related Product]、[!UICONTROL Up-Sell]或[!UICONTROL Cross-Sell]链接的产品后，产品从店面消失的问题。
1. **[ACP2E-5079](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-84/acp2e-5079.md)**：修复了当客户帐户在全球共享时，分配给多个网站的客户区段仅返回第一个网站的匹配客户的问题。
1. **ACP2E-5127**：修复了在具有非默认区域设置的“管理员”面板中编辑公司帐户时，其&#x200B;**[!UICONTROL Credit Limit]**&#x200B;重置为&#x200B;*零*&#x200B;的问题。
1. **AC-15494**：修复了products查询返回带有HTML转义特殊字符而不是其原始字符的产品名称的问题。

使用左侧的菜单导航到特定的修补程序页面。
