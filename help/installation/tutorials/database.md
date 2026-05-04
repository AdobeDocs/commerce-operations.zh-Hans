---
title: 创建数据库模式
description: 按照以下步骤为Adobe Commerce项目创建数据库。
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# 创建数据库模式

运行此命令之前，必须[创建或更新部署配置](deployment.md)。

## 配置数据库并添加数据

命令用法：

```shell
bin/magento setup:db-schema:upgrade
```

要查看数据库的状态，请输入

```shell
bin/magento setup:db:status
```
