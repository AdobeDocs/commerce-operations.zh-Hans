---
title: 配置自定义cron作业和cron组（教程）
description: 使用此分步教程可创建自定义cron作业。
exl-id: d8efcafc-3ae1-4c2d-a8ad-4a806fb48932
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---

# 配置自定义cron作业

此分步教程演示如何在示例模块中创建自定义cron作业和（可选）cron组。 您可以使用已有的模块，也可以使用我们的示例模块 [`magento2-samples` 存储库][samples].

运行cron作业会导致将一行添加到 `cron_schedule` 具有cron作业名称的表， `custom_cron`.

我们还将向您说明如何选择性创建cron组，您可以使用它来运行自定义cron作业，其设置不包括Commerce应用程序默认值。

在本教程中，我们假定：

- 商务应用程序安装在 `/var/www/html/magento2`
- 您的Commerce数据库用户名和密码都是 `magento`
- 您执行所有操作时， [文件系统所有者](../../installation/prerequisites/file-system/overview.md)

## 步骤1：获取示例模块

要设置自定义cron作业，您需要一个示例模块。 我们建议 `magento-module-minimal` 模块。

如果您已经有一个示例模块，则可以使用该模块；跳过此步骤和下一步，继续步骤3：创建类以运行cron。

**获取示例模块**：

1. 以或切换为登录到您的Commerce服务器 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).
1. 更改为不在Commerce应用程序根目录中的目录（例如，主目录）。
1. 克隆 [`magento2-samples` 存储库][samples].

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   如果命令失败并出现错误 `Permission denied (publickey).`，您必须 [将SSH公钥添加到GitHub.com][git-ssh].

1. 创建一个要向其中复制示例代码的目录：

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

1. 更新Commerce数据库和架构：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清理缓存：

   ```bash
   bin/magento cache:clean
   ```

## 步骤2：验证示例模块

在继续之前，请验证示例模块是否已注册并启用。

1. 运行以下命令：

   ```bash
   bin/magento module:status Magento_SampleMinimal
   ```

1. 确保模块已启用。

   ```terminal
   Module is enabled
   ```

>[!TIP]
>
>如果输出指示 `Module does not exist`，评论 [步骤1](#step-1-get-a-sample-module) 小心点。 确保代码位于正确的目录中。 拼写和大小写很重要；如果有任何不同，则不会加载模块。 还有，别忘了跑 `magento setup:upgrade`.

## 步骤3：创建类以运行cron

此步骤显示一个用于创建cron作业的简单类。 类只会将一行写入 `cron_schedule` 用于确认已成功设置的表。

要创建类，请执行以下操作：

1. 为类创建一个目录并转到该目录：

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. 创建了一个名为的文件 `Test.php` 目录，包含以下内容：

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

## 步骤4：创建 `crontab.xml`

此 `crontab.xml` 文件设置运行自定义cron代码的计划。

创建 `crontab.xml` 如下所示 `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc` 目录：

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

前一个 `crontab.xml` 运行 `Magento/SampleMinimal/Cron/Test.php` 类每分钟一次，导致行被添加到 `cron_schedule` 表格。

为了从管理员配置cron计划，请使用系统配置字段的配置路径。

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

其中， `system/config/path` 是中定义的系统配置路径 `etc/adminhtml/system.xml` 模块的。

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

此步骤说明如何在上使用SQL查询成功验证自定义cron作业。 `cron_schedule` 数据库表。

验证cron：

1. 运行Commerce cron作业：

   ```bash
   bin/magento cron:run
   ```

1. 输入 `magento cron:run` 指挥了两三次。

   第一次输入该命令时，它将作业排入队列；随后，将运行cron作业。 必须输入命令 _至少_ 两次。

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

1. （可选）验证消息是否已写入Commerce的系统日志：

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   您应会看到一个或多个条目，如下所示：

   ```terminal
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   这些消息来自 `execute` 中的方法 `Test.php`：

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

如果SQL命令和系统日志不包含任何条目，请运行 `magento cron:run` 再命令几次，然后等待。 更新数据库可能需要一些时间。

## 步骤7（可选）：设置自定义cron组

此步骤说明如何选择设置自定义cron组。 如果您希望自定义cron作业以与其他cron作业不同的计划运行（通常每分钟运行一次），或者希望使用不同的设置运行多个自定义cron作业，则应该设置自定义cron组。

要设置自定义cron组，请执行以下操作：

1. 打开 `crontab.xml` 在文本编辑器中。
1. 更改 `<group id="default">` 到 `<group id="custom_crongroup">`
1. 退出文本编辑器。
1. 创建 `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml` ，内容如下：

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

有关选项的含义的说明，请参见 [自定义crons引用](custom-cron-reference.md).

## 步骤8：验证您的自定义cron组

此 _可选_ 步骤显示如何使用管理员验证您的自定义cron组。

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
1. 单击 **商店** > **设置** > **配置** > **高级** > **系统**.
1. 在右窗格中，展开 **Cron**.

   您的cron组显示如下：

   ![您的自定义cron组](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
