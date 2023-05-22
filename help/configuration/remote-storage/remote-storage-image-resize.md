---
title: 設定遠端儲存裝置的影像調整大小
description: 透過設定伺服器端影像大小調整來最佳化磁碟資源。
feature: Configuration, Storage
exl-id: 51c2b9b3-0f5f-4868-9191-911d5df341ec
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# 設定遠端儲存裝置的影像調整大小

依預設，Adobe Commerce支援在應用程式端調整影像大小。 不過，透過啟用「遠端儲存」模組，您可以使用Nginx將影像大小調整解除安裝到伺服器端，藉此節省磁碟資源並最佳化磁碟使用量。

下圖顯示Nginx如何擷取、調整大小及儲存快取中的影像。 調整大小是由URL中包含的引數（例如高度和寬度）所決定。

![調整影像大小](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>如需雲端基礎結構專案的Adobe Commerce，請參閱 [在雲端基礎結構上設定Commerce的遠端儲存](cloud-support.md)

## 在Adobe Commerce中設定URL格式

若要在伺服器端調整影像大小，您必須設定Adobe Commerce以提供影像的高度、寬度和位置(URL)引數。

**若要設定Commerce以調整伺服器端影像大小**：

1. 在 _管理員_ 面板，按一下 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. 在右窗格中，展開 **[!UICONTROL Url options]**.

1. 在 _目錄媒體URL格式_ 部分，清除 **[!UICONTROL Use system value]**.

1. 選取 `Image optimization based on query parameters` 中的URL **_目錄媒體URL格式_** 欄位。

1. 按一下 **[!UICONTROL Save Config]**.

1. 繼續前往 [Nginx設定](#configure-nginx).

## 設定Nginx

若要繼續設定伺服器端影像調整大小，您必須準備 `nginx.conf` 檔案並提供 `proxy_pass` 您所選介面卡的值。

**啟用Nginx調整影像大小的方式**：

1. 安裝 [Nginx影像篩選模組][nginx-module].

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. 建立 `nginx.conf` 根據包含範本的檔案 `nginx.conf.sample` 檔案。 例如：

   ```conf
   location ~* \.(jpg|jpeg|png|gif|webp)$ {
       set $width "-";
       set $height "-";
       if ($arg_width != '') {
           set $width $arg_width;
       }
       if ($arg_height != '') {
           set $height $arg_height;
       }
       image_filter resize $width $height;
       image_filter_jpeg_quality 90;
   }
   ```

1. [_可選_] 設定 `proxy_pass` 您特定介面卡的值。

   - [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html
