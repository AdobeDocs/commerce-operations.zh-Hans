---
user-guide-title: 配置指南
user-guide-description: 配置Adobe Commerce或Magento Open Source应用程序功能和服务。
source-git-commit: b872a61f74818990833ba6b48e061fa1ca69b7cb
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---


# 配置指南 {#configuration-guide}

+ [概述](overview.md)
+ 常规设置 {#setup}
   + [应用程序初始化和引导](bootstrap/initialization.md)
   + [应用模式](bootstrap/application-modes.md)
   + [Bootstrap参数](bootstrap/set-parameters.md)
   + [分析](bootstrap/mage-profiler.md)
   + [基目录路径](bootstrap/mage-directory.md)
+ 部署 {#deployment}
   + [部署概述](deployment/overview.md)
   + [单机部署](deployment/single-machine.md)
   + [管道部署](deployment/technical-details.md)
   + [先决条件](deployment/prerequisites.md)
   + [开发系统设置](deployment/development-system.md)
   + [构建系统设置](deployment/build-system.md)
   + [生产系统设置](deployment/production-system.md)
   + [文件系统访问权限](deployment/file-system-permissions.md)
   + 示例 {#examples}
      + [使用共享配置](deployment/example-shared-configuration.md)
      + [使用CLI命令](deployment/example-using-cli.md)
      + [使用环境变量](deployment/example-environment-variables.md)
+ 缓存 {#cache}
   + [缓存概述](cache/caching-overview.md)
   + [缓存类型](cache/cache-types.md)
   + [缓存选项](cache/cache-options.md)
   + [二级高速缓存](cache/level-two-cache.md)
   + 雷迪斯 {#redis}
      + [配置Redi](cache/config-redis.md)
      + [默认缓存使用Redis](cache/redis-pg-cache.md)
      + [将Redis用于会话存储](cache/redis-session.md)
   + 清漆 {#varnish}
      + [清漆概述](cache/config-varnish.md)
      + [安装清漆](cache/config-varnish-install.md)
   + [Web服务器](cache/config-varnish-server.md)
   + [配置商务应用程序](cache/configure-varnish-commerce.md)
   + [高级清漆配置](cache/config-varnish-advanced.md)
   + [缓存清除](cache/use-varnish-cache.md)
   + [缓存清除多个清漆实例](cache/use-multiple-varnish-cache.md)
   + [验证清漆配置](cache/config-varnish-final.md)
   + [清漆ESI块](cache/use-varnish-esi.md)
   + [静态内容缓存](cache/static-content-signing.md)
+ 命令行 {#cli}
   + [命令行工具](cli/config-cli.md)
   + [常用命令](cli/common-cli-commands.md)
   + [启用日志记录](cli/enable-logging.md)
   + [管理缓存](cli/manage-cache.md)
   + [管理索引器](cli/manage-indexers.md)
   + [配置cron作业](cli/configure-cron-jobs.md)
   + [编译代码](cli/code-compiler.md)
   + [操作模式](cli/set-mode.md)
   + [启动消息队列使用者](cli/start-message-queues.md)
   + [URN高亮](cli/urn-highlighter.md)
   + [依赖关系报表](cli/dependency-reports.md)
   + [本地化](cli/localization.md)
   + 配置管理 {#configuration-management}
      + [设置值](cli/set-configuration-values.md)
      + [导出设置](cli/export-configuration.md)
      + [导入数据](cli/import-configuration.md)
   + 静态视图 {#static-view}
      + [部署策略](cli/static-view-file-strategy.md)
      + [部署静态视图文件](cli/static-view-file-deployment.md)
   + [创建符号链接](cli/create-symlinks.md)
   + [运行单元测试](cli/unit-tests.md)
   + [转换布局文件](cli/convert-layout-files.md)
   + [生成数据以进行性能测试](cli/generate-data.md)
   + [运行支持实用程序（仅限商务）](cli/run-support-utilities.md)
+ 配置文件 {#files}
   + [部署的配置文件](reference/deployment-files.md)
   + [配置类型](reference/config-create-types.md)
   + [模块文件](reference/module-files.md)
   + [模块输出](reference/disable-module-output.md)
   + [config.php](reference/config-reference-configphp.md)
   + [env.php](reference/config-reference-envphp.md)
   + [吉蒂尼奥雷](reference/config-reference-gitignore.md)
   + [system.xml](reference/config-reference-systemxml.md)
+ 配置路径 {#paths}
   + [常规](reference/config-reference-general.md)
   + [B2B扩展](reference/config-reference-b2b.md)
   + [目录](reference/config-reference-catalog.md)
   + [客户](reference/config-reference-customers.md)
   + [付款方法](reference/config-reference-payment.md)
   + [销售](reference/config-reference-sales.md)
   + [服务](reference/config-reference-services.md)
   + [敏感和系统特定的设置](reference/config-reference-sens.md)
   + [覆盖配置设置](reference/override-config-settings.md)
+ Cron作业 {#crons}
   + [Cron作业和组](cron/custom-cron.md)
   + [自定义转码参考](cron/custom-cron-reference.md)
   + [配置自定义cron作业](cron/custom-cron-tutorial.md)
+ 日志 {#logs}
   + [自定义日志](logs/custom-logging.md)
   + [记录器界面](logs/logger-interface.md)
   + [日志数据库活动](logs/database-activity.md)
   + [写入自定义日志文件](logs/custom-log-files.md)
+ 消息队列 {#message-queues}
   + [消息队列框架](queues/message-queue-framework.md)
   + [管理消息队列](queues/manage-message-queues.md)
   + [设置Amazon MQ](queues/aws-mq.md)
+ 多个网站 {#multi-sites}
   + [多个网站和视图](multi-sites/ms-overview.md)
   + [数据库实体增量ID](multi-sites/change-increment-id.md)
   + [在管理员中设置](multi-sites/ms-admin.md)
   + [使用Nginx进行设置](multi-sites/ms-nginx.md)
   + [使用Apache设置](multi-sites/ms-apache.md)
+ 搜索引擎 {#search}
   + [搜索引擎概述](search/overview-search.md)
   + [配置搜索引擎](search/configure-search-engine.md)
   + [包含秒词的过滤器](search/search-stopwords.md)
+ 安全性 {#security}
   + [安全概述](security/overview.md)
   + [密码哈希处理](security/password-hashing.md)
   + [缓存中毒](security/cache-poisoning.md)
   + [安全CRON PHP](security/secure-cron-php.md)
   + [安全TXT](security/security-txt.md)
   + [X-Frame-Options标题](security/xframe-options.md)
+ 存储 {#storage}
   + [数据库探查器](storage/db-profiler.md)
   + 远程存储 {#remote-storage}
      + [远程存储模块](remote-storage/remote-storage.md)
      + [AWS S3存储段](remote-storage/remote-storage-aws-s3.md)
      + [调整图像大小](remote-storage/remote-storage-image-resize.md)
      + [云的远程存储](remote-storage/cloud-support.md)
   + 会话存储 {#session-storage}
      + [会话存储位置](storage/sessions.md)
      + [会话存储的memcached](storage/memcached.md)
      + [CentOS上的memcached](storage/memcache-centos.md)
      + [梅姆卡德在乌本图](storage/memcache-ubuntu.md)
   + 拆分数据库 {#split-db}
      + [拆分数据库概述](storage/multi-master.md)
      + [自动配置](storage/multi-master-masterdb.md)
      + [手动配置](storage/multi-master-manual.md)
      + [验证拆分数据库](storage/multi-master-verify.md)
      + [数据库复制](storage/multi-master-replication.md)
      + [还原到单个数据库](storage/revert-split-database.md)
