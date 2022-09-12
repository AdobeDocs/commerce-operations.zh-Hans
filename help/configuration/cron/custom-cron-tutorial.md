---
title: 配置自定义cron作业和cron组（教程）
description: 使用此分步教程创建自定义cron作业。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---


# 配置自定义cron作业

此分步教程将演示如何在示例模块中创建自定义cron作业和（可选）cron组。 您可以使用已有的模块，也可以使用 [`magento2-samples` 存储库][samples].

运行cron作业会导致向 `cron_schedule` 表格，其名称为cron作业， `custom_cron`.

我们还将向您展示如何（可选）创建cron组，您可以使用该组通过除商务应用程序默认值以外的设置运行自定义cron作业。

在本教程中，我们假设：

- 商务应用程序安装在 `/var/www/html/magento2`
- 您的商务数据库用户名和密码均为 `magento`
- 您执行所有操作， [文件系统所有者](../../installation/prerequisites/file-system/overview.md)

## 步骤1:获取示例模块

要设置自定义cron作业，您需要一个示例模块。 我们建议 `magento-module-minimal` 模块。

如果您已经有一个示例模块，则可以使用它；跳过此步骤和下一步，并继续执行步骤3:创建要运行cron的类。

**获取示例模块**:

1. 作为或切换到 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).
1. 更改为Commerce应用程序根目录以外的目录（例如，您的主目录）。
1. 克隆 [`magento2-samples` 存储库][samples].

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   如果命令失败并出现错误 `Permission denied (publickey).`，您必须 [将您的SSH公钥添加到GitHub.com][git-ssh].

1. 创建一个要将示例代码复制到的目录：

   ```bash
   mkdir -p /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. 复制示例模块代码：

   ```bash
   cp -r ~/magento2-samples/sample-module-minimal/* /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. 验证文件是否正确复制：

   ```bash
   ls -al /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

   您应会看到以下结果：

   ```terminal
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

1. 更新商务数据库和架构：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除缓存：

   ```bash
   bin/magento cache:clean
   ```

## 步骤2:验证示例模块

在继续操作之前，请确认已注册并启用示例模块。

1. 运行以下命令：

   ```bash
   bin/magento module:status Magento_SampleMinimal
   ```

1. 确保已启用模块。

   ```terminal
   Module is enabled
   ```

>[!TIP]
>
>如果输出指示 `Module does not exist`，查看 [步骤1](#step-1-get-a-sample-module) 小心。 确保代码位于正确的目录中。 拼写和大小写很重要；如果有任何不同，则不会加载模块。 另外，不要忘记跑 `magento setup:upgrade`.

## 步骤3:创建要运行cron的类

此步骤显示了一个用于创建cron作业的简单类。 类只向 `cron_schedule` 表。

要创建类，请执行以下操作：

1. 为类创建一个目录，然后更改为该目录：

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. 已创建名为 `Test.php` 目录中，其中包含以下内容：

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

## 步骤4:创建 `crontab.xml`

的 `crontab.xml` 文件会设置运行自定义cron代码的计划。

创建 `crontab.xml` 如下 `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc` 目录：

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

上一个 `crontab.xml` 运行 `Magento/SampleMinimal/Cron/Test.php` 每分钟类一次，导致向 `cron_schedule` 表。

要从管理员中配置cron计划，请使用系统配置字段的配置路径。

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

其中， `system/config/path` 是 `etc/adminhtml/system.xml` 的子模块。

## 步骤5:编译和缓存清理

使用以下命令编译代码：

```bash
bin/magento setup:di:compile
```

然后，使用以下命令清除缓存：

```bash
bin/magento cache:clean
```

## 步骤6:验证cron作业

此步骤说明如何在 `cron_schedule` 数据库表。

要验证cron，请执行以下操作：

1. 运行Commerce cron作业：

   ```bash
   bin/magento cron:run
   ```

1. 输入 `magento cron:run` 命令两三次。

   第一次输入命令时，它会将作业排入队列；随后，将运行cron作业。 必须输入命令 _至少_ 两次。

1. 运行SQL查询 `SELECT * from cron_schedule WHERE job_code like '%custom%'` 如下所示：

   1. 输入 `mysql -u magento -p`
   1. 在 `mysql>` 提示，输入 `use magento;`
   1. 输入 `SELECT * from cron_schedule WHERE job_code like '%custom%';`

      结果应类似于以下内容：

      ```terminal
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      | schedule_id | job_code       | status  | messages | created_at        | scheduled_at        | executed_at         | finished_at     |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      |        3670 | custom_cronjob | success | NULL     | 2016-11-02 09:38:03 | 2016-11-02 09:38:00 | 2016-11-02 09:39:03 | 2016-11-02 09:39:03 |
      |        3715 | custom_cronjob | success | NULL     | 2016-11-02 09:53:03 | 2016-11-02 09:53:00 | 2016-11-02 09:54:04 | 2016-11-02 09:54:04 |
      |        3758 | custom_cronjob | success | NULL     | 2016-11-02 10:09:03 | 2016-11-02 10:09:00 | 2016-11-02 10:10:03 | 2016-11-02 10:10:03 |
      |        3797 | custom_cronjob | success | NULL     | 2016-11-02 10:24:03 | 2016-11-02 10:24:00 | 2016-11-02 10:25:03 | 2016-11-02 10:25:03 |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      ```

1. （可选）验证消息是否写入商务的系统日志：

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   您应会看到一个或多个如下条目：

   ```terminal
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   这些消息来自 `execute` 方法 `Test.php`:

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

如果SQL命令和系统日志不包含任何条目，请运行 `magento cron:run` 再命令几次然后等待。 数据库可能需要一些时间才能更新。

## 步骤7（可选）：设置自定义Cron组

此步骤将显示如何（可选）设置自定义客户群组。 如果您希望自定义cron作业以不同于其他cron作业的计划运行（通常为每分钟运行一次），或者您希望使用不同设置运行多个自定义cron作业，则应设置一个自定义cron组。

要设置自定义Cron组，请执行以下操作：

1. 打开 `crontab.xml` 在文本编辑器中。
1. 更改 `<group id="default">` to `<group id="custom_crongroup">`
1. 退出文本编辑器。
1. 创建 `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml` ，其内容如下：

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

有关选项含义的描述，请参阅 [自定义转码参考](custom-cron-reference.md).

## 步骤8:验证您的自定义客户群组

此 _可选_ 步骤显示如何使用管理员验证您的自定义cron群组。

要验证您的自定义Cron组，请执行以下操作：

1. 为自定义群组运行Commerce Cron作业：

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   至少运行两次命令。

1. 清除缓存：

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. 以管理员身份登录。
1. 单击 **商店** > **设置** > **配置** > **高级** > **系统**.
1. 在右侧窗格中，展开 **克龙**.

   您的群组显示如下：

   ![您的自定义客户群组](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
