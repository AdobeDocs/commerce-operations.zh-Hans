---
title: 此 [!UICONTROL Deploy] 选项卡
description: 了解 [!UICONTROL Deploy] 选项卡/ [!DNL Observation for Adobe Commerce].
exl-id: 3e33f7b0-7a40-4598-ae2e-436118e8d99a
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# 此 [!UICONTROL Deploy] 选项卡

此选项卡用于尝试快速隔离部署问题的问题和原因。

## [!UICONTROL Deploy log Deployment Troubleshooter]

![部署日志部署疑难解答程序](../../assets/tools/observation-for-adobe-commerce/deploy-tab-1.jpg)

此 **[!UICONTROL Deploy log Deployment Troubleshooter]** 框架显示选定时间范围内发生的部署日志事件计数。 其目的是提供部署活动的概览，并按计数确定部署的复杂性。 记录的消息越多，部署通常就越复杂。

## [!UICONTROL Deploy State]

![部署状态](../../assets/tools/observation-for-adobe-commerce/deploy-tab-2.jpg)

此 **[!UICONTROL Deploy State]** 此框架显示在所选时间范围内发生的部署事件。 此帧的解析器正在查找以下特定信号：

* ’`%NOTICE: Starting generate command%`&#39;)作为&#39;`start_gen`’
* ’`%git apply /app/vendor/magento/ece-tools/patches%`&#39;)作为&#39;`apply_patches`’
* ’`%Set flag: .static_content_deploy%`&#39;)作为&#39;`SCD`’
* ’`%NOTICE: Generate command completed%`&#39;)作为&#39;`gen_compl`’
* ’`%NOTICE: Starting deploy.%`&#39;)作为&#39;`start_deploy`’
* ’`%NOTICE: Deployment completed%`&#39;)作为&#39;`deploy_compl`’
* ’`%NOTICE: Starting post-deploy.%`&#39;)作为&#39;`start_pdeploy`’
* ’`%NOTICE: Post-deploy is complete%`&#39;)作为&#39;`pdeploy`’
* ’`%deploy-complete%`&#39;)作为&#39;`cl_deploy_compl`’

## [!UICONTROL Deploy Log Detail]

![部署日志详细信息](../../assets/tools/observation-for-adobe-commerce/deploy-tab-3.jpg)

此 **[!UICONTROL Deploy Log Detail]** 框架显示所选时间范围内发生的部署日志消息摘要详细信息。 正在解析框架以查找部署日志中的以下字符串：

* ’`%NOTICE: Starting deploy.%`&#39;)作为&#39;`start_dply`’
* ’`%INFO: Starting scenario(s): scenario/deploy.xml%`&#39;)作为&#39;`start_scenario`’
* ’`%NOTICE: Starting pre-deploy%`&#39;)作为&#39;`strt_predply`’
* ’`%INFO: Restoring patch log file%`&#39;)作为&#39;`rstr_ptch_log`’
* ’`%INFO: Updating cache configuration.%`&#39;)作为&#39;`updt_cach_config`’
* ’`%INFO: Set Redis slave connection%`&#39;)作为&#39;`redis_sec_conn_set`’
* ’`%INFO: Static content deployment was performed during build hook, cleaning old content%`&#39;)作为&#39;`scd_build_hk`’
* ’`%INFO: Clearing pub/static%`&#39;)作为&#39;`clr_pub_static`’
* ’`%NFO: Clearing redis cache:%`&#39;)作为&#39;`clr_redis_cach`’
* ’`%INFO: Clearing var/cache directory%`&#39;)作为&#39;`clr_var_cach`’
* ’`%NOTICE: Enabling Maintenance mode%`&#39;)作为&#39;`enable_maint_mode`’
* ’`%INFO: Disable cron%`&#39;)作为&#39;`disable_cron`’
* ’`%INFO: Trying to kill running cron jobs and consumers processes%`&#39;)作为&#39;`kill_cron_try`’
* ’`%INFO: Running Adobe Commerce cron and consumers processes were not found.%`&#39;)作为&#39;`no_cron_fnd`’
* ’`%NOTICE: Validating configuration%`&#39;)作为&#39;`validate_config`’
* ’`%The following admin data is required to create an admin user during initial installation%`&#39;)作为&#39;`no_admin`’
* ’`%recommended PHP version satisfying the constraint%`&#39;)作为&#39;`php_ver_constraint`’
* ’`%WARNING: Fix configuration with given suggestions:%`&#39;)作为&#39;`fix_config_sugg`’
* ’`%WARNING: [2003] The directory nesting level value for error reporting has not been configured.%`&#39;)作为&#39;`nest_err_reporting`’
* ’`%NOTICE: End of validation%`&#39;)作为&#39;`end_validation`’
* ’`%NOTICE: Starting update.%`&#39;)作为&#39;`start_update`’
* ’`%INFO: Updating env.php.%`&#39;)作为&#39;`update_php_env`’
* ’`%INFO: Updating env.php DB connection configuration.%`&#39;)作为&#39;`update_php_env_db`’
* ’`%INFO: Updating env.php AMQP configuration%`&#39;)作为&#39;`update_php_env_amqp`’
* ’`%INFO: Set search engine to: elasticsearch7%`&#39;)作为&#39;`set_elastic7`’
* ’`%elasticsearch 6.5.4 has passed EOL%`&#39;)作为&#39;`elastic_ver_EOL`’
* ’`%INFO: Set search engine to: elasticsearch6%`&#39;)作为&#39;`set_elastic6`’
* ’`%INFO: Updating secure and unsecure URLs%`&#39;)作为&#39;`update_urls`’
* ’`%INFO: Running setup upgrade.%`&#39;)作为&#39;`setup_upgrade_run`’
* ’`%INFO: Post-deploy hook enabled. Cron enabling, cache cleaning, and pre-warming operations are postponed%`&#39;)作为&#39;`post_hook_enabled`’
* ’`%NOTICE: Maintenance mode is disabled.%`&#39;)作为&#39;`maint_mode_disabled`’
* ’`%INFO: Scenario(s) finished%`&#39;)作为&#39;`scenario_finished`’
* ’`%WARNING: Command maintenance:enable finished with an error. Creating a maintenance flag file%`&#39;)作为&#39;`enable_maintenance_fail`’
* ’`%MySQL server has gone away%`&#39;)作为&#39;`MySQL_has_gone_away`’

