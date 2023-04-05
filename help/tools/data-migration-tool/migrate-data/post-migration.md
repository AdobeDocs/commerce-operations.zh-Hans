---
title: 数据迁移后步骤
description: 了解使用 [!DNL Data Migration Tool] 将数据从Magento1迁移到Magento2。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---


# 数据迁移后步骤

完成迁移并对新的Magento2站点进行全面测试后，请执行以下任务：

* 将Magento1置于维护模式并永久停止所有管理员活动

* 开始Magento2 cron作业

* [刷新所有Magento2缓存类型](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [重新编入所有Magento2索引器的索引](../../../configuration/cli/manage-indexers.md#reindex)

* 更改DNS和负载平衡器以指向Magento2生产硬件
