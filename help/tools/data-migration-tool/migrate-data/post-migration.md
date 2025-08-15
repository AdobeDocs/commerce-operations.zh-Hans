---
title: 数据迁移后的步骤
description: 了解使用 [!DNL Data Migration Tool] 将数据从Magento 1迁移到Magento 2后要采取的步骤。
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# 数据迁移后的步骤

完成迁移并彻底测试新的Magento 2站点后，请执行以下任务：

* 将Magento 1置于维护模式并永久停止所有管理员活动

* 启动Magento 2 cron作业

* [刷新所有Magento 2缓存类型](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [重新索引所有Magento 2索引器](../../../configuration/cli/manage-indexers.md#reindex)

* 更改DNS和负载平衡器以指向Magento 2生产硬件
