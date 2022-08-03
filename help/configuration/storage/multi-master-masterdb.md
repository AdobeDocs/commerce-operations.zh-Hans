---
title: 自动配置主控数据库
description: 请参阅有关自动配置拆分数据库解决方案的指南。
source-git-commit: 52f92ef79586d618fd4ac51c00eaa1446a2dc98f
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 1%

---


# 自动配置主控数据库

{{ee-only}}

{{deprecate-split-db}}

本主题讨论如何通过以下方式开始使用拆分数据库解决方案：

1. 使用单个主控数据库安装Adobe Commerce(名为 `magento`)
1. 为创建另外两个主控数据库 [结账](https://glossary.magento.com/checkout) 和OMS(已命名 `magento_quote` 和 `magento_sales`)
1. 配置Adobe Commerce以使用结帐和销售数据库

>[!INFO]
>
>本指南假定所有三个数据库都与Commerce应用程序位于同一台主机上，并且它们名为 `magento`, `magento_quote`和 `magento_sales`. 但是，数据库的位置及其名称的选择取决于您。 我们希望这些示例能够更方便地遵循相关说明。

## 安装Adobe Commerce软件

安装Adobe Commerce软件后，您可以随时启用拆分数据库；换言之，您可以将拆分数据库添加到已具有结帐和订购数据的Adobe Commerce系统。 使用Adobe Commerce README或 [安装指南](https://devdocs.magento.com/guides/v2.4/install-gde/bk-install-guide.html) 使用单个主控数据库安装Adobe Commerce软件。

## 设置其他主控数据库

按如下方式创建结帐和OMS主控数据库：

1. 以任何用户身份登录数据库服务器。
1. 输入以下命令以转到MySQL命令提示符：

   ```bash
   mysql -u root -p
   ```

1. 输入MySQL `root` 用户的密码。
1. 按照创建名为的数据库实例的顺序输入以下命令 `magento_quote` 和 `magento_sales` 使用相同的用户名和密码：

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

1. 每次验证一个数据库：

   结帐数据库：

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

   如果显示MySQL监视器，则表示您已正确创建了数据库。 如果显示错误，请重复上述命令。

## 配置Commerce以使用主控数据库

在设置了总共三个主控数据库之后，使用命令行配置Commerce以使用它们。 (该命令设置数据库连接并在主控数据库之间分发表。)

### 首要步骤

请参阅 [运行命令](../cli/config-cli.md#running-commands) 登录并运行CLI命令。

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

将显示以下消息以确认设置成功：

```terminal
Migration has been finished successfully!
```
