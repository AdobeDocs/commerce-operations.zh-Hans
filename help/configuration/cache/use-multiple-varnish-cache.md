---
title: 使用多個Varnish例項清除快取
description: 瞭解快取清除如何與多個Varnish執行個體搭配運作。
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# 快取清除多個Varnish例項

Adobe Commerce和Magento Open Source支援多個立即可用的清漆執行個體。

本主題說明使用Commerce設定多個Varnish執行個體的基本知識。

## 清除多個Varnish例項的設定

使用設定清漆主機後，Commerce會清除清漆主機 [`magento setup:config:set`](../../installation/tutorials/deployment.md) 命令。

您應使用 `--http-cache-hosts` 引數，用來指定清漆主機和接聽連線埠的逗號分隔清單。 （請勿以空格字元分隔主機。）

引數格式必須是 `<hostname or ip>:<listen port>`，您可在此省略 `<listen port>` 如果是連線埠80。

例如，

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

當您重新整理Commerce快取時，可以清除所有Varnish主機(也稱為 _清理_ （例如快取）或使用命令列。

若要使用管理員重新整理快取，請按一下 **系統** >工具> **快取管理**，然後按一下 **排清Magento快取** ，位於頁面頂端。 （您也可以重新整理個別快取型別。）

若要從cli重新整理多個Varnish執行個體的快取，請使用 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) 命令作為 [檔案系統擁有者](../../installation/prerequisites/file-system/overview.md).
