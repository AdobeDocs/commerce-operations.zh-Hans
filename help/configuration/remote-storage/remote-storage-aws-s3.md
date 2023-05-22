---
title: 設定遠端儲存的AWS S3貯體
description: 設定您的Commerce專案以使用AWS S3儲存服務進行遠端儲存。
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# 設定遠端儲存的AWS S3貯體

此 [Amazon Simple Storage Service (Amazon S3)][AWS S3] 是物件儲存服務，提供領先業界的可擴充性、資料可用性、安全性及效能。 AWS S3服務使用貯體或容器來儲存資料。 此設定需要您建立 _私人_ 貯體。 如需雲端基礎結構上的Adobe Commerce，請參閱 [在雲端基礎結構上設定Commerce的遠端儲存](cloud-support.md).

>[!WARNING]
>
>Adobe強烈建議不要使用公用儲存貯體，因為它有嚴重的安全風險。

**使用AWS S3配接卡啟用遠端儲存的功能**：

1. 登入您的Amazon S3控制面板並建立 _私人_ 貯體。

1. 設定 [AWS IAM] 角色。 或者，產生存取和秘密金鑰。

1. 停用預設資料庫儲存體。

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. 設定Commerce使用私人貯體。 另請參閱 [遠端儲存選項](remote-storage.md#remote-storage-options) 以取得完整的引數清單。

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. 將媒體檔案與遠端儲存裝置同步。

   ```bash
   bin/magento remote-storage:sync
   ```

## 設定Nginx

Nginx需要額外的設定，才能使用 `proxy_pass` 指令。 將下列Proxy資訊新增至 `nginx.conf` 檔案：

>nginx.conf

```conf
location ~* \.(ico|jpg|jpeg|png|gif|svg|js|css|swf|eot|ttf|otf|woff|woff2)$ {
    # Proxying to AWS S3 storage.
    resolver 8.8.8.8;
    set $bucket "<s3-bucket-name>";
    proxy_pass https://s3.amazonaws.com/$bucket$uri;
    proxy_pass_request_body off;
    proxy_pass_request_headers off;
    proxy_intercept_errors on;
    proxy_hide_header "x-amz-id-2";
    proxy_hide_header "x-amz-request-id";
    proxy_hide_header "x-amz-storage-class";
    proxy_hide_header "Set-Cookie";
    proxy_ignore_headers "Set-Cookie";
}
```

### 驗證

如果您使用存取金鑰和秘密金鑰，而不是 [AWS IAM] 角色，您必須包含 [`ngx_aws_auth` Nginx模組][ngx repo].

### 許可權

S3整合依賴在本機檔案系統上產生和儲存快取影像的能力。 因此，的檔案夾許可權 `pub/media` S3的和類似目錄與使用本機儲存時相同。

### 檔案作業

強烈建議您使用 [!DNL Commerce] 無論檔案儲存型別為何，編碼或擴充功能開發中的檔案配接器方法。 使用S3進行儲存時，請勿使用原生PHP檔案I/O操作，例如 `copy`， `rename`，或 `file_put_contents`，因為S3檔案不在檔案系統內。 另請參閱 [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) 以取得程式碼範例。

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
