---
title: 从RabbitMQ迁移到ActiveMQ
description: 了解如何替换用于Adobe Commerce本地安装的消息队列代理。
feature: Services, Configuration
source-git-commit: 8f57a4fa7744f4647ab96d0fcfae08b8eb4927c6
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 0%

---

# 迁移到ActiveMQ

ActiveMQ (Apache ActiveMQ Artemis)是一种高性能、多协议消息代理，为Adobe Commerce中处理消息队列的RabbitMQ提供了替代方案。

截至2.4.8-p3、2.4.7-p8和2.4.6-p13，Adobe Commerce支持ActiveMQ作为消息队列代理。 这为本地安装提供了更大的灵活性，以便根据其基础架构要求和专业知识在RabbitMQ和ActiveMQ之间进行选择。

## 开始之前

在开始迁移之前，请确保满足以下条件：

1. 在`app/etc/env.php`中查看您当前的RabbitMQ配置。
1. 对数据库和代码库进行完整备份。
1. 确保您的安装符合ActiveMQ的系统要求。
1. 规划一个维护窗口以完成迁移。

## 迁移路径

迁移到ActiveMQ是一个简单的过程，但务必要确保在切换代理之前处理所有待处理消息。

这些迁移指令假设Adobe Commerce是唯一利用消息队列代理的应用程序。

### 步骤1：将站点置于维护模式

1. 将站点置于[维护模式](../../installation/tutorials/maintenance-mode.md)：

   ```bash
   bin/magento maintenance:enable
   ```

1. 验证是否启用了维护模式：

   ```bash
   bin/magento maintenance:status
   ```

### 步骤2：检查RabbitMQ消息计数

在继续之前，请验证RabbitMQ中的所有消息均已处理完毕。 使用以下方法之一：

#### 方法A：使用RabbitMQ管理功能板

1. 访问`http://<host>:15672`上的RabbitMQ管理UI
1. 默认凭据： `guest/guest`
1. 导航到&#x200B;**队列**&#x200B;选项卡
1. 验证所有队列是否显示&#x200B;**0条消息**

   ![RabbitMQ管理仪表板](../../assets/upgrade-guide/rabbitmq_mgmt_dashboard.png)

#### 方法B：使用rabbitmqctl命令行

1. 检查所有队列及其消息计数：

   ```bash
   rabbitmqctl list_queues name messages consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl.png" alt="RabbitMQ CLI输出" width="500" />

1. 检查详细的队列信息：

   ```bash
   rabbitmqctl list_queues name messages messages_ready messages_unacknowledged consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl_detailed.png" alt="RabbitMQ CLI详细输出" width="500" />

### 步骤3：处理待处理消息

如果消息在任何队列中处于挂起状态，请在继续之前处理这些消息。

1. 获取可用使用者的列表：

   ```bash
   bin/magento queue:consumers:list
   ```

1. 将使用者作为组或按单个消息队列处理：

   - **将使用者处理为组**

     ```bash
     bin/magento cron:run --group=consumers
     ```

     >[!NOTE]
     >
     >如果cron已在系统中运行，则无需手动运行`bin/magento cron:run --group=consumers`。 相反，使用步骤2中的命令检查消息计数，以验证是否正在处理消息。

   - **处理特定消息队列**

     ```bash
     bin/magento queue:consumers:start <consumer_name> --max-messages=<number>
     ```

     例如，要处理异步操作，请执行以下操作：

     ```bash
     bin/magento queue:consumers:start async.operations.all --max-messages=1000
     ```

     >[!NOTE]
     >
     >`--max-messages`参数限制使用者停止之前要处理的消息数。 根据队列大小调整此值。

   - **监视邮件处理**

     持续检查消息计数，直到所有队列为空：

     ```bash
     # Check every few seconds until 0 messages remain
     watch -n 5 "rabbitmqctl list_queues name messages | grep -v '^Listing' | grep -v '0$'"
     ```

### 步骤4：验证是否处理了所有消息

在继续下一步之前，请确保&#x200B;**所有队列都显示0条消息**。 再次运行步骤2中的验证命令。

>[!WARNING]
>
>如果有任何消息仍未处理，请勿继续执行下一步。 如果在消息仍处于挂起状态时切换代理，则可能会丢失数据。

### 步骤5：停止使用者和cron作业

1. 停止所有正在运行的消息队列使用者：

   ```bash
   # If using supervisor
   supervisorctl stop all
   
   # Or manually kill consumer processes
   pkill -f "queue:consumers:start"
   ```

1. 禁用cron作业：

   ```bash
   bin/magento cron:remove
   ```

1. 验证是否已删除cron作业：

   ```bash
   crontab -l
   ```

### 步骤6：备份当前配置

创建当前配置的备份：

```bash
cp app/etc/env.php app/etc/env.php.backup.rabbitmq
```

### 步骤7：可选地卸载RabbitMQ

如果不再需要RabbitMQ，您可以将其卸载。

### 步骤8：在Adobe Commerce中安装和配置ActiveMQ

要完成ActiveMQ安装和配置任务（如配置STOMP协议和验证连接），请参阅[安装和配置指南](../../installation/prerequisites/activemq.md)。

### 步骤9：重新安装cron作业

1. 测试成功完成后，重新安装cron作业：

   ```bash
   bin/magento cron:install
   ```

1. 验证是否已计划cron作业：

   ```bash
   crontab -l
   ```

### 步骤10：禁用维护模式

1. 验证所有组件均正确工作后，禁用维护模式：

   ```bash
   bin/magento maintenance:disable
   ```

1. 验证维护模式是否已禁用：

   ```bash
   bin/magento maintenance:status
   ```

### 步骤11：监视系统

迁移后24-48小时监控您的系统，以确保所有队列操作均正常运行：

- 定期检查ActiveMQ Web控制台的消息吞吐量
- 监控应用程序日志中是否存在与队列相关的错误
- 验证异步操作（配置保存、导出等）是否正常工作
- 检查cron日志，确保使用者正在运行

```bash
# Monitor system logs for queue activity
tail -f var/log/system.log | grep -i queue

# Monitor cron logs
tail -f var/log/cron.log

# Check running consumer processes
ps aux | grep "queue:consumers:start"
```

## 回滚

如果在迁移期间或迁移之后出现问题，您可以回滚到RabbitMQ：

1. 启用维护模式：

   ```bash
   bin/magento maintenance:enable
   ```

1. 停止所有使用者并禁用cron：

   ```bash
   pkill -f "queue:consumers:start"
   bin/magento cron:remove
   ```

1. 恢复以前的配置：

   ```bash
   cp app/etc/env.php.backup.rabbitmq app/etc/env.php
   ```

1. 启动RabbitMQ（如果停止）：

   ```bash
   sudo systemctl start rabbitmq-server
   ```

1. 清除缓存：

   ```bash
   bin/magento cache:flush
   ```

1. 重新安装cron：

   ```bash
   bin/magento cron:install
   ```

1. 禁用维护模式：

   ```bash
   bin/magento maintenance:disable
   ```

完成迁移后，无需进一步更改配置值。

