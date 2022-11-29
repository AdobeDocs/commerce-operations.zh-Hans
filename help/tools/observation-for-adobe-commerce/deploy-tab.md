---
title: “ [!UICONTROL Deploy] 选项卡”
description: 了解 [!UICONTROL Deploy] 选项卡 [!DNL Observation for Adobe Commerce].
source-git-commit: 27ebd472dc4e81e58b36bf5fac529461beae4be1
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# 的 [!UICONTROL Deploy] 选项卡

此选项卡旨在快速隔离问题和导致部署问题的原因。

## [!UICONTROL Deploy log Deployment Troubleshooter]

![部署日志部署疑难解答](../../assets/tools/observation-for-adobe-commerce/deploy-tab-1.jpg)

的 **[!UICONTROL Deploy log Deployment Troubleshooter]** 框架显示在选定时间范围内发生的部署日志事件计数。 其目的在于提供部署活动的概览，并根据计数确定部署的复杂性。 记录的消息越多，部署通常就越复杂。

## [!UICONTROL Deploy State]

![部署状态](../../assets/tools/observation-for-adobe-commerce/deploy-tab-2.jpg)

的 **[!UICONTROL Deploy State]** 框架显示在选定的时间范围内发生的部署事件。 此帧的解析器正在查找以下特定信号：

* &#39;`%NOTICE: Starting generate command%`&#39;)作为&#39;`start_gen`&#39;
* &#39;`%git apply /app/vendor/magento/ece-tools/patches%`&#39;)作为&#39;`apply_patches`&#39;
* &#39;`%Set flag: .static_content_deploy%`&#39;)作为&#39;`SCD`&#39;
* &#39;`%NOTICE: Generate command completed%`&#39;)作为&#39;`gen_compl`&#39;
* &#39;`%NOTICE: Starting deploy.%`&#39;)作为&#39;`start_deploy`&#39;
* &#39;`%NOTICE: Deployment completed%`&#39;)作为&#39;`deploy_compl`&#39;
* &#39;`%NOTICE: Starting post-deploy.%`&#39;)作为&#39;`start_pdeploy`&#39;
* &#39;`%NOTICE: Post-deploy is complete%`&#39;)作为&#39;`pdeploy`&#39;
* &#39;`%deploy-complete%`&#39;)作为&#39;`cl_deploy_compl`&#39;

## [!UICONTROL Deploy Log Detail]

![部署日志详细信息](../../assets/tools/observation-for-adobe-commerce/deploy-tab-3.jpg)

的 **[!UICONTROL Deploy Log Detail]** 框架显示在选定时间范围内发生的部署日志消息摘要详细信息。 正在解析部署日志中的以下字符串：

* &#39;`%NOTICE: Starting deploy.%`&#39;)作为&#39;`start_dply`&#39;
* &#39;`%INFO: Starting scenario(s): scenario/deploy.xml%`&#39;)作为&#39;`start_scenario`&#39;
* &#39;`%NOTICE: Starting pre-deploy%`&#39;)作为&#39;`strt_predply`&#39;
* &#39;`%INFO: Restoring patch log file%`&#39;)作为&#39;`rstr_ptch_log`&#39;
* &#39;`%INFO: Updating cache configuration.%`&#39;)作为&#39;`updt_cach_config`&#39;
* &#39;`%INFO: Set Redis slave connection%`&#39;)作为&#39;`redis_sec_conn_set`&#39;
* &#39;`%INFO: Static content deployment was performed during build hook, cleaning old content%`&#39;)作为&#39;`scd_build_hk`&#39;
* &#39;`%INFO: Clearing pub/static%`&#39;)作为&#39;`clr_pub_static`&#39;
* &#39;`%NFO: Clearing redis cache:%`&#39;)作为&#39;`clr_redis_cach`&#39;
* &#39;`%INFO: Clearing var/cache directory%`&#39;)作为&#39;`clr_var_cach`&#39;
* &#39;`%NOTICE: Enabling Maintenance mode%`&#39;)作为&#39;`enable_maint_mode`&#39;
* &#39;`%INFO: Disable cron%`&#39;)作为&#39;`disable_cron`&#39;
* &#39;`%INFO: Trying to kill running cron jobs and consumers processes%`&#39;)作为&#39;`kill_cron_try`&#39;
* &#39;`%INFO: Running Adobe Commerce cron and consumers processes were not found.%`&#39;)作为&#39;`no_cron_fnd`&#39;
* &#39;`%NOTICE: Validating configuration%`&#39;)作为&#39;`validate_config`&#39;
* &#39;`%The following admin data is required to create an admin user during initial installation%`&#39;)作为&#39;`no_admin`&#39;
* &#39;`%recommended PHP version satisfying the constraint%`&#39;)作为&#39;`php_ver_constraint`&#39;
* &#39;`%WARNING: Fix configuration with given suggestions:%`&#39;)作为&#39;`fix_config_sugg`&#39;
* &#39;`%WARNING: [2003] The directory nesting level value for error reporting has not been configured.%`&#39;)作为&#39;`nest_err_reporting`&#39;
* &#39;`%NOTICE: End of validation%`&#39;)作为&#39;`end_validation`&#39;
* &#39;`%NOTICE: Starting update.%`&#39;)作为&#39;`start_update`&#39;
* &#39;`%INFO: Updating env.php.%`&#39;)作为&#39;`update_php_env`&#39;
* &#39;`%INFO: Updating env.php DB connection configuration.%`&#39;)作为&#39;`update_php_env_db`&#39;
* &#39;`%INFO: Updating env.php AMQP configuration%`&#39;)作为&#39;`update_php_env_amqp`&#39;
* &#39;`%INFO: Set search engine to: elasticsearch7%`&#39;)作为&#39;`set_elastic7`&#39;
* &#39;`%elasticsearch 6.5.4 has passed EOL%`&#39;)作为&#39;`elastic_ver_EOL`&#39;
* &#39;`%INFO: Set search engine to: elasticsearch6%`&#39;)作为&#39;`set_elastic6`&#39;
* &#39;`%INFO: Updating secure and unsecure URLs%`&#39;)作为&#39;`update_urls`&#39;
* &#39;`%INFO: Running setup upgrade.%`&#39;)作为&#39;`setup_upgrade_run`&#39;
* &#39;`%INFO: Post-deploy hook enabled. Cron enabling, cache cleaning, and pre-warming operations are postponed%`&#39;)作为&#39;`post_hook_enabled`&#39;
* &#39;`%NOTICE: Maintenance mode is disabled.%`&#39;)作为&#39;`maint_mode_disabled`&#39;
* &#39;`%INFO: Scenario(s) finished%`&#39;)作为&#39;`scenario_finished`&#39;
* &#39;`%WARNING: Command maintenance:enable finished with an error. Creating a maintenance flag file%`&#39;)作为&#39;`enable_maintenance_fail`&#39;
* &#39;`%MySQL server has gone away%`&#39;)作为&#39;`MySQL_has_gone_away`&#39;

