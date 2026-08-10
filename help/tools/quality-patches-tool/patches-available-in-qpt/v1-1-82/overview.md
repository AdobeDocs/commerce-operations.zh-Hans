---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.82
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.82中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-07-24T20:44:59.025Z'
TQID: 'https://experienceleague.adobe.com/Qoz-3w1ddXeHyDsyfsM0gD1kwi-Z6dc-C6P9Q-nYrUo'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: bd989d82-1e15-4534-88db-f1f51dd77ffaid: c1256247-af4b-46d8-9dca-0c654ecfa157id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: b5b0f88fa2b7c168ab51f457994e4ed0578794a2
workflow-type: tm+mt
source-wordcount: 488
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.82

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.82中提供的修补程序所修复的问题。

QPT v1.1.82包含以下修补程序：

1. **ACP2E-4815**：修复了导致日志中出现PHP异常的多个GraphQL问题，修复了通过GraphQL在订单后创建的订单与客户帐户之间的正确关联，以及通过HTTP规范将响应与GraphQL保持一致。
1. **ACP2E-4194**：修复了GraphQL响应针对无效、未授权或格式错误的请求返回错误的HTTP状态代码的问题。
1. **[ACP2E-4682](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4682.md)**：修复了在每次加载页面时，访问检查报价为isActive状态的店面页面会创建空报价记录的问题。
1. **[ACP2E-4547](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4547.md)**：修复了以下问题：管理员用户无法在管理员中使用&#x200B;**[!UICONTROL Add Products By SKU]**&#x200B;将默认目录中的产品添加到分配给未链接到共享目录的客户组的公司的订单中。
1. **[ACP2E-4593](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4593.md)**：修复了在多网站部署中，为网站限制显示的CMS页面可能在辅助网站上不正确的问题。
1. **ACP2E-4695**：修复了目录规则索引器占用过多内存且无法完成而导致不稳定和内存不足错误的问题。
1. **ACP2E-4698**：修复了在页面生成器文本内容中再次编辑图像时，会保存绝对媒体URL而不是保留可移植媒体指令的问题。
1. **[ACP2E-4797](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4797.md)**：修复了以下问题：即使将数据库配置为支持utf8mb4，在WYSIWYG编辑器或管理员中的页面生成器内容中输入4字节Unicode字符也会被错误阻止。
1. **[ACP2E-4748](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4748.md)**：修复了在具有大量奖励积分历史记录的商店中奖励积分过期时间较慢而导致奖励积分过期时间延迟的问题。
1. **[ACP2E-4799](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4799.md)**：修复了`requisition_lists GraphQL`查询返回的`total_count`值的问题，该值仅反映当前页面上的项目数，而不反映符合查询条件的申请列表的总数。
1. **[ACP2E-4805](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4805.md)**：修复了当第一个可销售子产品出现在列表中的较晚时，带许多子产品的可配置产品的签出API请求明显变慢的问题。
1. **ACP2E-4840**：修复了`products` GraphQL查询中请求的数量值返回&#x200B;*null*&#x200B;的问题。
1. **[ACP2E-4870](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4870.md)**：修复了产品警报电子邮件通知忽略商店查看电子邮件设置的问题。
1. **[ACP2E-4875](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4875.md)**：修复了在管理员中查看带有大型通讯簿的客户帐户时意外注销管理员用户的问题。
1. **ACP2E-4894**：修复了在大容量存储上启用&#x200B;**[!UICONTROL Asynchronous Indexing]**&#x200B;时，管理订单管理网格中新订单出现延迟的问题。
1. **ACP2E-4981**：修复了以下问题：页面生成器产品轮播显示产品的顺序不反映管理员中设置的位置，并且当匹配的子产品单独可见时包含可配置产品。

使用左侧的菜单导航到特定的修补程序页面。
