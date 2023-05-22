---
title: 設定遠端儲存
description: 瞭解如何為內部部署Commerce應用程式設定遠端儲存模組。
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# 設定遠端儲存

「遠端儲存」模組提供選項，讓您使用儲存服務(例如AWS S3)在永久性的遠端儲存容器中儲存媒體檔案及排程匯入和匯出。 依預設，Adobe Commerce應用程式會將媒體檔案儲存在包含應用程式的相同檔案系統中。 這對於複雜的多伺服器設定而言效率很低，並可能導致共用資源時效能降低。 使用遠端儲存模組，您可以將媒體檔案儲存在 `pub/media` 目錄和匯入/匯出檔案 `var` 遠端物件儲存的目錄，以利用伺服器端影像調整大小的功能。

>[!INFO]
>
>遠端儲存僅適用於Commerce 2.4.2版及更新版本。 請參閱 [2.4.2發行說明](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).

>[!INFO]
>
>遠端儲存模組具有 _受限_ 在雲端基礎結構上支援Adobe Commerce。 Adobe無法完全疑難排解協力廠商儲存配接卡服務。 另請參閱 [在雲端基礎結構上設定Commerce的遠端儲存](cloud-support.md) 以取得為雲端專案實作遠端儲存裝置的指南。

![結構描述影像](../../assets/configuration/remote-storage-schema.png)

## 遠端儲存選項

您可以使用 `remote-storage` 選項搭配 [`setup` CLI命令](../../installation/tutorials/deployment.md). 此 `remote-storage` option會使用以下語法：

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

此 `parameter-name` 是指特定的遠端儲存體引數名稱。 下表列出可用於設定遠端儲存的引數：

| 命令列引數 | 引數名稱 | 說明 | 預設值 |
|--- |--- |--- |--- |
| `remote-storage-driver` | 驅動程式 | 介面卡名稱<br>可能的值：<br>**檔案**：停用遠端儲存並使用本機檔案系統&#x200B;<br>**aws-s3**：使用 [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md) | 無 |
| `remote-storage-bucket` | 貯體 | 物件儲存空間或容器名稱 | 無 |
| `remote-storage-prefix` | 前置詞 | 選擇性首碼（物件儲存體內的位置） | 空白 |
| `remote-storage-region` | 區域 | 區域名稱 | 無 |
| `remote-storage-key` | 存取金鑰 | 選擇性存取金鑰 | 空白 |
| `remote-storage-secret` | 秘密金鑰 | 選擇性秘密金鑰 | 空白 |

### 儲存配接卡

預設儲存位置在本機檔案系統中。 A _儲存配接卡_ 可讓您連線至儲存服務，並將您的檔案存放於任何地方。 [!DNL Commerce] 支援設定下列儲存服務：

- [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

## 啟用遠端儲存

您可以在Adobe Commerce安裝期間安裝遠端儲存體，或將遠端儲存體新增至現有的Commerce執行個體。 下列範例示範使用一組的每種方法 `remote-storage` 引數和Commerce `setup` CLI命令。 至少您必須提供儲存空間 `driver`， `bucket`、和 `region`.

- 範例：使用遠端儲存體安裝Commerce

   ```bash
   bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

- 範例：在現有商務上啟用遠端儲存

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

>[!TIP]
>
>如需雲端基礎結構上的Adobe Commerce，請參閱 [在雲端基礎結構上設定Commerce的遠端儲存](cloud-support.md).

## 限制

您無法同時啟用遠端儲存裝置和資料庫儲存裝置。 如果您使用遠端儲存，請停用資料庫儲存。

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

啟用遠端儲存可能會影響您既定的開發體驗。 例如，某些PHP檔案函式可能無法如預期運作。 必須強制使用Commerce Framework進行檔案作業。

禁止的PHP原生函式清單可在 [magento-coding-standard存放庫][code-standard].

## 移轉內容

為特定介面卡啟用遠端儲存後，您可以使用CLI移轉現有的 _媒體_ 檔案至遠端儲存空間。

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>sync指令只會移轉 `pub/media` 目錄， _not_ 匯入/匯出檔案於 `var` 目錄。 另請參閱 [排定的匯入/匯出][import-export] 在 _Commerce 2.4使用手冊_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
[code-standard]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php
