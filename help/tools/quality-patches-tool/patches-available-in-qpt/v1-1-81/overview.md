---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.81
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.81中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-07-10T16:37:59.584Z'
TQID: 'https://experienceleague.adobe.com/M-ltaMCaVfRfc3vrobfkBCte-P4K2CELj7r3bD-cfxA'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: f73ca9edd0af3cfb0975eb4b13eabc78c20c340e
workflow-type: tm+mt
source-wordcount: 304
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.81

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.81中提供的修补程序所修复的问题。

QPT v1.1.81包含以下修补程序：

1. **ACP2E-4300**：修复了更改[!UICONTROL Admin]中的客户组不会更新店面上的目录权限，从而导致目录和购物车反映过期权限的问题。
1. **ACP2E-4401**：修复了带有可配置产品的主页链接的[!UICONTROL Scheduled Update Preview]重定向到维护页面而不是显示产品列表的问题。
1. **ACP2E-4395**：如果没有为全局范围指定任何金额，Giftcard API产品创建现在将显示错误。
1. **ACP2E-4468**：修复了具有网站范围权限的[!UICONTROL Admin]用户无法编辑横幅内容的问题。
1. **ACP2E-4630**：修复了具有自定义选项的长产品名称在分页后与多页“发票”、“发运”、“贷项通知单”和“退货”PDF中的相邻列或项目重叠，从而使行项目不可读的问题。
1. **ACP2E-4680**：修复了不可销售或删除的产品从最终可协商报价中消失的问题。
1. **ACP2E-4709**：修复了使用Page Builder时CMS页面无法保存的问题。
1. **ACP2E-4786**：修复了在配置AWS S3远程存储时，由于存储驱动程序中的路径解析不正确而导致导出产品无法写入文件的问题。
1. **ACP2E-4801**：修复了以下问题：通过[!UICONTROL Admin]中可转让报价的[!UICONTROL Configure]按钮更新捆绑产品选件数量时未应用，且已放弃更改。
1. **ACP2E-4815**：修复了导致日志中出现PHP异常的多个GraphQL问题，更正了订单与通过GraphQL在订单后创建的客户帐户的关联，并通过HTTP规范将响应与GraphQL保持一致。

使用左侧的菜单导航到特定的修补程序页面。