## [!UICONTROL Post Deploy Log Detail]

![部署后日志详细信息](../../assets/tools/observation-for-adobe-commerce/deploy-tab-4.jpg)

此 **[!UICONTROL Post Deploy Log Detail]** 框架显示所选时间范围内发生的部署后日志详细信息。 此框架侧重于包含以下字符串的特定日志消息：

* ’`%Disabled maintenance mode%`&#39;)作为&#39;`disabled_maint_mode`’
* ’`%INFO: Starting scenario(s): scenario/post-deploy.xml%`&#39;)作为&#39;`start_pstdply_scenario`’
* ’`%NOTICE: Validating configuration%`&#39;)作为&#39;`val_config`’
* ’`%NOTICE: End of validation%`&#39;)作为&#39;`end_val_config`’
* ’`%INFO: Enable cron%`&#39;)作为&#39;`cron_enabled`’
* ’`%INFO: Create backup of important files.%`&#39;)作为&#39;`file_backup`’
* ’`%INFO: Successfully created backup%`&#39;)作为&#39;`file_backup_success`’
* ’`%INFO: Starting page warming up%`&#39;)作为&#39;`pg_warmup_start`’
* ’`%INFO: Warmed up page:%`&#39;)作为&#39;`warmed_up_pg`’
* ’`%ERROR: Warming up failed:%`&#39;)作为&#39;`warm_up_pg_err`’
* ’`%INFO: Scenario(s) finished%`&#39;)作为&#39;`scenario_finished`’

## [!UICONTROL Cloud Log Detail]

![云日志详细信息](../../assets/tools/observation-for-adobe-commerce/deploy-tab-5.jpg)

此 **[!UICONTROL Cloud Log Detail]** 此框架显示所选时间范围内发生的云日志详细信息。 以下字符串经过解析后返回，并带有下面的“AS”标签：

