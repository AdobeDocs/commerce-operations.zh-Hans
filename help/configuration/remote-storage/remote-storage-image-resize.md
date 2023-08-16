---
title: 为远程存储配置图像大小调整
description: 通过配置服务器端映像调整大小来优化磁盘资源。
feature: Configuration, Storage
exl-id: 51c2b9b3-0f5f-4868-9191-911d5df341ec
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 1%

---

# 为远程存储配置图像大小调整

默认情况下，Adobe Commerce支持在应用程序端调整图像大小。 但是，通过启用“远程存储”模块，您可以使用Nginx将调整映像大小的功能卸载到服务器端，从而节省磁盘资源并优化磁盘使用。

下图显示了Nginx如何在缓存中检索、调整大小和存储图像。 调整大小取决于URL中包含的参数，如高度和宽度。

![调整图像大小](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>有关云基础架构项目的Adobe Commerce，请参阅 [在云基础架构上为Commerce配置远程存储](cloud-support.md)

## 在Adobe Commerce中配置URL格式

要调整服务器端图像的大小，必须配置Adobe Commerce以提供图像的高度、宽度和位置(URL)参数。

**配置Commerce以调整服务器端图像大小**：

1. 在 _管理员_ 面板，单击 **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. 在右窗格中，展开 **[!UICONTROL Url options]**.

1. 在 _目录媒体URL格式_ 部分，清除 **[!UICONTROL Use system value]**.

1. 选择 `Image optimization based on query parameters` 中的URL **_目录媒体URL格式_** 字段。

1. 单击 **[!UICONTROL Save Config]**.

1. 继续访问 [恩金克斯配置](#configure-nginx).

## 配置Nginx

要继续配置服务器端图像大小调整，您必须准备 `nginx.conf` 文件并提供 `proxy_pass` 所选适配器的值。

**启用Nginx调整图像大小**：

1. 安装 [Nginx图像滤镜模块][nginx-module].

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. 创建 `nginx.conf` 基于所包含模板的文件 `nginx.conf.sample` 文件。 例如：

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

1. [_可选_] 配置 `proxy_pass` 特定适配器的值。

   - [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html
