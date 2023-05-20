---
title: 此 [!UICONTROL Summary] 標籤
description: 瞭解 [!UICONTROL Summary] 索引標籤/ [!DNL Observation for Adobe Commerce].
exl-id: b07ed898-a211-4353-a1d4-1b71d4898b93
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2653'
ht-degree: 0%

---

# 此 [!UICONTROL Summary] 標籤

此 [!UICONTROL Summary] 索引標籤/ [!DNL Observation for Adobe Commerce] 旨在快速瞭解網站所遇到的一些問題，協助您自動解決或找出網站問題的可能根本原因。 其他標籤提供有關元件服務、資料庫、基礎架構和程式狀態的更深入層級資訊。

## [!UICONTROL Transaction Overview]

![交易概要](../../assets/tools/transaction-overview.jpg)

### [什麼是交易？](https://docs.newrelic.com/docs/apm/transactions/intro-transactions/transactions-new-relic-apm/#:%7E:text=transactions%20are%20reported.-，What%20is%20a%20transaction%3F，work%20in%20a%20software%20application。&amp;text=For%20APM%2C%20it%20will%20overly，當%20the%20response%20is%20sent)

&quot;於 [!DNL New Relic]，交易被定義為軟體應用程式中一個邏輯工作單位。 具體來說，它是指組成該工作單位的函式呼叫和方法呼叫。 這通常指的是Web交易，代表從應用程式收到Web請求到傳送回應時所發生的活動。」

### 交易型別：

**網頁：** Web交易是以HTTP要求起始。 對於大多陣列織而言，這些代表以客戶為中心的互動，因此是最重要的要監控的交易。

**非網頁：** 非Web交易並非透過Web請求起始。 它們可以包括非Web工作者處理序、背景處理序、指令碼、訊息佇列活動和其他工作。

如果您檢視 **[!UICONTROL Transaction Overview]** 框架上，有將近53,000筆交易，平均APDEX分數為。76，而其中95%的交易發生在2.313秒內。 如果在較短時間範圍內有APDEX點選，則較短時間範圍可能會顯示與目前平均值的偏離。

## [!UICONTROL 404 page errors frame]

![404頁錯誤框架](../../assets/tools/404-page-errors.jpg)

此 **[!UICONTROL 404 page errors]** 框架列出 [URI](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier) 以及所選時間範圍內的404頁錯誤計數。

## [!UICONTROL % of Storage Free frame]

![可用儲存空間影格的百分比](../../assets/tools/percent-of-storage-free.jpg)

此 **[!UICONTROL % of Storage Free]** frame會顯示叢集所有節點之儲存裝載的平均可用百分比。 例如，如果您有三節點叢集，框架會顯示\&lt;mount point=&quot;&quot;>， \&lt;environment name=&quot;&quot;>. 如果三個節點之間有變數，則此框架可能是欺騙性的。 一個變異的範例是如果 `/data/mysql` 掛接點free是三個節點叢集上的不同值。 下方有一個框架 [!UICONTROL MySQL] 標籤可依節點名稱對掛載點進行多面處理，以更精確地檢視 `/data/mysql` 每個節點上的可用儲存空間實際上都是。

## [!UICONTROL % of system memory that is free frame]

![可用框架的系統記憶體百分比](../../assets/tools/percent-of-system-memory-that-is-free.jpg)

此 **可用系統記憶體的%** frame會依節點顯示每個節點上可用的系統記憶體數量。

## [!UICONTROL Swap memory free in bytes]

![交換可用記憶體（以位元組為單位）](../../assets/tools/swap-memory-free-in-bytes.jpg)

此 **[!UICONTROL Swap memory free in bytes]** 框架會依節點顯示節點上可用的SWAP記憶體數量。

## [!UICONTROL CPU % by host]

![依主機的CPU百分比](../../assets/tools/cpu-percent-by-host.jpg)

