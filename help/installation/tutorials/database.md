---
title: 建立資料庫綱要
description: 請依照下列步驟，為您的Adobe Commerce或Magento Open Source建立資料庫。
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---

# 建立資料庫綱要

在執行這個命令之前，您必須 [建立或更新部署設定](deployment.md).

## 設定資料庫並新增資料

命令使用方式：

```bash
bin/magento setup:db-schema:upgrade
```

若要檢視資料庫的狀態，請輸入

```bash
bin/magento setup:db:status
```
