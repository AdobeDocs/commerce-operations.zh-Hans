---
title: 还原拆分数据库
description: 从已弃用的拆分数据库实现还原到单个数据库实现。
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%
---
# 从拆分数据库还原

{{ee-only}}

对于已实施[拆分数据库](multi-master.md)的Adobe Commerce客户，以下主题介绍了如何还原或迁移回单个数据库。 我们建议Adobe Commerce商家当前使用拆分数据库，并计划升级到2.4.2及更高版本，然后查看这些步骤。

从拆分数据库还原到单个数据库涉及先创建`magento_quote`和`magento_sales`数据库的备份，然后再将其加载到单个`magento_main`数据库中。

在本例中，我们登录到与“root”用户安装在同一主机(`magento2-mysql`)上的所有三个数据库。 必须将这些值替换为数据库的相应值。

1. 创建`magento_quote`数据库的备份：

   ```shell
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. 创建`magento_sales`数据库的备份：

   ```shell
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. 将`magento_quote`数据库加载到`magento_main`数据库中：

   ```shell
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. 将`magento_sales`数据库加载到`magento_main`数据库中：

   ```shell
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. 删除`magento_sales`数据库：

   ```shell
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. 删除`magento_quote`数据库：

   ```shell
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. 在`env.php`文件的`connections`和`resources`部分中移除`checkout`和`sales`的部署配置。
1. 还原外键：

   ```shell
   bin/magento setup:upgrade
   ```

## 验证您的工作

要验证单个数据库实施是否正常工作，请使用数据库工具（如[phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin)）执行以下任务并验证数据是否已添加到`magento_main`数据库表中：

1. 验证是否已还原外键。 例如，`quote`数据库表中的`QUOTE_STORE_ID_STORE_STORE_ID`键。
1. 确认客户可以从店面下订单。
1. 验证在将拆分数据库还原到单个数据库之前创建的订单在管理员中是否可用。