所有環境和節點的彙總會顯示在 **[!UICONTROL CPU % by host]** 框架。 您應取消選取非生產環境。 也請注意生產環境的所有節點不存在的任何例項。 有關高CPU使用率的更多提示，請參閱 [在Adobe Commerce上使用New Relic進行效能疑難排解](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce.html).

## [!UICONTROL Alerts during timeframe]

![時間範圍內的警報](../../assets/tools/alerts-during-timeframe.jpg)

此 **[!UICONTROL Alerts during timeframe]** 顯示所有警示，包括 [!UICONTROL Managed Alerts] 由Adobe Commerce支援新增。

## [!UICONTROL CPU Usage]

![CPU使用量](../../assets/tools/cpu-usage.jpg)

如果 **[!UICONTROL CPU Usage]** 框架是空白的，這表示基礎建設應用程式 [!DNL New Relic] 未啟用。 如果您的網站在入門版，您不會看到此資訊。 如果您的網站位於Pro，請開啟 [支援票證](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) 擁有 [!DNL New Relic Infrastructure] 已為您的網站啟用。

## [!UICONTROL Average Response Time]

![平均回應時間](../../assets/tools/average-response-time.jpg)

此 **[!UICONTROL Average Response Time]** 圖表顯示交易的平均回應時間（網頁和其他專案）。

## [!UICONTROL Long duration cron_schedule updates]

![長時間的cron_schedule更新](../../assets/tools/long-duration-cron-schedule-updates.jpg)

此 **[!UICONTROL cron_schedule]** 表格會在cron工作的開始和完成時寫入。 長時間的cron作業可能表示更新此表格時的延遲，這可能表示cron棧疊或cron排程方式的問題。

## [!UICONTROL Response Code]

![回應代碼](../../assets/tools/response-code.jpg)

