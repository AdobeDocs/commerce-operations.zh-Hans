---
title: 配置自定义cron作业和cron组（教程）
description: 通过此Adobe Commerce分步教程了解如何创建自定义cron作业。 发现模块设置和cron组配置。
exl-id: d8efcafc-3ae1-4c2d-a8ad-4a806fb48932
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 0%

---

# 配置自定义cron作业

此分步教程将演示如何在示例模块中创建自定义cron作业和（可选）cron组。 您可以使用已有的模块，也可以使用我们[`magento2-samples`存储库][samples]中的示例模块。

运行cron作业会导致向`cron_schedule`表中添加一个名为cron作业`custom_cron`的行。

我们还将向您说明如何选择创建一个cron组，以便您能够使用该组通过Commerce应用程序默认值以外的设置运行自定义cron作业。

在本教程中，我们假定：

- Commerce应用程序安装在`/var/www/html/magento2`中
- 您的Commerce数据库用户名和密码均为`magento`
- 您以[文件系统所有者](../../installation/prerequisites/file-system/overview.md)的身份执行所有操作

## 步骤1：获取示例模块

要设置自定义cron作业，您需要一个示例模块。 我们建议`magento-module-minimal`模块。

如果您已经有一个示例模块，则可以使用该模块；跳过此步骤和下一步，继续步骤3：创建类以运行cron。

**获取示例模块**：

1. 以[文件系统所有者](../../installation/prerequisites/file-system/overview.md)的身份登录或切换到Commerce服务器。
1. 更改为不在Commerce应用程序根目录中的目录（例如，主目录）。
1. 克隆[`magento2-samples`存储库][samples]。

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   如果命令失败，出现错误`Permission denied (publickey).`，您必须[将SSH公钥添加到GitHub.com][git-ssh]。

1. 创建要将示例代码复制到其中的目录：

   ```bash
   mkdir -p /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. 复制示例模块代码：

   ```bash
   cp -r ~/magento2-samples/sample-module-minimal/* /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. 验证是否正确复制了文件：

   ```bash
   ls -al /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

   您应会看到以下结果：

   ```
   drwxrwsr-x.   4 magento_user apache  4096 Oct 30 13:19 .
   drwxrwsr-x. 121 magento_user apache  4096 Oct 30 13:19 ..
   -rw-rw-r--.   1 magento_user apache   372 Oct 30 13:19 composer.json
   drwxrwsr-x.   2 magento_user apache  4096 Oct 30 13:19 etc
   -rw-rw-r--.   1 magento_user apache 10376 Oct 30 13:19 LICENSE_AFL.txt
   -rw-rw-r--.   1 magento_user apache 10364 Oct 30 13:19 LICENSE.txt
   -rw-rw-r--.   1 magento_user apache  1157 Oct 30 13:19 README.md
   -rw-rw-r--.   1 magento_user apache   270 Oct 30 13:19 registration.php
   drwxrwsr-x.   3 magento_user apache  4096 Oct 30 13:19 Test
   ```

1. 更新Commerce数据库和架构：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清理缓存：

   ```bash
   bin/magento cache:clean
   ```

## 第2步：验证示例模块

在继续之前，请验证是否已注册并启用示例模块。

1. 运行以下命令：

   ```bash
   bin/magento module:status Magento_SampleMinimal
   ```

1. 确保模块已启用。

   ```
   Module is enabled
   ```

>[!TIP]
>
>如果输出指示`Module does not exist`，请仔细查看[步骤1](#step-1-get-a-sample-module)。 确保代码位于正确的目录中。 拼写和大小写很重要；如果有任何不同，则不会加载模块。 另外，不要忘记运行`magento setup:upgrade`。

## 步骤3：创建一个类以运行cron

此步骤显示用于创建cron作业的简单类。 该类仅向`cron_schedule`表中写入一行，以确认已成功设置该类。

要创建类：

1. 为类创建一个目录并转到该目录：

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. 在该目录中创建了一个名为`Test.php`的文件，其内容如下：

   ```php
   <?php
   namespace Magento\SampleMinimal\Cron;
   
   use Psr\Log\LoggerInterface;
   
   class Test {
       protected $logger;
   
       public function __construct(LoggerInterface $logger) {
           $this->logger = $logger;
       }
   
      /**
       * Write to system.log
       *
       * @return void
       */
       public function execute() {
           $this->logger->info('Cron Works');
       }
   }
   ```

## 步骤4：创建`crontab.xml`

`crontab.xml`文件设置运行自定义cron代码的计划。

按如下方式在`crontab.xml`目录中创建`/var/www/html/magento2/app/code/Magento/SampleMinimal/etc`：

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

前面`crontab.xml`每分钟运行一次`Magento/SampleMinimal/Cron/Test.php`类，从而在`cron_schedule`表中添加了一行。

要使管理员能够配置cron计划，请使用系统配置字段的配置路径。

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <config_path>system/config/path</config_path>
        </job>
    </group>
</config>
```

