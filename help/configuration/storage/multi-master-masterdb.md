---
title: 自动配置主控的数据库
description: 请参阅关于自动配置拆分数据库解决方案的指南。
recommendations: noCatalog
exl-id: a27ad097-de60-4cdd-81f9-eb1ae84587e4
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# 自动配置主控的数据库

{{ee-only}}

{{deprecate-split-db}}

本主题讨论如何通过以下方式开始使用拆分数据库解决方案：

1. 使用单个主控数据库安装Adobe Commerce（已命名） `magento`)
1. 为签出和OMS创建另外两个主控数据库(已命名 `magento_quote` 和 `magento_sales`)
1. 配置Adobe Commerce以使用结帐和销售数据库

>[!INFO]
>
>本指南假定所有三个数据库都与Commerce应用程序位于同一主机上，并且它们已命名 `magento`， `magento_quote`、和 `magento_sales`. 但是，如何定位数据库以及数据库名称由您来决定。 我们希望我们的示例使说明更易于遵循。

## 安装Adobe Commerce软件

您可以在安装Adobe Commerce软件后随时启用拆分数据库；换句话说，您可以将拆分数据库添加到已具有结帐和订购数据的Adobe Commerce系统中。 按照Adobe Commerce自述文件中的说明或 [安装指南](../../installation/overview.md) 使用单个主控数据库安装Adobe Commerce软件。

## 设置其他主控数据库

按如下方式创建签出和OMS主控的数据库：

1. 以任意用户身份登录到数据库服务器。
1. 输入以下命令以进入MySQL命令提示符：

   ```bash
   mysql -u root -p
   ```

1. 输入MySQL `root` 提示时的用户密码。
1. 按照显示的顺序输入以下命令，以创建名为的数据库实例 `magento_quote` 和 `magento_sales` 用户名和密码相同：

   ```shell
   create database magento_quote;
   ```

   ```shell
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   ```

   ```shell
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. 输入 `exit` 退出命令提示符。

1. 逐个验证数据库：

   签出数据库：

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   订单管理系统数据库：

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   如果显示MySQL监视器，则表示您正确创建了数据库。 如果显示错误，请重复上述命令。

## 配置Commerce以使用主控的数据库

在设置总共三个主控的数据库后，使用命令行将Commerce配置为使用它们。 (该命令设置数据库连接并在主控的数据库之间分发表。)

### 首要步骤

参见 [正在运行命令](../cli/config-cli.md#running-commands) 登录并运行CLI命令。

### 配置签出数据库

命令语法：

```bash
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

例如，

```bash
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

将显示以下消息以确认设置成功：

```terminal
Migration has been finished successfully!
```

### 配置OMS数据库

命令语法：

```bash
bin/magento setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

例如，

```bash
bin/magento setup:db-schema:split-sales --host="localhost" --dbname="magento_sales" --username="magento_sales" --password="magento_sales"
```

```bash
bin/magento setup:upgrade
```

将显示以下消息以确认设置成功：

```terminal
Migration has been finished successfully!
```
