---
title: 数据迁移后的步骤
description: 了解在使用[!DNL Data Migration Tool]将数据从Magento 1迁移到Magento 2后应采取哪些步骤。
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '84'
ht-degree: 0%
---
# 数据迁移后的步骤

完成迁移并彻底测试新的Magento 2站点后，执行以下任务：

* 将Magento 1置于维护模式并永久停止所有管理员活动

* 启动Magento 2 cron作业

* [刷新所有Magento 2缓存类型](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [重新索引所有Magento 2索引器](../../../configuration/cli/manage-indexers.md#reindex)

* 更改DNS和负载平衡器以指向Magento 2生产硬件
