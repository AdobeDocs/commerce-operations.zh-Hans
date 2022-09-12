---
title: 检查数据库状态
description: 请按照以下步骤检查您的Adobe Commerce或Magento Open Source数据库状态。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 检查数据库状态

运行此命令之前，必须 [创建或更新部署配置](deployment.md).

## 使用命令

检查数据库的状态。

```bash
bin/magento setup:db:status
```

此命令没有参数或选项。

示例输出如下：

```terminal
All modules are up to date.
```

该命令会返回以下退出代码之一：

| 退出代码 | 描述 | 建议的操作 |
|--------------|--------------|---------------|
| 0 | 正常 | 无 |
| 1 | 某些模块使用比数据库更新或更早的代码版本 | 运行 [`magento setup:upgrade`](database-upgrade.md) 更新数据库模式并运行 `composer update` 从应用程序根目录更新组件依赖项 |
| 2 | `magento setup:upgrade` 必需 | [`magento setup:upgrade`](database-upgrade.md) 更新 [数据库模式](https://glossary.magento.com/database-schema) |
