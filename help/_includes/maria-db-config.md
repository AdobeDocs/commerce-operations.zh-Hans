---
source-git-commit: 631735eceb3609edd743c682291f373f6b01b399
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---
# MariaDB配置设置

与以前的MariaDB或MySQL版本相比，对MariaDB 10.4和10.6重新编制索引需要更多时间。 要加快重新索引速度，我们建议设置以下MariaDB配置参数：

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

如果您在升级到MariaDB 10.6后遇到与索引无关的性能下降，请考虑启用 [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) 设置。 例如， `--query-cache-type=ON`.

除了这些建议之外，您还应咨询数据库管理员配置以下参数：

>[!NOTE]
>
>这些设置仅适用于内部部署。 云基础架构上的Adobe Commerce客户无权访问这些设置。

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
