---
title: 有效的缓存规划
description: 请参阅推荐的缓存基准，以确保网站在加载时成功运行。
exl-id: 275eb21d-fa52-4b97-9453-8f8553128b53
source-git-commit: 87e379aff4ec57f15ce914a13b4e9bc2769e6d1c
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# 规划在负载下实现电子商务成功的有效缓存

在负载下提供购物体验将需要精心规划的缓存策略。 虽然最初，业务利益相关方的请求可能是始终向客户显示实时产品数据，但这并不是系统资源的最佳使用方式，最终用户站点性能的影响将大大超过持续显示实时信息的好处。

因此，缓存策略的初始步骤应当是与相关利益相关方一起，为网站的不同区域定义一个可接受的缓存计时矩阵，例如：

| 缓存区域 | 多久更改一次？ | 从缓存提供的过时内容是否有影响 | 可接受的缓存生存时间(TTL)? |
|---------------------------------------------------------------|--------------------|-------------------------------------------|-----------------------------------------------------|
| 网站内容HTML页面，通过CMS更新。 | 偶然 | 低 | 1天 |
| 网站内容模板媒体/资产 — 徽标、CSS设计、图像 | 偶然 | 低 | 1周 |
| 产品列表页面(PLP) | 偶然 | 中 | 1天 |
| 产品详细信息页面(PDP) | 有时 | 中 | 1小时 |
| 产品类别 | 偶然 | 中 | 1天 |
| 价格 | 经常 | 高 | 无缓存 |
| 库存/库存 | 经常 | 高 | 无缓存 |
| 网站搜索 | 最多用户独特 | 中 | 缓存前100个搜索短语的结果，为期1天 |
| 结帐 | 每个独特用户 | 非常高 | 无缓存 |
| 购物车 | 每个独特用户 | 非常高 | 无缓存 |
| 付款页面 | 每个独特用户 | 非常高 | 无缓存 |

在初始规划完成后，技术配置可以开始到位，以根据这些要求配置缓存。

即使内容已更新并且需要在缓存TTL内生存，在大多数情况下，也可以手动清除 [AEM dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=en) 和 [Adobe Commerce](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cache.html#config-cli-subcommands-cache-clean) 会选择性地缓存该内容，这意味着将立即反映紧急更改。 手动缓存清除的过程也应事先进行规划和测试，以便如果需要手动对某些内容强制进行更新，则会将其记录到站点操作Runbook中，并明确操作过程中需要涉及的方式和人员。
