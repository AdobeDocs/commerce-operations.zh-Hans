---
user-guide-title: 安装指南
user-guide-description: 了解如何安装Adobe Commerce和Magento Open Source以进行内部部署。
source-git-commit: 949ef8d2036ceeef3cc892a5063ddecc2586a6a9
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# 安装指南 {#installation-guide}

- [概述](overview.md)
- [系统要求](system-requirements.md)
- 先决条件 {#prerequisites}
   - [概述](prerequisites/overview.md)
   - 文件系统 {#file-system}
      - [概述](prerequisites/file-system/overview.md)
      - [配置权限](prerequisites/file-system/configure-permissions.md)
   - Web服务器 {#web-server}
      - [Nginx](prerequisites/web-server/nginx.md)
      - [Apache](prerequisites/web-server/apache.md)
   - 数据库服务器 {#database-server}
      - [MySQL](prerequisites/database/mysql.md)
      - [远程连接](prerequisites/database/mysql-remote.md)
   - 搜索引擎 {#search-engine}
      - [概述](prerequisites/search-engine/overview.md)
      - [AWS OpenSearch](prerequisites/search-engine/aws-opensearch.md)
      - [配置Nginx](prerequisites/search-engine/configure-nginx.md)
      - [配置Apache](prerequisites/search-engine/configure-apache.md)
   - [PHP](prerequisites/php-settings.md)
   - [消息代理](prerequisites/rabbitmq.md)
   - [安全性](prerequisites/security.md)
   - [身份验证密钥](prerequisites/authentication-keys.md)
   - [Adobe Commerce](prerequisites/commerce.md)
   - [可选软件](prerequisites/optional-software.md)
- [快速启动安装](composer.md)
- [高级安装](advanced.md)
- 安装后步骤 {#next-steps}
   - [验证安装](next-steps/verify.md)
   - [配置应用程序](next-steps/configuration.md)
   - [设置变调（可选）](next-steps/set-umask.md)
   - 安装示例数据（可选） {#sample-data}
      - [概述](sample-data/overview.md)
      - [下载编辑器包](sample-data/composer-packages.md)
      - [克隆Git存储库](sample-data/git-repositories.md)
      - [删除或更新模块](sample-data/remove-or-update.md)
- 教程 {#tutorials}
   - [备份和回滚文件系统、介质和数据库](tutorials/backup.md)
   - [检查数据库状态](tutorials/database-status.md)
   - [配置消息使用者行为](tutorials/message-consumers.md)
   - [配置锁定提供程序](tutorials/lock-provider.md)
   - [配置存储](tutorials/store.md)
   - [创建、编辑或解锁管理员帐户](tutorials/admin.md)
   - [创建或更新部署配置](tutorials/deployment.md)
   - [创建数据库模式](tutorials/database.md)
   - [显示或更改管理员URI](tutorials/admin-uri.md)
   - [启用或禁用维护模式](tutorials/maintenance-mode.md)
   - [启用或禁用模块](tutorials/manage-modules.md)
   - [安装扩展](tutorials/extensions.md)
   - [安装商务](tutorials/install.md)
   - [修改docroot以提高安全性](tutorials/docroot.md)
   - [卸载语言包](tutorials/language-packages.md)
   - [卸载模块](tutorials/uninstall-modules.md)
   - [卸载或重新安装Commerce](tutorials/uninstall.md)
   - [卸载主题](tutorials/themes.md)
   - [升级数据库模式](tutorials/database-upgrade.md)