## [!UICONTROL Post Deploy Log Detail]

![部署日志后详细信息](../../assets/tools/observation-for-adobe-commerce/deploy-tab-4.jpg)

的 **[!UICONTROL Post Deploy Log Detail]** 框架显示在选定时间范围内发生的部署后日志详细信息。 此框架重点介绍包含以下字符串的特定日志消息：

* &#39;`%Disabled maintenance mode%`&#39;)作为&#39;`disabled_maint_mode`&#39;
* &#39;`%INFO: Starting scenario(s): scenario/post-deploy.xml%`&#39;)作为&#39;`start_pstdply_scenario`&#39;
* &#39;`%NOTICE: Validating configuration%`&#39;)作为&#39;`val_config`&#39;
* &#39;`%NOTICE: End of validation%`&#39;)作为&#39;`end_val_config`&#39;
* &#39;`%INFO: Enable cron%`&#39;)作为&#39;`cron_enabled`&#39;
* &#39;`%INFO: Create backup of important files.%`&#39;)作为&#39;`file_backup`&#39;
* &#39;`%INFO: Successfully created backup%`&#39;)作为&#39;`file_backup_success`&#39;
* &#39;`%INFO: Starting page warming up%`&#39;)作为&#39;`pg_warmup_start`&#39;
* &#39;`%INFO: Warmed up page:%`&#39;)作为&#39;`warmed_up_pg`&#39;
* &#39;`%ERROR: Warming up failed:%`&#39;)作为&#39;`warm_up_pg_err`&#39;
* &#39;`%INFO: Scenario(s) finished%`&#39;)作为&#39;`scenario_finished`&#39;

## [!UICONTROL Cloud Log Detail]

![云日志详细信息](../../assets/tools/observation-for-adobe-commerce/deploy-tab-5.jpg)

的 **[!UICONTROL Cloud Log Detail]** 框架显示在选定时间范围内发生的云日志详细信息。 将解析以下字符串，并使用下面的“AS”标签返回：