此 **[!UICONTROL Response Code]** 框架能很好地顯示網路流量和請求的回應代碼。 它是 [!DNL New Relic's] 交易資料，並以 `httpResponseCode` 已傳回。

## [!UICONTROL Web Traffic volume compared with one week ago Magento Managed Alerts Information]

![網站流量與一星期前比較](../../assets/tools/web-traffic-volume-compared.jpg)

此框架顯示過去一週與本週的比較Web流量。

## [!UICONTROL Deployment Log Entries]

![部署記錄專案](../../assets/tools/deployment-log-entries.jpg)

此 **[!UICONTROL Deployment Log Entries]** frame會顯示部署和雲端記錄專案的計數，並根據部署記錄名稱多面向計數。

## [!UICONTROL Deployment State]

![部署狀態](../../assets/tools/deployment-state.jpg)

此 **[!UICONTROL Deployment State]** 框架會從部署記錄檔中多面向特定的部署階段。 以下是記錄檔和Facet名稱中計算的一些階段範例：

**部署記錄階段：**

* &#39;%Start產生命令%&#39;)為&#39;start_gen&#39;
* &#39;%git將/app/vendor/magento/ece-tools/patches%&#39;)套用為&#39;apply_patches&#39;
* &#39;%Set flag： .static_content_deploy%&#39;)設為&#39;SCD&#39;
* &#39;%NOTICE： Generate command completed%&#39;)為&#39;gen_compl&#39;
* &#39;%NOTICE： Deployment completed%&#39;)為&#39;deploy_compl&#39;
* &#39;%NOTICE：正在啟動後部署。%&#39;)作為&#39;start_pdeploy&#39;
* &#39;%NOTICE： Post-deploy is complete%&#39;)為&#39;pdeploy&#39;
* &#39;%deploy-complete%&#39;)作為&#39;cl_deploy_compl&#39;

## [!UICONTROL IP Frequency]

![IP頻率](../../assets/tools/ip-frequency.jpg)

此 **[!UICONTROL IP Frequency]** frame會計算（&#39;MISS&#39;和&#39;PASS&#39;）中每個IP的狀態， [!DNL Fastly] 記錄。 具有這些狀態的網頁請求會連線至原始伺服器，並將新增負載至伺服器。 它會顯示頻率排名前20的地址。 此框架可用來偵測網站上的IP攻擊或大量負載來源。

## [!UICONTROL IP Response – top 20 URLs in duration]

![ip回應 — 持續時間內前20個url](../../assets/tools/ip-response-top-20-urls.jpg)

此 **[!UICONTROL IP Response – top 20 URLs in duration]** 框架會顯示回應持續時間最長的URL。 這可能表示大型影像檔案或頁面、API或回應持續時間最長的頁面。

## [!UICONTROL API Calls by IP]

![依ip的api呼叫](../../assets/tools/api-calls-by-ip.jpg)

此 **[!UICONTROL API Calls by IP]** frame有助於識別針對API和IP位址的大量流量，以從API URL提出請求。

## [!UICONTROL API Calls by IP, details by URL]

![依ip依url的api呼叫詳細資料](../../assets/tools/api-calls-by-ip-details-by-url.jpg)

此 **[!UICONTROL API Calls by IP, details by URL]** frame會針對API提供大量流量的詳細資訊，以及提出請求的URL的詳細資訊。

## [!UICONTROL IP Frequency Rate per minute]

![每分鐘的ip頻率速率](../../assets/tools/ip-frequency-rate-per-minute.jpg)

有時很難分辨哪個IP位址在其他影格上的請求最多。 此 **[!UICONTROL IP Frequency Rate per minute]** frame顯示每個IP位址的每分鐘速率。

## [!UICONTROL Potential Bots]

![潛在的機器人](../../assets/tools/potential-bots.jpg)

此 **[!UICONTROL Potential Bots]** frame會檢視具有request_user_agent名稱（例如NULL或&#39;%bot%&#39;）的請求。 通常&#39;%bot%&#39; request_user_agent會遵循中的原則設定 `robots.txt` 檔案。

## [!UICONTROL Transaction Errors]

![交易錯誤](../../assets/tools/transaction-errors.jpg)

此 **[!UICONTROL Transaction Errors]** frame顯示來自的異動錯誤計數 [!DNL New Relic].

## [!UICONTROL Nginx access by node]

![依節點的nginx存取](../../assets/tools/nginx-access-by-node.jpg)

此 **[!UICONTROL Nginx access by node]** 框架會從 `access.log` 依節點。 檢視負載是否均勻分佈很有幫助。 它通常會顯示節點何時中斷。 框架也會顯示整個網站的負載。

## [!UICONTROL Galera Log]

![galera記錄](../../assets/tools/galera-log.jpg)

[[!DNL Galera]](https://galeracluster.com/library/galera-documentation.pdf) 用於資料庫叢集。 此框架著重於來自以下專案的特定訊號： [!UICONTROL Galera] 叢集。 訊號著重於進入和退出叢集的節點，這是維護資料庫資料完整性的正常行為。 節點會保持同步化為 [!UICONTROL Galera] 叢集狀態變更。

**以下專案清單： [!UICONTROL Galera] 狀態變更：**

* &#39;%1047 WSREP尚未準備應用程式use%&#39;的節點)為&#39;node_not_prep_for_use&#39;
* &#39;%\[ERROR\] WSREP：無法從wsrep_sst_xtrabackup-v2%&#39;讀取為&#39;xtrabackup_read_fail&#39;
* &#39;%\[ERROR\] WSREP：處理程式已完成，但發生錯誤： wsrep_sst_xtrabackup-v2 %&#39;)為&#39;xtrabackup_compl_w_err&#39;
* &#39;%\[ERROR\] WSREP： rbr write fail%&#39;)作為&#39;rbr_write_fail&#39;
* &#39;%self-leave%&#39;)作為&#39;susp_node&#39;
* &#39;%members = 3/3 （已加入/總計）%&#39;)作為&#39;3of3&#39;
* &#39;%members = 2/3 （已加入/總計）%&#39;)作為&#39;2of3&#39;
* &#39;%members = 2/2%&#39;) as &#39;2of2&#39; * &#39;%members = 1/2%&#39;) as &#39;1of2&#39; * &#39;%members = 1/3%&#39;) as &#39;1of3&#39;
* &#39;%members = 1/1%&#39;)作為&#39;1of1&#39;
* &#39;%\[注意\] /usr/sbin/mysqld (mysqld 10.%&#39;)作為&#39;sql_restart&#39;
* &#39;%Quorum：沒有具有完整狀態的節點：%&#39;)為&#39;no_node_count&#39;
* &#39;%WSREP： Member 0%&#39;)作為&#39;mem_0&#39;
* &#39;%WSREP： Member 1.0%&#39;)作為&#39;mem_1&#39;
* &#39;%WSREP：成員2%&#39;)為&#39;mem2&#39;
* &#39;%WSREP：與群組同步，已準備好連線%&#39;)為&#39;ready&#39;
* &#39;%/usr/sbin/mysqld，版本：%&#39;)為&#39;mysql_restart_mysql.slow&#39;
* &#39;%\[Note\] WSREP：新叢集檢視：全域狀態：%&#39;)為&#39;galera_cluster_view_chng&#39;

如果狀態頻繁變更，這些訊號可能表示儲存、記憶體或查詢問題。

## [!UICONTROL Database errors]

![資料庫錯誤](../../assets/tools/database-errors.jpg)

**偵測到資料庫錯誤或訊息的清單：**

* &#39;%配置給暫存資料表的記憶體大小超過innodb_buffer_pool_size%&#39;的20%)為&#39;temp_tbl_buff_pool&#39;
* &#39;%\[ERROR\] WSREP： rbr write fail%&#39;)作為&#39;rbr_write_fail&#39;
* &#39;%mysqld：磁碟已滿%&#39;)做為&#39;disk_full&#39;
* &#39;%Error number 28%&#39;)作為&#39;err_28&#39;
* &#39;%rollback%&#39;)作為&#39;rollback&#39;
* &#39;%Foreign key constraint對資料表%&#39;失敗)，因為&#39;foreign_key_constraint&#39;
* &#39;%Error_code： 1114%&#39;)作為&#39;sql_1114_full&#39;
* &#39;%CRITICAL： SQLSTATE\[HY000\] \[2006\] MySQL伺服器已消失%&#39;)為&#39;sql_gone&#39;
* &#39;%SQLSTATE\[HY000\] \[1040\]太多連線%&#39;)為&#39;sql_1040&#39;
* &#39;%CRITICAL： SQLSTATE\[HY000\] \[2002\]%&#39;)為&#39;sql_2002&#39;
* &#39;%SQLSTATE\[08S01\]：%&#39;)作為&#39;sql_1047&#39;
* &#39;%\[Warning\]已中止連線%&#39;)為&#39;aborted_conn&#39;
* &#39;%SQLSTATE\[23000\]：完整性條件約束違規：%&#39;)為&#39;sql_23000&#39;
* &#39;%1205 Lock等待逾時%&#39;)為&#39;sql_1205&#39;
* &#39;%SQLSTATE\[HY000\] \[1049\]未知的資料庫%&#39;)為&#39;sql_1049&#39;
* &#39;%SQLSTATE\[42S02\]：找不到基底資料表或檢視：%&#39;)為&#39;sql_42S02&#39;
* &#39;%General error： 1114%&#39;)作為&#39;sql_1114&#39;
* &#39;%SQLSTATE\[40001\]%&#39;)為&#39;sql_1213&#39;
* &#39;%SQLSTATE\[42S22\]：找不到資料行： 1054 Unknown column%&#39;)為&#39;sq1_1054&#39;
* &#39;%SQLSTATE\[42000\]：語法錯誤或存取違規：%&#39;)為&#39;sql_42000&#39;
* &#39;%SQLSTATE\[21000\]：基數違規：%&#39;)為&#39;sql_1241&#39;
* &#39;%SQLSTATE\[22003\]：%&#39;)為&#39;sql_22003&#39;
* &#39;%SQLSTATE\[HY000\] \[9000\]具有IP位址%的使用者端)為&#39;sql_9000&#39;
* &#39;%SQLSTATE\[HY000\]：一般錯誤： 2014%&#39;)為&#39;sql_2014&#39;
* &#39;%1927連線已終止%&#39;)為&#39;sql_1927&#39;
* &#39;%1062 \[\ERROR\] InnoDB：%&#39;)作為&#39;sql_1062_e&#39;
* &#39;%\[Note\] WSREP：正在將記憶體對應排清至磁碟……%&#39;)做為&#39;mem_map_flush&#39;
* &#39;%Internal MariaDB錯誤碼： 1146%&#39;)為&#39;sql_1146&#39;
* &#39;%Internal MariaDB錯誤碼： 1062%&#39;)為&#39;sql_1062&#39; * &#39;%1062 \[Warning\] InnoDB：%&#39;)為&#39;sql_1062_w&#39;
* &#39;%Internal MariaDB錯誤碼： 1064%&#39;)為&#39;sql_1064&#39;
* &#39;%InnoDB：檔案中的宣告失敗%&#39;)為&#39;assertion_err&#39;
* &#39;%mysqld_safe目前執行的處理序數目： 0%&#39;)為&#39;mysql_oom&#39;
* &#39;%\[ERROR\] mysqld取得signal%&#39;)為&#39;mysql_sigterm&#39;
* &#39;%1452 Cannot add%&#39;)為&#39;sql_1452&#39;
* &#39;%ERROR 1698%&#39;)作為&#39;sql_1698&#39;
* &#39;%SQLSTATE\[HY000\]：一般錯誤： 3%&#39;)為&#39;cnt_wrt_tmp&#39;
* &#39;%General error： 1 %&#39;)作為&#39;sql_syntax&#39;
* &#39;%42S22%&#39;)做為&#39;sql_42S22&#39;
* &#39;%InnoDB：錯誤（索引鍵重複）%&#39;)，因為&#39;innodb_dup_key&#39;

## [!UICONTROL Database traces]

![資料庫追蹤](../../assets/tools/database-traces.jpg)

此 **[!UICONTROL Database traces]** 框架會檢視以下專案的資料： [sql追蹤](https://docs.newrelic.com/docs/apm/transactions/transaction-traces/transaction-traces-database-queries-page/) 實體 [!DNL New Relic] 和會傳回追蹤的路徑。

## [!UICONTROL Database mysql-slow.log]

![資料庫mysql-slow.log](../../assets/tools/database-mysql-slow-log.jpg)

此 **[!UICONTROL Database mysql-slow.log]** frame會計算 [mysql-slow.log](https://dev.mysql.com/doc/refman/5.7/en/slow-query-log.html) 依查詢要求型別。 它會以視覺化方式隔離可能與mysql-slow.log （緩慢查詢記錄）有關的時間範圍。 查詢沒有索引的表格或更新大型表格的查詢可能會封鎖其他查詢。

## [!UICONTROL Redis synchronization from Log]

![記錄檔的redis同步](../../assets/tools/redis-synchronization-from-log.jpg)

[[!DNL Redis]](https://redis.io/docs/about/) 是開放原始碼（BSD授權）的記憶體內資料結構存放區，用於資料庫、快取和訊息代理人。 如果已設定，它可以執行資料庫和工作階段快取。 此 **[!UICONTROL Redis synchronization from Log]** 影格焦點在 [[!DNL Redis] 同步](https://redis.io/docs/manual/replication/). 越大 [!DNL Redis] 資料集，同步化發生問題的可能性就越大（需要保持同步的資料更多）。

**[!DNL Redis]錯誤和訊息：**

* &#39;%SLAVE同步處理：裝置%&#39;上沒有剩餘的空間)作為&#39;space&#39;
* &#39;%Server started， Redis version%&#39;)作為&#39;serv_start&#39;
* &#39;%伺服器現在已準備好接受連線%&#39;)為&#39;ready&#39;
* 與主要的&#39;%Connection遺失。%&#39;)，作為&#39;mstr_lost&#39;
* &#39;%+sdown sentinel%&#39;)做為&#39;+sentinal&#39;
* &#39;%-sdown sentinel%&#39;)做為&#39;-sentinal&#39;
* &#39;%-sdown slave%&#39;)為&#39;-slave&#39;，&#39;%+sdown slave%&#39;)為&#39;+slave&#39;
* &#39;%-failover-abort-not-selected master%&#39;)作為&#39;-failover&#39;
* &#39;%+failover-abort-not-selected master%&#39;)作為&#39;+failover&#39;
* &#39;%無法部分重新同步化（無快取的主版）%&#39;)為&#39;part_sync_err&#39;
* &#39;%MASTER已中止復寫，錯誤為： ERR Can%&#39;)為&#39;mstr_sync_err&#39;
* &#39;%Master不支援PSYNC或處於錯誤狀態%&#39;)作為&#39;mstr_psync_err&#39;
* &#39;%SLAVE同步：已完成，成功%&#39;)為&#39; slv_sync_suc&#39;
* &#39;%MASTER已中止復寫，錯誤為： ERR Can%&#39;)為&#39;mstr_sync_err，coun&#39;
* &#39;%OOM命令在使用記憶體%&#39;時不允許使用)作為&#39; max_mem_err&#39;
* &#39;%CredisException（代碼： 0）：連線%&#39;發生讀取錯誤)為&#39;credis_read_error&#39;
* &#39;%Uncaught RedisException：%&#39;)作為&#39;redis_excp_err&#39;
* &#39;%psync已排定在ASAP關閉，以克服輸出緩衝區%&#39;)作為&#39;output_buf_err&#39;

## [!UICONTROL PHP process states]

![PHP處理狀態](../../assets/tools/php-process-states.jpg)

PHP流程的行為方式取決於 [設定](https://www.php.net/manual/en/install.fpm.configuration.php). 設定很複雜，有許多變數和選項。 此 **[!UICONTROL PHP process states]** 框架可協助您瞭解PHP處理序何時終止和重新啟動。

### [!UICONTROL PHP errors]

![php錯誤](../../assets/tools/php-errors.jpg)

此 **[!UICONTROL PHP errors]** 框架顯示所選時間範圍內背景程式的PHP錯誤數目。 如需詳細資訊，請參閱 [Adobe Commerce PHP設定](../../installation/prerequisites/php-settings.md).

**PHP錯誤和訊息：**

* &#39;%worker_connections不足%&#39;)做為&#39;worker&#39;
* &#39;%PHP嚴重錯誤：允許的記憶體大小！%&#39;)，作為&#39;mem_size&#39;
* &#39;%exited on signal 11 (SIGSEGV)%&#39;)為&#39;sig_11&#39;
* &#39;%exited on signal 7 (SIGBUS)%&#39;)為&#39;sig_7&#39;
* &#39;%increase pm.start_servers%&#39;)作為&#39;pmstart_serv&#39;
* &#39;%max_children%&#39;)做為&#39;max_children_cnt&#39;
* &#39;%PHP嚴重錯誤：允許的記憶體大小為%&#39;)為&#39;mem_exhst_coun&#39;
* &#39;%無法為集區%配置記憶體&#39;)做為&#39;opc_mem_count&#39;
* &#39;%Warning Interned string buffer overflow%&#39;)作為&#39;opc_str_buf&#39;
* &#39;%Illegal string offsetl%&#39;)做為&#39;opc_sv_comments&#39;
* &#39;%PHP嚴重錯誤：未攔截到的RedisException：連線%&#39;上的讀取錯誤)為&#39;php_exc&#39;

## [!UICONTROL PHP processes]

![php程式](../../assets/tools/php-processes.jpg)

[PHP-FPM](https://php-fpm.org/) 是 [!UICONTROL FastCGI Process Manager] 使用者 [!DNL Nginx]. 若要瞭解系統需求，請參閱 [對應至Adobe Commerce版本的PHP版本要求](../../installation/system-requirements.md). 此 **[!UICONTROL PHP processes]** frame顯示在所選時間軸中特定時間執行的PHP處理序數目。

## [!UICONTROL Secondary processes]

![次要程式](../../assets/tools/secondary-processes.jpg)

次要程式可能會影響網站回應。 此 **[!UICONTROL Secondary processes]** 框架表示可能增加網站負載的一或多個程式。 資料庫的主要次要處理序執行次數最多。

## [!UICONTROL Traffic vs Week Ago]

![流量與周前](../../assets/tools/traffic-vs-week-ago.jpg)

此 **[!UICONTROL Traffic vs Week Ago]** frame會檢視來自的網站流量（請求）。 [!DNL Fastly] (&#39;MISS&#39;， &#39;PASS&#39;)快取狀態的記錄。 這些要求會將負載新增至原始伺服器。 此影格顯示本週與上週前同一時間範圍內的比較Web請求量。

## [!UICONTROL Fastly Cache]

![fastly快取](../../assets/tools/fastly-cache.jpg)

此 **[!UICONTROL Fastly Cache]** frame顯示來自的請求之快取狀態的彙總檢視。 [!DNL Fastly] 記錄。 如果您選取ERROR，它會顯示請求中的錯誤百分比。 當原始伺服器對頁面要求的回應速度不夠快時，這個數字通常會增加。

## [!UICONTROL Page Rendering]

![頁面呈現](../../assets/tools/page-rendering.jpg)

此 **[!UICONTROL Page Rendering]** frame顯示當週頁面檢視來源的平均頁面轉譯持續時間： [!DNL New Relic] 與相同時段的前一週比較。

## [!UICONTROL Page loading detail]

![頁面載入詳細資料](../../assets/tools/page-loading-detail.png)

此 **[!UICONTROL Page loading detail]** 框架說明頁面載入事件。 它詳細說明這些Facet的意義。 以下是為此框架執行的查詢：

`SELECT percentile(timeToResponseStart, 50) AS 'first byte', percentile(firstPaint, 50) as 'First paint', percentile(firstContentfulPaint, 50) as 'First contentful paint', percentile(timeToDomContentLoadedEventEnd, 50) AS 'DOM content loaded', percentile(duration, 50) AS 'Window load + AJAX' FROM BrowserInteraction TIMESERIES`

## [!UICONTROL Transactions – Avg, Max, Min]

![交易 — 平均、最大、最小](../../assets/tools/transactions-avg-max-min.jpg)

交易持續時間以秒為單位。 視交易而定，如果交易長時間執行，可能會影響其他交易。 列在名稱和持續時間下方的交易是針對特定時段的。 如果問題時間範圍很簡潔，請調整 [!DNL Observation for Adobe Commerce] 該狹窄時間範圍的日期/時間選擇器。

## [!UICONTROL Admin Activities]

![管理員活動](../../assets/tools/admin-activities.jpg)

此 **[!UICONTROL Admin Activities]** frame會識別與管理員使用者的交易。

## [!UICONTROL Order transactions (default?)]

![訂單異動預設值](../../assets/tools/order-transactions-default.jpg)

此 **[!UICONTROL Order transactions (default?)]** 框架尋找交易 `request.headers.host` 來自交易，名稱= `WebTransaction/Action/checkout/onepage/success`. 如果訂單成功URL不同，此框架將沒有資料。

## [!UICONTROL Elasticsearch Index information]

![elasticsearch索引資訊](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

**[Elasticsearch狀態：](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html)**

* 綠色：指派所有分片。
* 黃色：會指派所有主要分片，但會取消指派一或多個復本分片。 如果叢集中的某個節點失敗，則修復該節點之前，某些資料可能無法使用。
* 紅色：有一或多個主要分片未指派，因此無法取得部分資料。 在叢集啟動期間，當指派主要分片時，可能會短暫發生這種情況。

## [!UICONTROL Elasticsearch Errors]

![elasticsearch錯誤](../../assets/tools/elasticsearch-errors.jpg)

**[!DNL Elasticsearch]錯誤：**

* &#39;%all shards failed%&#39;為&#39;all_shards_failed&#39;
* &#39;%NoNodesAvailableException%&#39;做為&#39;no_alive_nodes&#39;
* &#39;%PHP嚴重錯誤：未攔截到的錯誤：Elasticsearch%&#39;的引數錯誤，為&#39;wrong_param&#39;
* &#39;%您可以修正此問題，方法是將Magento雲端基礎結構上的Elasticsearch服務升級為&#39;ver_err&#39;版本%&#39;
* &#39;%cluster健全狀態從\[YELLOW\]變更為\[RED\] (原因：%&#39;為&#39;yel_red&#39;
* &#39;%device%&#39;上沒有剩餘的空間，因為&#39;no_space&#39;
* &#39;%無法執行[SearchRequest{searchType=%&#39;，因為&#39;failed_query&#39;

## [!UICONTROL Cron view]

![cron檢視](../../assets/tools/cron-view.jpg)

此 **[!UICONTROL Cron view]** frame會檢視cron記錄，以取得開始的cron數目與cron完成數目之間的平衡。


## [!UICONTROL Cron error]

![cron錯誤](../../assets/tools/cron-error.png)

**cron.log中的Cron錯誤：**

* &#39;%_stg%&#39;做為&#39;stg_crons&#39;
* &#39;%Could not acquire lock for cron job%&#39; as &#39;cron_lock&#39;
* &#39;%一般錯誤： 2006 MySQL伺服器已經離開%&#39;為&#39;mysql_has_gone_away&#39;
* &#39;%error%&#39;為&#39;error&#39;
* &#39;%一般錯誤： 1205 Lock等待逾時%&#39; as sql_1205_cron

## [!UICONTROL cron_schedule table updates]

![cron_schedule表格更新](../../assets/tools/cron-schedule-table-updates.jpg)

此 **[!UICONTROL cron_schedule table updates]** frame會檢視資料存放區作業更新涉及cron_schedule表格的最長持續時間（以秒為單位）。 它以SQL要求型別為分面。

## [!UICONTROL Datastore Operations Tables]

![資料存放區操作表格](../../assets/tools/datastore-operations-tables.jpg)

此 **[!UICONTROL Datastore Operations Tables]** frame會依持續時間、表格名稱和SQL要求型別顯示前25個作業。 暫留在尖峰上，可檢視正在存取哪個表格以及按哪個請求型別存取的詳細資訊。

## [!UICONTROL Cache Flush]

![快取排清](../../assets/tools/cache-flush.jpg)

**偵測到快取排清：**

* &#39;%config%&#39;為&#39;config_cache_flushed&#39;
* &#39;%layout%&#39;作為&#39;layout_cache_flush&#39;
* &#39;%block_html%&#39;做為&#39;block_html_cache_flush&#39;
* &#39;%collections%&#39;作為&#39;collections_cache_flush&#39;
* &#39;%reflection%&#39;做為&#39;reflection_cache_flush&#39;
* &#39;%db_ddl%&#39;做為&#39;db_ddl_cache_flush&#39;
* &#39;%compiled_config%&#39;做為&#39;compiled_config_cache_flush&#39;
* &#39;%eav%&#39;為&#39;eav_cache_flush&#39;
* &#39;%customer_notification%&#39;作為&#39;cust_notif_cache_flush&#39;
* &#39;%config_integration%&#39;作為&#39;config_intege_cache_flush&#39;
* &#39;%config_integration_api%&#39;，作為&#39;config_integg_api_cache_flush&#39;
* &#39;%full_page%&#39;作為&#39;full_page_cache_flush&#39;
* &#39;%config_webservice%&#39;作為&#39;config_webserv_cache_flush&#39;
* &#39;%translate%&#39;作為&#39;translate_cache_flush&#39;
