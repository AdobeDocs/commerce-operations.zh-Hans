---
user-guide-title: 設定指南
user-guide-description: 設定您的Adobe Commerce或Magento Open Source應用程式功能與服務。
feature: Configuration
source-git-commit: 68c4cfc29735d2ea296f579ed0a0ff52db3fdd9f
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# 設定指南 {#configuration-guide}

+ [概觀](overview.md)
+ 一般設定 {#setup}
   + [應用程式初始化和啟動程式](bootstrap/initialization.md)
   + [應用程式模式](bootstrap/application-modes.md)
   + [Bootstrap引數](bootstrap/set-parameters.md)
   + [設定檔分析](bootstrap/mage-profiler.md)
   + [基底目錄路徑](bootstrap/mage-directory.md)
+ 部署 {#deployment}
   + [部署概觀](deployment/overview.md)
   + [單一電腦部署](deployment/single-machine.md)
   + [管道部署](deployment/technical-details.md)
   + [必要條件](deployment/prerequisites.md)
   + [開發系統設定](deployment/development-system.md)
   + [建置系統設定](deployment/build-system.md)
   + [生產系統設定](deployment/production-system.md)
   + [檔案系統存取許可權](deployment/file-system-permissions.md)
   + 範例 {#examples}
      + [使用共用設定](deployment/example-shared-configuration.md)
      + [使用CLI命令](deployment/example-using-cli.md)
      + [使用環境變數](deployment/example-environment-variables.md)
+ 快取 {#cache}
   + [快取概述](cache/caching-overview.md)
   + [快取型別](cache/cache-types.md)
   + [快取選項](cache/cache-options.md)
   + [L2快取](cache/level-two-cache.md)
   + Redis {#redis}
      + [設定Redis](cache/config-redis.md)
      + [預設快取使用Redis](cache/redis-pg-cache.md)
      + [將Redis用於工作階段儲存](cache/redis-session.md)
   + 清漆 {#varnish}
      + [塗漆概述](cache/config-varnish.md)
      + [安裝清漆](cache/config-varnish-install.md)
   + [網頁伺服器](cache/config-varnish-server.md)
   + [設定商務應用程式](cache/configure-varnish-commerce.md)
   + [進階清漆設定](cache/config-varnish-advanced.md)
   + [快取清除](cache/use-varnish-cache.md)
   + [快取清除多個Varnish例項](cache/use-multiple-varnish-cache.md)
   + [驗證清漆組態](cache/config-varnish-final.md)
   + [清漆ESI區塊](cache/use-varnish-esi.md)
   + [靜態內容快取](cache/static-content-signing.md)
+ 命令列 {#cli}
   + [命令列工具](cli/config-cli.md)
   + [常用命令](cli/common-cli-commands.md)
   + [啟用記錄](cli/enable-logging.md)
   + [管理快取](cli/manage-cache.md)
   + [管理索引子](cli/manage-indexers.md)
   + [設定cron工作](cli/configure-cron-jobs.md)
   + [編譯程式碼](cli/code-compiler.md)
   + [操作模式](cli/set-mode.md)
   + [啟動訊息佇列消費者](cli/start-message-queues.md)
   + [URN熒光筆](cli/urn-highlighter.md)
   + [相依性報表](cli/dependency-reports.md)
   + [本地化](cli/localization.md)
   + 設定管理 {#configuration-management}
      + [設定值](cli/set-configuration-values.md)
      + [匯出設定](cli/export-configuration.md)
      + [匯入資料](cli/import-configuration.md)
   + 靜態檢視 {#static-view}
      + [部署策略](cli/static-view-file-strategy.md)
      + [部署靜態檢視檔案](cli/static-view-file-deployment.md)
   + [建立符號](cli/create-symlinks.md)
   + [執行單元測試](cli/unit-tests.md)
   + [轉換配置檔案](cli/convert-layout-files.md)
   + [產生資料以進行效能測試](cli/generate-data.md)
   + [執行支援公用程式（僅限Commerce）](cli/run-support-utilities.md)
+ 組態檔 {#files}
   + [用於部署的組態檔](reference/deployment-files.md)
   + [設定型別](reference/config-create-types.md)
   + [模組檔案](reference/module-files.md)
   + [模組輸出](reference/disable-module-output.md)
   + [config.php](reference/config-reference-configphp.md)
   + [env.php](reference/config-reference-envphp.md)
   + [gitignore](reference/config-reference-gitignore.md)
   + [system.xml](reference/config-reference-systemxml.md)
+ 設定路徑 {#paths}
   + [一般](reference/config-reference-general.md)
   + [B2B擴充功能](reference/config-reference-b2b.md)
   + [目錄](reference/config-reference-catalog.md)
   + [客戶](reference/config-reference-customers.md)
   + [付款方法](reference/config-reference-payment.md)
   + [銷售](reference/config-reference-sales.md)
   + [服務](reference/config-reference-services.md)
   + [敏感和系統專屬設定](reference/config-reference-sens.md)
   + [覆寫組態設定](reference/override-config-settings.md)
+ Cron工作 {#crons}
   + [Cron工作和群組](cron/custom-cron.md)
   + [自訂crons參考](cron/custom-cron-reference.md)
   + [設定自訂cron工作](cron/custom-cron-tutorial.md)
+ 記錄檔 {#logs}
   + [自訂記錄](logs/custom-logging.md)
   + [記錄器介面](logs/logger-interface.md)
   + [記錄資料庫活動](logs/database-activity.md)
   + [寫入自訂記錄檔](logs/custom-log-files.md)
+ 訊息佇列 {#message-queues}
   + [訊息佇列架構](queues/message-queue-framework.md)
   + [管理訊息佇列](queues/manage-message-queues.md)
   + [設定Amazon MQ](queues/aws-mq.md)
   + [消費者](queues/consumers.md)
+ 多個網站 {#multi-sites}
   + [多個網站和檢視](multi-sites/ms-overview.md)
   + [資料庫實體增量ID](multi-sites/change-increment-id.md)
   + [在管理員中設定](multi-sites/ms-admin.md)
   + [使用Nginx設定](multi-sites/ms-nginx.md)
   + [使用Apache設定](multi-sites/ms-apache.md)
+ 搜尋引擎 {#search}
   + [搜尋引擎概觀](search/overview-search.md)
   + [設定搜尋引擎](search/configure-search-engine.md)
   + [使用停用字詞篩選](search/search-stopwords.md)
+ 安全性 {#security}
   + [安全性總覽](security/overview.md)
   + [密碼雜湊](security/password-hashing.md)
   + [快取中毒](security/cache-poisoning.md)
   + [安全cron PHP](security/secure-cron-php.md)
   + [安全性TXT](security/security-txt.md)
   + [X-Frame-Options標頭](security/xframe-options.md)
+ 儲存 {#storage}
   + [資料庫分析工具](storage/db-profiler.md)
   + 遠端儲存 {#remote-storage}
      + [遠端儲存模組](remote-storage/remote-storage.md)
      + [AWS S3貯體](remote-storage/remote-storage-aws-s3.md)
      + [調整影像大小](remote-storage/remote-storage-image-resize.md)
      + [雲端的遠端儲存空間](remote-storage/cloud-support.md)
   + 工作階段儲存 {#session-storage}
      + [工作階段儲存位置](storage/sessions.md)
      + [memcached用於工作階段儲存](storage/memcached.md)
      + [memcached on CentOS](storage/memcache-centos.md)
      + [Ubuntu上的memcached](storage/memcache-ubuntu.md)
   + 分割資料庫 {#split-db}
      + [分割資料庫概觀](storage/multi-master.md)
      + [自動設定](storage/multi-master-masterdb.md)
      + [手動設定](storage/multi-master-manual.md)
      + [驗證分割資料庫](storage/multi-master-verify.md)
      + [資料庫復寫](storage/multi-master-replication.md)
      + [還原為單一資料庫](storage/revert-split-database.md)
+ [返回作業指南](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)