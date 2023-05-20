---
title: 啟動訊息佇列消費者
description: 瞭解如何啟動訊息佇列取用者。
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# 啟動訊息佇列消費者

{{file-system-owner}}

您必須啟動 [訊息佇列取用者](../queues/consumers.md) 啟用非同步操作，例如Inventory management大量動作和REST大量和非同步端點。 若要啟用B2B功能，您必須啟動多個消費者。 協力廠商模組可能也需要您啟動自訂消費者。

若要檢視所有消費者的清單：

```bash
bin/magento queue:consumers:list
```

若要啟動訊息佇列取用者：

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

使用所有可用訊息後，該命令即終止。 您可以手動或使用cron工作再次執行此命令。 您也可以執行多個 `magento queue:consumers:start` 處理大型訊息佇列的命令。 例如，您可以附加 `&` 使用命令在背景執行，返回提示字元並繼續執行命令：

```bash
bin/magento queue:consumers:start <consumer_name> &
```

另請參閱 [佇列:consumers:開始](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#queueconsumersstart) 在的Commerce區段中 _命令列工具參考_ 瞭解指令選項、引數和值的詳細資訊。

>[!INFO]
>
>此 `--multi-process` 選項存在於 `queue:consumers:start` 命令，但若要以平行程式執行消費者，請設定 [`multiple_processes`](../queues/manage-message-queues.md#configuration) 中的選項 `/app/etc/env.php`. 否則，如果 `queue:consumers:start` 使用呼叫 `--multi-process` 選項，它僅適用於單一執行緒。
