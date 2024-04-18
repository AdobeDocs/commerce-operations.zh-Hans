---
title: 检查数据库状态
description: 按照以下步骤检查Adobe Commerce数据库状态。
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 3%

---

# 检查数据库状态

运行此命令之前，必须 [创建或更新部署配置](deployment.md).

## 命令用法

检查数据库的状态。

```bash
bin/magento setup:db:status
```

此命令没有参数或选项。

示例输出如下：

```terminal
All modules are up to date.
```

该命令返回以下退出代码之一：

| 退出代码 | 描述 | 建议的操作 |
|--------------|--------------|---------------|
| 0 | 普通 | 无 |
| 1 | 某些模块使用比数据库更新或更旧的代码版本 | 运行 [`magento setup:upgrade`](database-upgrade.md) 更新数据库模式并运行 `composer update` 从应用程序根目录更新组件依赖关系 |
| 2 | `magento setup:upgrade` 为必填项 | [`magento setup:upgrade`](database-upgrade.md) 更新数据库模式 |
