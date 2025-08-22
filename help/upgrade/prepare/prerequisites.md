---
title: 完成先决条件
description: 通过完成这些先决条件步骤，准备Adobe Commerce项目以进行升级。
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '1866'
ht-degree: 0%

---

# 完成升级先决条件

了解运行Adobe Commerce所需的内容很重要。 您必须首先查看计划升级到的版本的[系统要求](../../installation/system-requirements.md)。

查看系统要求后，必须在升级系统之前完成以下先决条件：

* 更新所有软件
* 验证是否安装了受支持的搜索引擎
* 转换数据库表格式
* 设置打开文件限制
* 验证cron作业是否正在运行
* 设置`DATA_CONVERTER_BATCH_SIZE`
* 验证文件系统权限
* 设置`pub/`目录根
* 安装编辑器更新插件

## 更新所有软件

[系统要求](../../installation/system-requirements.md)准确地描述了哪些版本的第三方软件已通过Adobe Commerce版本测试。

确保更新了环境中的所有系统要求和依赖项。 请参阅PHP [7.4](https://www.php.net/manual/en/migration74.php)、PHP [8.0](https://www.php.net/manual/en/migration80.php)、PHP [8.1](https://www.php.net/manual/en/migration81.php)和[所需的PHP设置](../../installation/prerequisites/php-settings.md#php-settings)。

>[!NOTE]
>
>对于云基础架构Pro项目上的Adobe Commerce，您必须创建[支持](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)票证，以在暂存环境和生产环境中安装或更新服务。 指示所需的服务更改，并在票证中包含更新的`.magento.app.yaml`和`services.yaml`文件以及PHP版本。 Cloud Infrastructure团队更新项目最多可能需要48小时。 请参阅[支持的软件和服务](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services)。

## 验证是否安装了受支持的搜索引擎

Adobe Commerce需要安装Elasticsearch或OpenSearch才能使用该软件。

**如果您要从2.3.x升级到2.4**，则必须检查您在2.3.x实例中是使用MySQL、Elasticsearch还是第三方扩展作为目录搜索引擎。 结果确定在升级到2.4之前&#x200B;_必须_&#x200B;做什么。

**如果要升级2.3.x或2.4.x版本行中的修补程序版本**，如果已安装Elasticsearch 7.x，则可以选择[迁移到OpenSearch](opensearch-migration.md)。

您可以使用命令行或管理员来确定目录搜索引擎：

* 输入`bin/magento config:show catalog/search/engine`命令。 该命令返回值`mysql`、`elasticsearch`(表示已配置Elasticsearch 2)、`elasticsearch5`、`elasticsearch6`、`elasticsearch7`或自定义值，表示您已安装第三方搜索引擎。 对于低于2.4.6的版本，为Elasticsearch 7或OpenSearch引擎使用`elasticsearch7`值。 对于版本2.4.6及更高版本，请使用OpenSearch引擎的`opensearch`值。

* 从管理员中，检查&#x200B;**[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]**&#x200B;字段的值。

以下部分介绍在升级到2.4.0之前必须执行的操作。

### MySQL

从2.4开始，MySQL不再是一个受支持的目录搜索引擎。 升级之前，必须安装和配置Elasticsearch或OpenSearch。 请使用以下资源来帮助您完成此过程：

* [安装和配置Elasticsearch](../../configuration/search/overview-search.md)
* [正在安装Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* 配置[nginx](../../installation/prerequisites/search-engine/configure-nginx.md)或[Apache](../../installation/prerequisites/search-engine/configure-apache.md)以使用您的搜索引擎
* [配置Commerce以使用Elasticsearch](../../configuration/search/configure-search-engine.md)并重新索引

一些第三方目录搜索引擎在Adobe Commerce搜索引擎上运行。 请与供应商联系以确定是否必须更新扩展。

### MySQL 8.4更改

Adobe在2.4.8版本中添加了对MySQL 8.4的支持。
本节介绍开发人员应了解的对MySQL 8.4的主要更改。

#### 已弃用的非标准键

使用非唯一键或部分键作为外键是不标准的，在MySQL 8.4中已弃用。从MySQL 8.4.0开始，您必须通过将[`restrict_fk_on_non_standard_key`](https://dev.mysql.com/doc/refman/8.4/en/server-system-variables.html#sysvar_restrict_fk_on_non_standard_key)设置为`OFF`或使用`--skip-restrict-fk-on-non-standard-key`选项启动服务器来显式启用此类密钥。

#### 从MySQL 8.0（或更早版本）升级到MySQL 8.4

要将MySQL从版本8.0正确升级到版本8.4，必须按顺序执行以下步骤：

1. 启用维护模式：

   ```bash
   bin/magento maintenance:enable
   ```

1. 进行数据库备份：

   ```bash
   bin/magento setup:backup --db
   ```

1. 将MySQL升级到版本8.4。
1. 在`restrict_fk_on_non_standard_key`文件的`OFF`中将`[mysqld]`设置为`my.cnf`。

   ```bash
   [mysqld]
   restrict_fk_on_non_standard_key = OFF 
   ```

   >[!WARNING]
   >
   >如果不将`restrict_fk_on_non_standard_key`的值更改为`OFF`，则在导入期间将收到以下错误：
   >
   >```sql
   > ERROR 6125 (HY000) at line 2164: Failed to add the foreign key constraint. Missing unique key for constraint 'CAT_PRD_FRONTEND_ACTION_PRD_ID_CAT_PRD_ENTT_ENTT_ID' in the referenced table 'catalog_product_entity'
   >```
1. 重新启动MySQL服务器。
1. 将备份的数据导入MySQL。
1. 清理缓存：

   ```bash
   bin/magento cache:clean
   ```

1. 禁用维护模式：

   ```bash
   bin/magento maintenance:disable
   ```

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### 搜索引擎

在升级到2.4.0之前，必须安装和配置Elasticsearch 7.6或更高版本或者OpenSearch 1.2。Adobe不再支持Elasticsearch 2.x、5.x和6.x。[配置指南](../../configuration/search/configure-search-engine.md)中的&#x200B;_搜索引擎配置_&#x200B;介绍了将Elasticsearch升级到支持的版本后必须执行的任务。

有关在部署到生产环境之前备份数据、检测潜在迁移问题和测试升级的完整说明，请参阅[升级Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html)。 根据您当前的Elasticsearch版本，可能需要也可能不需要完全重新启动群集。

Elasticsearch需要Java开发工具包(JDK) 1.8或更高版本。 请参阅[安装Java软件开发工具包(JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk)以检查安装的JDK版本。

#### OpenSearch

OpenSearch是Elasticsearch 7.10.2的一个开源分支，它遵循Elasticsearch的许可更改原则。 以下版本的Adobe Commerce引入了对OpenSearch的支持：

* 2.4.6（OpenSearch具有单独的模块和设置）
* 2.4.5
* 2.4.4
* 2.4.3-p2
* 2.3.7 - p3

只有升级到上述（或更高版本）列出的Elasticsearch版本时，才能[从Adobe Commerce迁移到OpenSearch](opensearch-migration.md)。

OpenSearch需要JDK 1.8或更高版本。 请参阅[安装Java软件开发工具包(JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk)以检查安装的JDK版本。

[搜索引擎配置](../../configuration/search/configure-search-engine.md)描述了更改搜索引擎后必须执行的任务。

#### 升级Elasticsearch

Adobe Commerce 2.4.6中引入了对Elasticsearch 8.x的支持。以下说明显示了Elasticsearch从7.x升级到8.x的示例：

>[!NOTE]
>
>在即将发布的2.4.8版本中，这些步骤将不是必需的，因为默认情况下包含Elasticsearch 8模块，因此您无需单独安装该模块。

1. 将Elasticsearch 7.x服务器升级到8.x，并确保已启动并正在运行。 请参阅[Elasticsearch文档](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)。

1. 通过将以下配置添加到您的`id_field_data`文件并重新启动Elasticsearch 8.x服务来启用`elasticsearch.yml`字段。

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >为了支持Elasticsearch 8.x，Adobe Commerce 2.4.6在默认情况下不允许使用`indices.id_field_data`属性，并使用`_id`属性中的`docvalue_fields`字段。

1. 在Adobe Commerce项目的根目录中，更新编辑器依赖项以删除`Magento_Elasticsearch7`模块并安装`Magento_Elasticsearch8`模块。

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

   如果您遇到`psr/http-message`的依赖关系错误，请单击以展开以下疑难解答部分：

   +++故障排除

   如果在安装Elasticsearch 8时遇到依赖关系冲突，特别是与`psr/http-message`的冲突，可以通过执行以下步骤来解决此问题：

   1. 首先，需要Elasticsearch 8模块，而不更新其他依赖项：

      ```bash
      composer require magento/module-elasticsearch-8 --no-update
      ```

   1. 然后更新Elasticsearch 8模块和`aws/aws-sdk-php`包：

      ```bash
      composer update magento/module-elasticsearch-8 aws/aws-sdk-php -W
      ```

   此方法适用于2.4.7-p4和PHP 8.3。出现此问题的原因是`aws/aws-sdk-php`需要`psr/http-message >= 2.0`，这可能会导致冲突。 上述步骤有助于解决这些依赖性问题。

   +++

1. 更新项目组件。

   ```bash
   bin/magento setup:upgrade
   ```

1. 在[中](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin)配置Elasticsearch[!DNL Admin]。

1. 重新索引目录索引。

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 从启用的缓存类型中删除所有项目。

   ```bash
   bin/magento cache:clean
   ```

#### 降级Elasticsearch

如果您无意中升级了服务器上的Elasticsearch版本，或确定由于任何其他原因需要降级，则还必须更新Adobe Commerce项目依赖项。 例如，从Elasticsearch 8.x降级到7.x

1. 将Elasticsearch 8.x服务器降级为7.x，并确保其已启动并正在运行。 请参阅[Elasticsearch文档](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)。

1. 在Adobe Commerce项目的根目录中，更新编辑器依赖项以删除`Magento_Elasticsearch8`模块及其编辑器依赖项，并安装`Magento_Elasticsearch7`模块。

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. 更新项目组件。

   ```bash
   bin/magento setup:upgrade
   ```

1. 在[中](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin)配置Elasticsearch[!DNL Admin]。

1. 重新索引目录索引。

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. 从启用的缓存类型中删除所有项目。

   ```bash
   bin/magento cache:clean
   ```

### 第三方扩展

我们建议您联系搜索引擎供应商，以确定您的扩展是否与Adobe Commerce版本完全兼容。

## 转换数据库表格式

您必须将所有数据库表的格式从`COMPACT`转换为`DYNAMIC`。 还必须将存储引擎类型从`MyISAM`转换为`InnoDB`。 请参阅[最佳实践](../../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md)。

## 设置打开文件限制

设置打开文件限制(ulimit)有助于避免多次递归调用长查询字符串失败或使用`bin/magento setup:rollback`命令时出现问题。 此命令对于不同的UNIX shell是不同的。 有关`ulimit`命令的详细信息，请咨询您的个人风格。

Adobe建议将打开的文件[ulimit](https://ss64.com/bash/ulimit.html)设置为`65536`或更多的值，但如有必要，您可以使用更大的值。 您可以在命令行上设置限制，也可以将其设置为用户shell的永久设置。

要从命令行设置限制，请执行以下操作：

1. 切换到[文件系统所有者](../../installation/prerequisites/file-system/overview.md)。
1. 将限制设置为`65536`。

   ```bash
   ulimit -n 65536
   ```

要在Bash shell中设置值，请执行以下操作：

1. 切换到[文件系统所有者](../../installation/prerequisites/file-system/overview.md)。
1. 在文本编辑器中打开`/home/<username>/.bashrc`。
1. 添加以下行：

   ```bash
   ulimit -n 65536
   ```

1. 保存对`.bashrc`文件所做的更改并退出文本编辑器。

>[!IMPORTANT]
>
>我们建议您避免为`pcre.recursion_limit`文件中的`php.ini`属性设置值，因为它可能会导致不完整的回滚，并且不会出现失败通知。

## 验证cron作业是否正在运行

UNIX任务计划程序`cron`对于日常Adobe Commerce操作至关重要。 它计划重新索引、新闻稿、电子邮件和站点地图等内容。 多个功能要求至少有一个cron作业作为文件系统所有者运行。

要验证您的cron作业是否设置正确，请通过输入以下命令作为文件系统所有者检查crontab：

>[!NOTE]
>
>crontab是负责运行cron作业的配置文件。

```bash
crontab -l
```

应显示类似于以下内容的结果：

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

cron未运行的另一个症状是管理员中出现以下错误：

![系统消息 — cron未运行](../../assets/upgrade-guide/cron-not-running.png)

要查看错误，请单击窗口顶部的&#x200B;**系统消息**，如下所示：

![系统消息通知](../../assets/upgrade-guide/system-messages.png)

有关详细信息，请参阅[配置和运行cron](../../configuration/cli/configure-cron-jobs.md)。

## 设置DATA_CONVERTER_BATCH_SIZE

Adobe Commerce 2.4包含安全增强功能，这些功能要求将某些数据从序列化转换为JSON。 此转换在升级期间发生，并且可能需要很长时间，具体取决于数据库中的数据量。

以下表格受到的影响最大：

* `catalogrule`
* `core_config_data`
* `magento_reward_history`
* `quote_payment`
* `quote`
* `sales_order_payment`
* `sales_order`
* `salesrule`
* `url_rewrite`

如果您有大量数据，可以通过设置环境变量`DATA_CONVERTER_BATCH_SIZE`的值来提高性能。 默认情况下，该值设置为`50,000`。

要设置环境变量，请执行以下操作：

1. 切换到[文件系统所有者](../../installation/prerequisites/file-system/overview.md)。
1. 设置变量：

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE`需要内存；如果不先测试它，请避免将其设置为较大的值（约1 GB）。

1. 升级完成后，您可以取消设置变量：

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## 验证文件系统权限

出于安全原因，Adobe Commerce要求对文件系统具有某些权限。 权限与&#x200B;_[所有权](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_&#x200B;不同。 所有权决定了谁可以对文件系统执行操作；权限决定了用户可以执行哪些操作。

文件系统中的目录必须可由[文件系统所有者的](../../installation/prerequisites/file-system/overview.md)组写入。

要验证您的文件系统权限是否设置正确，请登录到应用程序服务器或使用托管提供商的文件管理器应用程序。

例如，如果应用程序安装在`/var/www/html/magento2`中，请输入以下命令：

```bash
ls -l /var/www/html/magento2
```

示例输出：

```console
total 1028
drwxrwx---. 12 magento_user apache   4096 Jun  7 07:55 .
drwxr-xr-x.  3 root         root     4096 May 11 14:29 ..
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 app
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 bin
-rw-rw----.  1 magento_user apache 439792 Apr 27 21:23 CHANGELOG.md
-rw-rw----.  1 magento_user apache   3422 Apr 27 21:23 composer.json
-rw-rw----.  1 magento_user apache 425214 Apr 27 21:27 composer.lock
-rw-rw----.  1 magento_user apache   3425 Apr 27 21:23 CONTRIBUTING.md
-rw-rw----.  1 magento_user apache  10011 Apr 27 21:23 CONTRIBUTOR_LICENSE_AGREEMENT.html
-rw-rw----.  1 magento_user apache    631 Apr 27 21:23 COPYING.txt
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 dev
-rw-rw----.  1 magento_user apache   2926 Apr 27 21:23 Gruntfile.js
-rw-rw----.  1 magento_user apache   7592 Apr 27 21:23 .htaccess
-rw-rw----.  1 magento_user apache   6419 Apr 27 21:23 .htaccess.sample
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 lib
-rw-rw----.  1 magento_user apache  10376 Apr 27 21:23 LICENSE_AFL.txt
-rw-rw----.  1 magento_user apache  30634 Apr 27 21:23 LICENSE_EE.txt
-rw-rw----.  1 magento_user apache  10364 Apr 27 21:23 LICENSE.txt
-rw-rw----.  1 magento_user apache   4108 Apr 27 21:23 nginx.conf.sample
-rw-rw----.  1 magento_user apache   1427 Apr 27 21:23 package.json
-rw-rw----.  1 magento_user apache   1659 Apr 27 21:23 .php_cs
-rw-rw----.  1 magento_user apache    804 Apr 27 21:23 php.ini.sample
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 phpserver
drwxrwx---.  6 magento_user apache   4096 Jun  7 07:53 pub
-rw-rw----.  1 magento_user apache   2207 Apr 27 21:23 README_EE.md
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 setup
-rw-rw----.  1 magento_user apache   3731 Apr 27 21:23 .travis.yml
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 update
drwxrws---. 11 magento_user apache   4096 Jun 13 16:05 var
drwxrws---. 29 magento_user apache   4096 Jun  7 07:53 vendor
```

有关示例输出的说明，请参阅以下内容：

* 大多数文件为`-rw-rw----`，即`660`
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* 文件系统所有者是`magento_user`

要获取更多详细信息，可以输入以下命令：

```bash
ls -la /var/www/html/magento2/pub
```

由于Adobe Commerce会将静态文件资产部署到`pub`的子目录，因此最好也验证其权限和所有权。

有关详细信息，请参阅[文件系统权限和所有权](../../installation/prerequisites/file-system/overview.md)。

## 设置`pub/`目录根

有关详细信息，请参阅[修改docroot以提高安全性](../../installation/tutorials/docroot.md)。

## 安装编辑器更新插件

[`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) Composer插件解析了在更新到新产品要求之前必须对根项目`composer.json`文件进行的更改。

该插件通过识别和帮助您解决相关性冲突，而不是要求您手动识别和修复这些冲突，从而部分自动化了手动升级。

要安装插件，请执行以下操作：

1. 将包添加到您的`composer.json`文件。

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. 更新依赖关系：

   ```bash
   composer update
   ```

<!-- Last updated from includes: 2024-02-12 09:51:27 -->
