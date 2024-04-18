---
title: 显示或更改管理员URI
description: 按照以下步骤查看和修改Adobe Commerce Admin应用程序的URI。
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# 显示或更改管理员URI

运行此命令之前，必须 [创建或更新部署配置](deployment.md).

## 显示管理员URI

本节讨论如何使用命令行显示管理员统一资源标识符([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2))。

命令选项：

```bash
bin/magento info:adminuri
```

以下是示例结果：

```terminal
Admin Panel URI: /admin_1wgrah
```

您还可以在中查看管理员URI `<magento_root>/app/etc/env.php`. 以下是一个代码片段：

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## 更改管理员URL

要更改管理员URI，请使用 [`magento setup:config:set`](deployment.md) 命令。