其中，`system/config/path`是在模块的`etc/adminhtml/system.xml`中定义的系统配置路径。

## 步骤5：编译和缓存清理

使用以下命令编译代码：

```bash
bin/magento setup:di:compile
```

并使用以下命令清除缓存：

```bash
bin/magento cache:clean
```

## 步骤6：验证cron作业

此步骤显示如何使用`cron_schedule`数据库表上的SQL查询成功验证自定义cron作业。

验证cron：

1. 运行Commerce cron作业：

   ```bash
   bin/magento cron:run
   ```

1. 输入`magento cron:run`命令两或三次。

   第一次输入该命令时，它将作业排入队列；随后，将运行cron作业。 必须输入命令&#x200B;_至少_&#x200B;两次。

1. 按如下方式运行SQL查询`SELECT * from cron_schedule WHERE job_code like '%custom%'`：

   1. 输入`mysql -u magento -p`
   1. 在`mysql>`提示下，输入`use magento;`
   1. 输入`SELECT * from cron_schedule WHERE job_code like '%custom%';`

      结果应类似于以下内容：

      ```
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      | schedule_id | job_code       | status  | messages | created_at        | scheduled_at        | executed_at         | finished_at     |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      |        3670 | custom_cronjob | success | NULL     | 2016-11-02 09:38:03 | 2016-11-02 09:38:00 | 2016-11-02 09:39:03 | 2016-11-02 09:39:03 |
      |        3715 | custom_cronjob | success | NULL     | 2016-11-02 09:53:03 | 2016-11-02 09:53:00 | 2016-11-02 09:54:04 | 2016-11-02 09:54:04 |
      |        3758 | custom_cronjob | success | NULL     | 2016-11-02 10:09:03 | 2016-11-02 10:09:00 | 2016-11-02 10:10:03 | 2016-11-02 10:10:03 |
      |        3797 | custom_cronjob | success | NULL     | 2016-11-02 10:24:03 | 2016-11-02 10:24:00 | 2016-11-02 10:25:03 | 2016-11-02 10:25:03 |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      ```

1. （可选）验证消息是否已写入Commerce的系统日志：

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   您应会看到一个或多个条目，如下所示：

   ```
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   这些消息来自`execute`中的`Test.php`方法：

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

如果SQL命令和系统日志不包含任何条目，请再运行几次`magento cron:run`命令并等待。 更新数据库可能需要一些时间。

## 步骤7（可选）：设置自定义cron组

此步骤说明如何根据需要设置自定义cron组。 如果您希望自定义cron作业以与其他cron作业不同的计划运行（通常每分钟运行一次），或者如果您希望使用不同的设置运行多个自定义cron作业，则应该设置自定义cron组。

要设置自定义cron组，请执行以下操作：

1. 在文本编辑器中打开`crontab.xml`。
1. 将`<group id="default">`更改为`<group id="custom_crongroup">`
1. 退出文本编辑器。
1. 创建包含以下内容的`/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml`：

   ```xml
   <?xml version="1.0"?>
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
       <group id="custom_crongroup">
           <schedule_generate_every>1</schedule_generate_every>
           <schedule_ahead_for>4</schedule_ahead_for>
           <schedule_lifetime>2</schedule_lifetime>
           <history_cleanup_every>10</history_cleanup_every>
           <history_success_lifetime>60</history_success_lifetime>
           <history_failure_lifetime>600</history_failure_lifetime>
           <use_separate_process>1</use_separate_process>
       </group>
   </config>
   ```

有关选项含义的说明，请参阅[自定义crons引用](custom-cron-reference.md)。

## 步骤8：验证您的自定义cron组

此&#x200B;_可选_&#x200B;步骤显示如何使用管理员验证您的自定义cron组。

验证您的自定义cron组：

1. 为自定义组运行Commerce cron作业：

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   至少运行命令两次。

1. 清理缓存：

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. 以管理员身份登录到管理员。
1. 单击&#x200B;**存储** > **设置** > **配置** > **高级** > **系统**。
1. 在右窗格中，展开&#x200B;**Cron**。

   您的cron组显示如下：

   ![您的自定义cron组](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
