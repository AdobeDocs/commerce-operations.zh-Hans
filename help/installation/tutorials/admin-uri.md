---
title: 显示或更改管理员URI
description: 按照以下步骤查看和修改Adobe Commerce或Magento Open Source管理应用程序的URI。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# 显示或更改管理员URI

运行此命令之前，必须 [创建或更新部署配置](deployment.md).

## 显示管理员URI

本节讨论如何使用命令行来显示 [管理员](https://glossary.magento.com/admin) 统一资源标识符([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2))。

命令选项：

```bash
bin/magento info:adminuri
```

示例结果如下：

```terminal
Admin Panel URI: /admin_1wgrah
```

您还可以在 `<magento_root>/app/etc/env.php`. 以下是一个代码片段：

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## 更改管理员URL

要更改管理员URI，请使用 [`magento setup:config:set`](deployment.md) 命令。