* ’`%DEBUG: /bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade%`&#39;)作为&#39;`start_update`’
* ’`%Schema creation/updates:%`&#39;)作为&#39;`schema_updates`’
* ’`%Nothing to import.%`&#39;)作为&#39;`mod_import_finish`’
* ’`%NOTICE: End of update.%`&#39;)作为&#39;`update_finished`’
* ’`%DEBUG: Running step: deploy-static-content%`&#39;)作为&#39;`scd_run`’
* ’`%NOTICE: Skipping static content deploy. SCD on demand is enabled.%`&#39;)作为&#39;`scd_ondemand`’
* ’`%INFO: Clearing%`&#39;)作为&#39;`clr_dirs`’
* ’`%DEBUG: Step "deploy-static-content" finished%`&#39;)作为&#39;`scd_finished`’
* ’`%NOTICE: Skipping static content compression. SCD on demand is enabled.%`&#39;)作为&#39;`scd_compression_run`’
* ’`%INFO: Clearing var/cache directory%`&#39;)作为&#39;`clr_var_cach`’
* ’`%DEBUG: Step "compress-static-content" finished%`&#39;)作为&#39;`scd_compression_finished`’
* ’`%DEBUG: Running step: deploy-complete%`&#39;)作为&#39;`deploy_finished`’
* ’`%INFO: Post-deploy hook enabled. Cron enabling, cache cleaning, and pre-warming operations are postponed to post-deploy stage.%`&#39;)作为&#39;`Post_deploy_hook_enabled`’
* ’`%NOTICE: Maintenance mode is disabled.%`&#39;)作为&#39;`maint_mode_disabled`’
* ’`%INFO: Scenario(s) finished%`&#39;)作为&#39;`scenario_finished`’
* ’`%post-deploy.xml%`&#39;)作为&#39;`post_deploy_start`’
* ’`%NOTICE: Validating configuration%`&#39;)作为&#39;`validate_config`’
* ’`%WARNING: [2003] The directory nesting level value for error reporting has not been configured.%`&#39;)作为&#39;`nest_err_reporting`’
* ’`%NOTICE: End of validation%`&#39;)作为&#39;`end_validation`’
* ’`%INFO: Enable cron%`&#39;)作为&#39;`enable_cron`’
* ’`%INFO: Create backup of important files%`&#39;)作为&#39;`create_backup`’
* ’`%DEBUG: Step "backup" finished%`&#39;)作为&#39;`backup_finished`’
* ’`%INFO: Starting page warming up%`&#39;)作为&#39;`warmup_start`’
* ’`%ERROR: Warming up failed:%`&#39;)作为&#39;`warm_up_fail`’
* ’`%DEBUG: Step "warm-up" finished%`&#39;)作为&#39;`warmup_finished`’
* ’`%DEBUG: Step "time-to-first-byte" finished%`&#39;)作为&#39;`ttfb_finished`’
* ’`%INFO: Scenario(s) finished%`&#39;)作为&#39;`post_deploy_finished`’
* ’`%DEBUG: Running step: pre-build%`&#39;)作为&#39;`run_pre-build`’
* ’`%DEBUG: Flag .static_content_deploy has already been deleted%`&#39;)作为&#39;`scd_flag_del`’
* ’`%DEBUG: Step "pre-build" finished%`&#39;)作为&#39;`pre-build_completed`’
* ’`%NOTICE: Applying patches%`&#39;)作为&#39;`apply_patches`’
* ’`%has been applied%`&#39;)作为&#39;`patches_applied`’
* ’`%DEBUG: Step "apply-patches" finished%`&#39;)作为&#39;`apply_patches_complete`’
* ’`%Deploy using quick strategy%`&#39;)作为&#39;`quick_strategy_deploy`’
* ’`%NOTICE: Running DI compilation%`&#39;)作为&#39;`di_compliation_start`’
* ’`%NOTICE: End of running DI compilation%`&#39;)作为&#39;`di_compliation_finished`’
* ’`%NOTICE: Generating fresh static content%`&#39;)作为&#39;`gen_frsh_static_content`’
* ’`%magento setup:static-content:deploy%`&#39;)作为&#39;`scd_executing`’
* ’`%NOTICE: End of generating fresh static content%`&#39;)作为&#39;`gen_frsh_static_cont_finished`’
* ’`%INFO: Starting scenario(s): scenario/build/transfer.xml%`&#39;)作为&#39;`start_transferxml`’
* ’`%INFO: Trying to kill running cron jobs%`&#39;)作为&#39;`kill_crons`’
* ’`%INFO: Clearing redis cache:%`&#39;)作为&#39;`clear_redis_cache`’
* ’`%INFO: Checking if db exists and has tables%`&#39;)作为&#39;`db_check`’
* ’`%WARNING: [2010] Elasticsearch service is installed at infrastructure layer, but is not used as a search engine.%`)作为&#39;`es_not_used`’
* ’`%NOTICE: Starting update.%`&#39;)作为&#39;`starting_update`’
* ’`%INFO: Set search engine to: mysql%`&#39;)作为&#39;`mysql_search`’
* ’`%SQLSTATE[HY000] [2006] MySQL server has gone away%`&#39;)作为&#39;`mysql_gone`’

## [!UICONTROL Count of modules imported during deploy]

![部署期间导入的模块计数](../../assets/tools/observation-for-adobe-commerce/deploy-tab-6.jpg)

此 **[!UICONTROL Count of modules imported during deploy]** 框架显示在选定时间范围内部署期间导入的模块数。

## [!UICONTROL Deployed module list]

![已部署模块列表](../../assets/tools/observation-for-adobe-commerce/deploy-tab-7.jpg)

此 **[!UICONTROL Deployed module list]** 该帧显示了所选时间范围内的已部署模块。
