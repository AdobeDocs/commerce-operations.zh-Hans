---
title: 为远程存储配置图像大小调整
description: 通过配置服务器端映像调整大小来优化磁盘资源。
feature: Configuration, Storage
exl-id: 51c2b9b3-0f5f-4868-9191-911d5df341ec
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# 为远程存储配置图像大小调整

默认情况下，Adobe Commerce支持在应用程序端调整图像大小。 但是，通过启用“远程存储”模块，您可以使用Nginx将调整映像大小的功能卸载到服务器端，从而节省磁盘资源并优化磁盘使用。

下图显示了Nginx如何在缓存中检索、调整大小和存储图像。 调整大小取决于URL中包含的参数，如高度和宽度。

![用于远程存储映像调整大小的Nginx配置显示服务器块设置](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>有关云基础架构项目上的Adobe Commerce，请参阅[为云基础架构上的Commerce配置远程存储](cloud-support.md)

## 在Adobe Commerce中配置URL格式

要调整服务器端图像的大小，必须配置Adobe Commerce以提供图像的高度、宽度和位置(URL)参数。

**要配置Commerce以调整服务器端图像大小**：

1. 在&#x200B;_管理员_&#x200B;面板中，单击&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**。

1. 在右窗格中，展开&#x200B;**[!UICONTROL Url options]**。

1. 在&#x200B;_目录媒体URL格式_&#x200B;部分中，清除&#x200B;**[!UICONTROL Use system value]**。

1. 在`Image optimization based on query parameters`目录媒体URL格式&#x200B;**_字段中选择_** URL。

1. 单击&#x200B;**[!UICONTROL Save Config]**。

1. 继续到[Nginx配置](#configure-nginx)。

## 配置Nginx

要继续配置服务器端图像大小调整，您必须准备`nginx.conf`文件并为您选择的适配器提供`proxy_pass`值。

**要允许Nginx调整图像大小**：

1. 安装[Nginx映像筛选器模块][nginx-module]。

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. 基于包含的模板`nginx.conf`文件创建一个`nginx.conf.sample`文件。 例如：

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

1. [_可选_]&#x200B;为特定适配器配置`proxy_pass`值。

   - [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html
