---
title: 顯示或變更管理員URI
description: 請依照下列步驟檢視和修改Adobe Commerce或Magento Open Source管理員應用程式的URI。
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# 顯示或變更管理員URI

在執行這個命令之前，您必須 [建立或更新部署設定](deployment.md).

## 顯示管理員URI

本節討論如何使用命令列來顯示管理員統一資源識別碼([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2))。

命令選項：

```bash
bin/magento info:adminuri
```

範例結果如下：

```terminal
Admin Panel URI: /admin_1wgrah
```

您也可以檢視管理員URI，位置如下： `<magento_root>/app/etc/env.php`. 以下是程式碼片段：

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## 變更管理員URL

若要變更管理員URI，請使用 [`magento setup:config:set`](deployment.md) 命令。
