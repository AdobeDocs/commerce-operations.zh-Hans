---
title: 配置和运行cron作业
description: 了解如何管理cron作业。
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 0%

---

# 配置cron作业

{{file-system-owner}}

有几个Commerce功能至少需要一个cron作业，该作业可安排未来开展的活动。 以下是这些活动的部分列表：

- 目录价格规则
- 快讯
- 生成Google站点地图
- 客户警报/通知（产品价格变动，产品重新上架）
- 重新索引
- 私人销售(仅限Adobe Commerce)
- 自动更新汇率
- 所有Commerce电子邮件（包括订单确认和事务性）

>[!WARNING]
>
>您无法再运行`dev/tools/cron.sh`，因为脚本已被删除。

>[!INFO]
>
>Commerce依赖正确的cron作业配置来实现许多重要的系统功能，包括编制索引。 如果未正确设置，则意味着Commerce将无法按预期工作。

UNIX系统使用&#x200B;_crontab_&#x200B;安排由特定用户执行的任务，该文件包含有关cron守护程序的说明，指示守护程序在生效时“在此日期运行此命令”。 每个用户都有自己的crontab，任何给定的crontab中的命令都以拥有该命令的用户身份执行。

要在Web浏览器中运行cron，请参阅[在浏览器中运行的安全cron.php ](../security/secure-cron-php.md)。

## 创建或删除Commerce crontab

此部分讨论如何创建或删除Commerce crontab(即Commerce cron作业的配置)。

_crontab_&#x200B;是用于运行cron作业的配置。

Commerce应用程序使用可以使用不同配置运行的cron任务。 PHP命令行配置控制常规cron作业，该作业可重新索引索引器、生成电子邮件、生成Sitemap等。

>[!WARNING]
>
>- 为避免在安装和升级过程中出现问题，我们强烈建议您将相同的PHP设置同时应用于PHP命令行配置和PHP Web服务器插件的配置。 有关详细信息，请参阅[必需的PHP设置](../../installation/prerequisites/php-settings.md)。
>- 在多节点系统中，crontab只能在一个节点上运行。 仅当出于与性能或可扩展性相关的原因设置了多个Web节点时，此规则才适用。

### 创建Commerce crontab

从版本2.2开始，Commerce会为您创建一个crontab。 我们将Commerce crontab添加到Commerce文件系统所有者的任何已配置crontab中。 换言之，如果您已经为其他扩展或应用程序设置了crontab，我们会向其添加Commerce crontab。

Commerce crontab位于您的crontab中的`#~ MAGENTO START`和`#~ MAGENTO END`条评论中。

要创建Commerce crontab，请执行以下操作：

1. 作为[文件系统所有者](../../installation/prerequisites/file-system/overview.md)登录或切换到该所有者。
1. 转到Commerce安装目录。
1. 输入以下命令：

   ```bash
   bin/magento cron:install [--force]
   ```

使用`--force`重写现有的crontab。

>[!INFO]
>
>- `magento cron:install`不会重写您的crontab中的`#~ MAGENTO START`和`#~ MAGENTO END`评论中的现有crontab。
>- `magento cron:install --force`对Commerce注释之外的任何cron作业没有影响。

要查看crontab，请输入以下命令作为文件系统所有者：

```bash
crontab -l
```

下面是一个示例：

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>`update/cron.php`文件已在Commerce 2.4.0中删除，如果该文件存在于您的安装中，则可以安全地将其删除。
>
>对`update/cron.php`和`bin/magento setup:cron:run`的任何引用也应从crontab中删除

### 删除Commerce crontab

您应该仅在卸载Commerce应用程序之前删除Commerce crontab。

要删除Commerce crontab，请执行以下操作：

1. 以或切换身份登录到[文件系统所有者](../../installation/prerequisites/file-system/overview.md)。
1. 转到Commerce安装目录。
1. 输入以下命令：

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>此命令对crontab中`#~ MAGENTO START`和`#~ MAGENTO END`评论以外的cron作业没有影响。

## 从命令行运行cron

命令选项：

```bash
bin/magento cron:run [--group="<cron group name>"]
```

其中`--group`指定要运行的cron组（忽略此选项以为所有组运行cron）

要运行索引cron作业，请输入：

```bash
bin/magento cron:run --group index
```

要运行默认的cron作业，请输入：

```bash
bin/magento cron:run --group default
```

要设置自定义cron作业和组，请参阅[配置自定义cron作业和cron组](../cron/custom-cron.md)。

>[!INFO]
>
>您必须运行两次cron：第一次发现要运行的任务，第二次发现要运行的任务，然后运行任务本身。 第二次cron运行必须在每个任务的`scheduled_at`时间或之后进行。

## 记录

所有`cron`作业信息已从`system.log`移至单独的`cron.log`。
默认情况下， cron信息可在`<install_directory>/var/log/cron.log`中找到。
来自cron作业的所有异常均由`\Magento\Cron\Observer\ProcessCronQueueObserver::execute`记录。

除了登录`cron.log`之外：

- 具有`ERROR`和`MISSED`状态的失败作业将记录到`<install_directory>/var/log/support_report.log`。

- 在`<install_directory>/var/log/exception.log`中，状态为`ERROR`的作业始终记录为`CRITICAL`。

- 状态为`MISSED`的作业在`<install_directory>/var/log/debug.log`目录中记录为`INFO`（仅限开发人员模式）。

>[!INFO]
>
>所有cron数据也将写入Commerce数据库的`cron_schedule`表中。 该表提供了cron作业的历史记录，包括：
>
>- 作业ID和代码
>- 状态
>- 创建日期
>- 计划日期
>- 执行日期
>- 完成日期
>
>要查看表中的记录，请在命令行上登录到Commerce数据库并输入`SELECT * from cron_schedule;`。
