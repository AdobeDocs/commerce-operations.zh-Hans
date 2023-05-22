---
title: 自訂記錄
description: 瞭解如何使用自訂記錄來調查錯誤。
feature: Configuration, Logs
exl-id: 6c94ebcf-70df-4818-a17b-32512eba516d
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# 自訂記錄概觀

記錄提供系統程式的可見度；例如，偵錯資訊可協助您瞭解何時發生錯誤或導致錯誤的原因。

雖然Commerce也提供了在資料庫中儲存記錄檔的靈活性，但本主題著重於檔案型記錄。

Adobe建議使用集中式應用程式記錄，原因如下：

- 它允許在應用程式伺服器以外的伺服器上儲存記錄檔，並減少磁碟I/O作業，簡化對應用程式伺服器的支援。

- 它使用特殊工具(例如 [Logstash]， [Logplex]，或 [已流失] — 不影響生產伺服器。

   >[!INFO]
   >
   >Adobe不建議或認可任何特定的記錄解決方案。

## PSR-3合規性

此 [PSR-3標準][laminas] 定義記錄程式庫的通用PHP介面。 PSR-3的主要目標是允許程式庫接收 `Psr\Log\LoggerInterface` 物件並以簡單且通用的方式將記錄寫入其中。

如此一來，實施便可輕鬆更換，不必擔心更換會破壞應用程式程式碼。 此外，即使日後系統版本中的記錄實作有所變更，也能確保自訂元件正常運作。

## 獨白

Commerce 2符合PSR-3標準。 依預設，Commerce會使用 [獨白]. 實作作為偏好設定的獨白 `Psr\Log\LoggerInterface` 在商務應用程式中 [`di.xml`][di].

Monolog是一種常用的PHP記錄解決方案，具有廣泛的處理常式，可讓您建置進階記錄策略。 以下是Monolog運作方式的摘要。

獨白 _logger_ 是擁有自己一套的管道 _處理常式_. Monolog有許多處理常式，包括：

- 記錄至檔案與系統記錄檔
- 傳送警報和電子郵件
- 記錄特定的伺服器和網路記錄
- 登入開發（與FireBug和Chrome Logger等整合）
- 登入資料庫

每個處理常式都可以處理輸入訊息並停止傳輸，或將控制項傳遞至鏈結中的下一個處理常式。

記錄訊息的處理方式有很多種。 例如，您可以將所有除錯資訊儲存在磁碟上的檔案中，將記錄層級較高的訊息放入資料庫中，最後透過電子郵件傳送記錄層級為「嚴重」的訊息。

其他管道可以有不同的處理常式和邏輯集。

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[已流失]: https://www.fluentd.org/
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[獨白]: https://github.com/Seldaek/monolog
