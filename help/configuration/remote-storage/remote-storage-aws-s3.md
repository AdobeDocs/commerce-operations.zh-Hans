---
title: 为远程存储配置AWS S3存储段
description: 将您的Commerce项目配置为使用AWS S3存储服务进行远程存储。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# 为远程存储配置AWS S3存储段

的 [Amazon Simple Storage Service(Amazon S3)][AWS S3] 是一项对象存储服务，可提供业界领先的可扩展性、数据可用性、安全性和性能。 AWS S3服务使用存储段或容器进行数据存储。 此配置要求您创建 _私人_ 存储段。

>[!WARNING]
>
>Adobe极不鼓励使用公共存款，因为这会带来严重的安全风险。

**使用AWS S3适配器启用远程存储**:

1. 登录到Amazon S3功能板，并创建 _私人_ 存储段。

1. 设置 [AWS IAM] 角色。 或者，生成访问密钥和密钥。

1. 禁用默认数据库存储。

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. 配置商务以使用专用存储段。 请参阅 [远程存储选项](remote-storage.md#remote-storage-options) ，以获取参数的完整列表。

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
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

S3集成依赖于在本地文件系统上生成和存储缓存图像的功能；因此，文件夹的权限 `pub/media` S3的类似目录与使用本地存储时的目录相同。

### 文件操作

强烈建议您使用 [!DNL Commerce] 在编码或扩展开发中使用文件适配器方法，而不考虑文件存储类型。 使用S3进行存储时，请勿使用本机PHP文件I/O操作，例如 `copy`, `rename` 或 `file_put_contents`，因为S3文件不在文件系统中。 请参阅 [DriverInterface.php] ，以了解代码示例。

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
[DriverInterface.php]: https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18