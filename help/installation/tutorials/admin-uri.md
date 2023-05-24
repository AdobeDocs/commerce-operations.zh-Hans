---
title: 显示或更改管理员URI
description: 按照以下步骤查看和修改Adobe Commerce或Magento Open Source管理应用程序的URI。
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# 显示或更改管理员URI

在运行此命令之前，必须 [创建或更新部署配置](deployment.md).

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
