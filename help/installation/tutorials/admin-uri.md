---
title: 显示或更改管理员URI
description: 按照以下步骤查看和修改Adobe Commerce Admin应用程序的URI。
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
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
source-wordcount: '99'
ht-degree: 0%
---
# 显示或更改管理员URI

运行此命令之前，必须[创建或更新部署配置](deployment.md)。

## 显示管理员URI

本节讨论如何使用命令行显示管理员统一资源标识符([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2))。

命令选项：

```shell
bin/magento info:adminuri
```

以下是示例结果：

```text
Admin Panel URI: /admin_1wgrah
```

您还可以在`<magento_root>/app/etc/env.php`中查看管理员URI。 以下是一个代码片段：

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## 更改管理员URL

要更改管理员URI，请使用[`magento setup:config:set`](deployment.md)命令。