* &#39;`%DEBUG: /bin/bash -c "set -o pipefail; php ./bin/magento setup:upgrade%`&#39;)作为&#39;`start_update`&#39;
* &#39;`%Schema creation/updates:%`&#39;)作为&#39;`schema_updates`&#39;
* &#39;`%Nothing to import.%`&#39;)作为&#39;`mod_import_finish`&#39;
* &#39;`%NOTICE: End of update.%`&#39;)作为&#39;`update_finished`&#39;
* &#39;`%DEBUG: Running step: deploy-static-content%`&#39;)作为&#39;`scd_run`&#39;
* &#39;`%NOTICE: Skipping static content deploy. SCD on demand is enabled.%`&#39;)作为&#39;`scd_ondemand`&#39;
* &#39;`%INFO: Clearing%`&#39;)作为&#39;`clr_dirs`&#39;
* &#39;`%DEBUG: Step "deploy-static-content" finished%`&#39;)作为&#39;`scd_finished`&#39;
* &#39;`%NOTICE: Skipping static content compression. SCD on demand is enabled.%`&#39;)作为&#39;`scd_compression_run`&#39;
* &#39;`%INFO: Clearing var/cache directory%`&#39;)作为&#39;`clr_var_cach`&#39;
* &#39;`%DEBUG: Step "compress-static-content" finished%`&#39;)作为&#39;`scd_compression_finished`&#39;
* &#39;`%DEBUG: Running step: deploy-complete%`&#39;)作为&#39;`deploy_finished`&#39;
* &#39;`%INFO: Post-deploy hook enabled. Cron enabling, cache cleaning, and pre-warming operations are postponed to post-deploy stage.%`&#39;)作为&#39;`Post_deploy_hook_enabled`&#39;
* &#39;`%NOTICE: Maintenance mode is disabled.%`&#39;)作为&#39;`maint_mode_disabled`&#39;
* &#39;`%INFO: Scenario(s) finished%`&#39;)作为&#39;`scenario_finished`&#39;
* &#39;`%post-deploy.xml%`&#39;)作为&#39;`post_deploy_start`&#39;
* &#39;`%NOTICE: Validating configuration%`&#39;)作为&#39;`validate_config`&#39;
* &#39;`%WARNING: [2003] The directory nesting level value for error reporting has not been configured.%`&#39;)作为&#39;`nest_err_reporting`&#39;
* &#39;`%NOTICE: End of validation%`&#39;)作为&#39;`end_validation`&#39;
* &#39;`%INFO: Enable cron%`&#39;)作为&#39;`enable_cron`&#39;
* &#39;`%INFO: Create backup of important files%`&#39;)作为&#39;`create_backup`&#39;
* &#39;`%DEBUG: Step "backup" finished%`&#39;)作为&#39;`backup_finished`&#39;
* &#39;`%INFO: Starting page warming up%`&#39;)作为&#39;`warmup_start`&#39;
* &#39;`%ERROR: Warming up failed:%`&#39;)作为&#39;`warm_up_fail`&#39;
* &#39;`%DEBUG: Step "warm-up" finished%`&#39;)作为&#39;`warmup_finished`&#39;
* &#39;`%DEBUG: Step "time-to-first-byte" finished%`&#39;)作为&#39;`ttfb_finished`&#39;
* &#39;`%INFO: Scenario(s) finished%`&#39;)作为&#39;`post_deploy_finished`&#39;
* &#39;`%DEBUG: Running step: pre-build%`&#39;)作为&#39;`run_pre-build`&#39;
* &#39;`%DEBUG: Flag .static_content_deploy has already been deleted%`&#39;)作为&#39;`scd_flag_del`&#39;
* &#39;`%DEBUG: Step "pre-build" finished%`&#39;)作为&#39;`pre-build_completed`&#39;
* &#39;`%NOTICE: Applying patches%`&#39;)作为&#39;`apply_patches`&#39;
* &#39;`%has been applied%`&#39;)作为&#39;`patches_applied`&#39;
* &#39;`%DEBUG: Step "apply-patches" finished%`&#39;)作为&#39;`apply_patches_complete`&#39;
* &#39;`%Deploy using quick strategy%`&#39;)作为&#39;`quick_strategy_deploy`&#39;
* &#39;`%NOTICE: Running DI compilation%`&#39;)作为&#39;`di_compliation_start`&#39;
* &#39;`%NOTICE: End of running DI compilation%`&#39;)作为&#39;`di_compliation_finished`&#39;
* &#39;`%NOTICE: Generating fresh static content%`&#39;)作为&#39;`gen_frsh_static_content`&#39;
* &#39;`%magento setup:static-content:deploy%`&#39;)作为&#39;`scd_executing`&#39;
* &#39;`%NOTICE: End of generating fresh static content%`&#39;)作为&#39;`gen_frsh_static_cont_finished`&#39;
* &#39;`%INFO: Starting scenario(s): scenario/build/transfer.xml%`&#39;)作为&#39;`start_transferxml`&#39;
* &#39;`%INFO: Trying to kill running cron jobs%`&#39;)作为&#39;`kill_crons`&#39;
* &#39;`%INFO: Clearing redis cache:%`&#39;)作为&#39;`clear_redis_cache`&#39;
* &#39;`%INFO: Checking if db exists and has tables%`&#39;)作为&#39;`db_check`&#39;
* &#39;`%WARNING: [2010] Elasticsearch service is installed at infrastructure layer, but is not used as a search engine.%`)作为“`es_not_used`&#39;
* &#39;`%NOTICE: Starting update.%`&#39;)作为&#39;`starting_update`&#39;
* &#39;`%INFO: Set search engine to: mysql%`&#39;)作为&#39;`mysql_search`&#39;
* &#39;`%SQLSTATE[HY000] [2006] MySQL server has gone away%`&#39;)作为&#39;`mysql_gone`&#39;

## [!UICONTROL Count of modules imported during deploy]

![部署期间导入的模块计数](../../assets/tools/observation-for-adobe-commerce/deploy-tab-6.jpg)

的 **[!UICONTROL Count of modules imported during deploy]** 框架显示在选定时间范围内部署期间导入的模块数。

## [!UICONTROL Deployed module list]

![已部署的模块列表](../../assets/tools/observation-for-adobe-commerce/deploy-tab-7.jpg)

的 **[!UICONTROL Deployed module list]** 框架显示选定时间范围内已部署的模块。

