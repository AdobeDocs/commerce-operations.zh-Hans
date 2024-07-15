---
title: '[!UICONTROL PHP]选项卡'
description: 了解 [!DNL Observation for Adobe Commerce]的[!UICONTROL PHP]选项卡。
exl-id: 0989a7f5-75b0-4fb5-ac5e-2618603bf548
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# [!UICONTROL PHP]选项卡

**PHP**&#x200B;选项卡显示PHP进程问题，以便对PHP问题进行更深入的分析。

## [!UICONTROL PHP active process details]

![PHP活动进程详细信息](../../assets/tools/php-active-process-details.jpg)

**[!UICONTROL PHP active process details]**&#x200B;帧显示选定时间范围内的PHP进程，包括php-fpm。

## [!UICONTROL PHP process load (# of PHP processes and % of CPU load)]

![PHP进程加载](../../assets/tools/php-process-load.jpg)

**[!UICONTROL PHP process load (# of PHP processes and % of CPU load)]**&#x200B;帧显示选定时间范围内来自PHP-FPM进程的CPU负载。

## [!UICONTROL PHP Memory detail]

![PHP内存详细信息](../../assets/tools/php-memory-detail.jpg)

**[!UICONTROL PHP Memory detail]**&#x200B;帧显示选定时间范围内的PHP进程的内存使用情况。

## [!UICONTROL PHP CPU Utilization]

![PHP CPU使用率](../../assets/tools/php-cpu-utilization.jpg)

**[!UICONTROL PHP CPU Utilization]**&#x200B;帧显示选定时间范围内PHP进程的CPU利用率百分比。

## [!UICONTROL PHP Process states]

![PHP进程状态](../../assets/tools/php-process-states-image-1.jpg)

**[!UICONTROL PHP Process states]**&#x200B;帧显示选定时间范围内的PHP进程状态。 它在PHP进程终止和重新启动时显示。 请注意未显示重新启动的已终止PHP进程。

* &#39;%NOTICE：正在终止……%&#39;)为&#39;php_term&#39;
* &#39;%注意：正在退出，再见！%&#39;)作为“php_exit”
* “%注意： fpm正在运行，pid%”)，为“fpm_start”
* &#39;%NOTICE：已准备好处理连接%&#39;)作为&#39;php_ready&#39;

## [!UICONTROL PHP Errors]

![PHP错误](../../assets/tools/php-errors-image-1.jpg)

**[!UICONTROL PHP Errors]**&#x200B;帧显示选定时间范围内的PHP Worker错误数。 解析和显示的错误消息包括：

* “%worker_connections不足%”)
* &#39;%PHP严重错误：允许的内存大小！%&#39;)作为“mem_size”
* &#39;%exited on signal 11 (SIGSEGV)%&#39;)为&#39;sig_11&#39;
* &#39;%exited on signal 7 (SIGBUS)%&#39;)为&#39;sig_7&#39;
* &#39;%increase pm.start_servers%&#39;)作为&#39;pmstart_serv&#39;
* “%max_children%”)作为“max_children_cnt”
* “%PHP致命错误：允许的内存大小为%”)作为“mem_exhst_coun”
* “%Unable to allocate memory for pool%”)，作为“opc_mem_count”
* “%Warning Interned string buffer overflow%”)作为“opc_str_buf”
* “%Illegal string offsetl%”)作为“opc_sv_comments”
* “%PHP严重错误：未捕获的RedisException：连接%”上出现读取错误)，作为“php_exc”

## [!UICONTROL PHP processes count]

![个PHP进程计数](../../assets/tools/php-processes-count.jpg)

**[!UICONTROL PHP processes count]**&#x200B;帧显示选定时间范围内的PHP进程计数。

## [!UICONTROL Database Errors]

![数据库错误](../../assets/tools/php-tab-database-errors.jpg)

**[!UICONTROL Database Errors]**&#x200B;帧显示选定时间范围内的数据库错误。 分析的错误包括：

