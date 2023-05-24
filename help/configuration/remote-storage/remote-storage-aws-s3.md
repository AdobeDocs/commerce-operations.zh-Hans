---
title: 为远程存储配置AWS S3存储段
description: 将Commerce项目配置为使用AWS S3存储服务进行远程存储。
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# 为远程存储配置AWS S3存储段

此 [Amazon Simple Storage Service (Amazon S3)][AWS S3] 是一种对象存储服务，它提供了业界领先的可扩展性、数据可用性、安全性和性能。 AWS S3服务使用存储桶或容器存储数据。 此配置要求您创建 _私有_ 桶。 有关云基础架构上的Adobe Commerce，请参阅 [在云基础架构上为Commerce配置远程存储](cloud-support.md).

>[!WARNING]
>
>Adobe强烈建议不要使用公共存储桶，因为它会带来严重的安全风险。

**使用AWS S3适配器启用远程存储**：

1. 登录到Amazon S3仪表板并创建 _私有_ 桶。

1. 设置 [AWS IAM] 角色。 或者，生成访问密钥和密钥。

1. 禁用默认数据库存储。

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. 配置Commerce以使用专用存储桶。 参见 [远程存储选项](remote-storage.md#remote-storage-options) 以获取完整的参数列表。

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. 将媒体文件与远程存储同步。

   ```bash
   bin/magento remote-storage:sync
   ```

## 配置Nginx

Nginx需要其他配置才能使用 `proxy_pass` 指令。 将以下代理信息添加到 `nginx.conf` 文件：

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

### 身份验证

如果您使用访问密钥和密钥，而不是 [AWS IAM] 角色，则必须包含 [`ngx_aws_auth` Nginx模块][ngx repo].

### 权限

S3集成依赖于在本地文件系统上生成和存储缓存图像的功能。 因此，的文件夹权限 `pub/media` S3和类似的目录在使用本地存储时是相同的。

### 文件操作

强烈建议您使用 [!DNL Commerce] 无论文件存储类型如何，编码或扩展开发中的文件适配器方法。 使用S3进行存储时，请勿使用本机PHP文件I/O操作，例如 `copy`， `rename`，或 `file_put_contents`，因为S3文件不在文件系统中。 参见 [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) 以了解代码示例。

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
