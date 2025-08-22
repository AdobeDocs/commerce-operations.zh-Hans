---
title: 升级基于Git的安装
description: 升级您从Git存储库克隆的Adobe Commerce安装。
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# 升级基于Git的安装

本主题将讨论参与开发的开发人员如何更新Adobe Commerce而不重新安装它。 如果您不是参与开发人员，请参阅[执行升级](../implementation/perform-upgrade.md)。

要升级（如果您是参与开发人员），请执行以下操作：

{{$include /help/_includes/server-login.md}}

1. 保存您对`composer.json`文件所做的任何更改，因为后续步骤将覆盖该文件。

1. 创建`composer.json`文件的备份。

   ```bash
   cp composer.json composer.json.old
   ```

1. 更新本地存储库以获取最新代码：

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >如果`git pull origin develop`失败，请参阅[疑难解答](https://support.magento.com/hc/en-us/articles/360034229872)。

1. 比较您的`composer.json.old`文件并将其与`composer.json`文件合并。

1. 解决依赖关系并将精确版本写入`composer.lock`文件。

   ```bash
   composer update
   ```

1. 更新数据库：

   ```bash
   bin/magento setup:upgrade
   ```

1. 清理缓存：

   ```bash
   bin/magento cache:clean
   ```

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