* &#39;%为临时表分配的内存大小超过innodb_buffer_pool_size%&#39;的20%)，如&#39;temp_tbl_buff_pool&#39;
* “%\[ERROR\] WSREP： rbr write fail%”)作为“rbr_write_fail”
* “%mysqld：磁盘已满%”)作为“disk_full”
* “%Error number 28%”)，作为“err_28”
* “%rollback%”)作为“rollback”
* “%Foreign key constraint对表%”失败)，为“foreign_key_constraint”
* &#39;%Error_code： 1114%&#39;)作为&#39;sql_1114_full&#39;
* &#39;%CRITICAL： SQLSTATE[HY000] [2006] MySQL服务器已消失%&#39;)为&#39;sql_gone&#39;
* &#39;%SQLSTATE[HY000] [1040]连接数太多%&#39;)作为&#39;sql_1040&#39;
* &#39;%CRITICAL： SQLSTATE[HY000] [2002]%&#39;)为&#39;sql_2002&#39;
* “%SQLSTATE[08S01]：%”)作为“sql_1047”
* “%[警告]已中止连接%”)为“aborted_conn”
* “%SQLSTATE[23000]：完整性约束冲突：%”)为“sql_23000”
* “%1205 Lock wait timeout%”)作为“sql_1205”
* “%SQLSTATE[HY000] [1049]未知数据库%&#39;)作为“sql_1049”
* “%SQLSTATE[42S02]：未找到基表或视图：%”)，作为“sql_42S02”
* &#39;%General error： 1114%&#39;)作为&#39;sql_1114&#39;
* “%SQLSTATE[40001]%”)作为“sql_1213”
* “%SQLSTATE[42S22]：找不到列： 1054 Unknown column%&#39;)为“sq1_1054”
* &#39;%SQLSTATE[42000]：语法错误或访问冲突：%&#39;)为&#39;sql_42000&#39;
* “%SQLSTATE[21000]：基数违规：%”)为“sql_1241”
* “%SQLSTATE[22003]：%”)作为“sql_22003”
* “%SQLSTATE[HY000] [9000]客户端，IP地址为%”)作为“sql_9000”
* “%SQLSTATE[HY000]：常规错误： 2014%”)为“sql_2014”
* “%1927连接已终止%”)为“sql_1927”
* “%1062 \[ERROR\] InnoDB：%&#39;)作为“sql_1062_e”
* “%[注意] WSREP：正在刷新内存映射到磁盘……%”)，作为“mem_map_flush”
* &#39;%Internal MariaDB错误代码： 1146%&#39;)为&#39;sql_1146&#39;
* &#39;%Internal MariaDB错误代码： 1062%&#39;)，作为&#39;sql_1062&#39; * &#39;%1062 [警告] InnoDB：%&#39;)，作为&#39;sql_1062_w&#39;
* &#39;%Internal MariaDB错误代码： 1064%&#39;)为&#39;sql_1064&#39;
* “%InnoDB：文件%”中的断言失败)为“assertion_err”
* &#39;%mysqld_safe现在运行的进程数： 0%&#39;)为&#39;mysql_oom&#39;
* “%\[ERROR\] mysqld得到signal%&#39;)作为“mysql_sigterm”
* “%1452无法添加%”)作为“sql_1452”
* “%ERROR 1698%”)作为“sql_1698”
* “%SQLSTATE[HY000]：常规错误： 3%”)作为“cnt_wrt_tmp”
* &#39;%General error： 1 %&#39;)作为&#39;sql_syntax&#39;
* “%42S22%”)作为“sql_42S22”
* “%InnoDB：错误（重复键）%”，因为“innodb_dup_key”

## [!UICONTROL Database traces]

![数据库跟踪](../../assets/tools/php-tab-database-traces.jpg)

**[!UICONTROL Database traces]**&#x200B;框架显示数据库跟踪信息。 此框架与所选时间轴的APM事务摘要视图一致。

## [!UICONTROL Database mysql-slow.log]

![数据库mysql-slow.log](../../assets/tools/php-tab-database-mysql-slow-log.jpg)

**[!UICONTROL Database mysql-slow.log]**&#x200B;框架显示所选时间范围内`mysql-slow.log`文件中包含的查询语句类型。
