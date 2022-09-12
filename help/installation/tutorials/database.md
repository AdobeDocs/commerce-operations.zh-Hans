---
title: 创建数据库模式
description: 按照以下步骤为您的Adobe Commerce或Magento Open Source创建数据库。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# 创建数据库模式

运行此命令之前，必须 [创建或更新部署配置](deployment.md).

## 配置数据库并添加数据

命令用法：

```bash
bin/magento setup:db-schema:upgrade
```

要查看数据库的状态，请输入

```bash
bin/magento setup:db:status
```
