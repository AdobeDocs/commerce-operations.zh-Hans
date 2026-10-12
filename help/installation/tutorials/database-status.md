---
title: 检查数据库状态
description: 按照以下步骤检查Adobe Commerce数据库状态。
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '104'
ht-degree: 3%
---
# 检查数据库状态

运行此命令之前，必须[创建或更新部署配置](deployment.md)。

## 命令用法

检查数据库的状态。

```shell
bin/magento setup:db:status
```

此命令没有参数或选项。

示例输出如下：

```text
All modules are up to date.
```

该命令返回以下退出代码之一：

| 退出代码 | 描述 | 建议的操作 |
|--------------|--------------|---------------|
| 0 | 普通 | 无 |
| 1 | 某些模块使用比数据库更新或更旧的代码版本 | 运行[`magento setup:upgrade`](database-upgrade.md)以更新数据库架构，并从应用程序根目录中运行`composer update`以更新组件依赖项 |
| 2 | `magento setup:upgrade`为必填项 | [`magento setup:upgrade`](database-upgrade.md)以更新数据库架构 |
