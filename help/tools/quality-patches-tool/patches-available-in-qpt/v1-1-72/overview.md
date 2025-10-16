---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.72
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.72中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 89b78f72fce3f65b8f282038cc4e2ef0f190bda3
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.72

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.72中提供的修补程序所修复的问题。

QPT v1.1.72包含以下修补程序：
1. **ACSD-68040**：前端搜索页面在包含许多历史搜索请求的[!DNL MariaDB] 10.6和11.4上性能下降。
1. **ACSD-67941**：具有未知筛选器名称的GraphQL请求会导致PHP异常日志。
1. **ACSD-68064**：创建计划更新会导致环境中存在重复条目，这些环境具有大量嵌套类别。
1. **ACSD-66807**： `report_viewed_product_index`表显示的产品页面查看次数不正确。
1. **ACSD-67383**：在同一会话中以客户身份登录并拥有两个公司管理员帐户会导致&#x200B;*没有cartId为*&#x200B;的此类实体错误。
1. **ACSD-67518**：当行数超过批次大小时，高级报表会生成重复的标题行。
1. **ACSD-67639**：为&#x200B;**[!UICONTROL Dynamic Price]**&#x200B;设置为&#x200B;*No*&#x200B;的捆绑产品创建贷项通知单失败。
1. **ACSD-67696**：缓存刷新后，`media_gallery`条目未返回到Cart GraphQL产品节点中。
1. **ACSD-67946**：购物车更新显示重复的错误横幅。
1. **ACSD-68011**：可以通过`/V1/sharedCatalog/:id/assignProducts` [!DNL REST] API将不存在的SKU分配给共享目录。
1. **ACSD-68118**： `customerCart` GraphQL查询返回的产品属性值未反映商店标头，从而导致本地化不一致。
1. **ACSD-68092**：由于计划更新与基本产品数据之间的同步不当，多次保存后捆绑产品选项丢失。
1. **ACSD-67424**： `updated_at` `GET /carts/search` API响应中的[!DNL REST]值与使用可协商引号时&#x200B;**[!UICONTROL Admin panel]**&#x200B;中显示的值不匹配。
1. **ACSD-67187**：限制到非默认网站的管理员用户看到此错误，*“*”请至少创建一个公共共享目录以继续*，并且无法访问公司网格上的&#x200B;**[!UICONTROL Add New Company]**&#x200B;按钮。

使用左侧的菜单导航到特定的修补程序页面。
