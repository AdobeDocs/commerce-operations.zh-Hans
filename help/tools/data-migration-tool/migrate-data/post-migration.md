---
title: 数据迁移后步骤
description: 了解使用 [!DNL Data Migration Tool] 将数据从Magento1迁移到Magento2。
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 数据迁移后步骤

完成迁移并对新的Magento2站点进行全面测试后，请执行以下任务：

* 将Magento1置于维护模式并永久停止所有 [管理员](https://glossary.magento.com/admin) 活动

* 开始Magento2 cron作业

* [刷新所有Magento2缓存类型](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-cache.html#clean-and-flush-cache-types)

* [重新编入所有Magento2索引器的索引](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#reindex)

* 更改DNS和负载平衡器以指向Magento2生产硬件
