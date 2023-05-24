---
title: 云基础架构上的Commerce远程存储
description: 请参阅有关如何为云基础架构上的Adobe Commerce设置远程存储的指南。
feature: Configuration, Cloud, Storage
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# 在云基础架构上为Commerce配置远程存储

从 `ece-tools` 软件包2002.1.5中，可以使用环境变量来启用远程存储模块；但是，远程存储模块具有 _有限_ 在云基础架构上支持Adobe Commerce。 Adobe无法完全排除第三方存储适配器服务的故障。

## 环境变量

此 `REMOTE_STORAGE` 变量用在 [部署阶段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) 云基础架构项目的ID。

### `REMOTE_STORAGE`

- **默认**—_未设置_
- **版本**—Commerce 2.4.2及更高版本

配置 _存储适配器_ 使用存储服务(如AWS S3)将媒体文件存储在一个永久性的远程存储容器中。 启用远程存储模块以提高云项目的性能，这些项目具有必须共享资源的复杂、多服务器配置。 以下是使用 `.magento.env.yaml` 文件：

```yaml
stage:
  deploy:
    REMOTE_STORAGE:
      driver: aws-s3 # Required
      prefix: cloud # Optional
      config:
        bucket: my-bucket # Required
        region: my-region # Required
        key: my-key # Optional
        secret: my-secret-key # Optional
```

### 使用Cloud CLI设置变量

设置 `REMOTE_STORAGE` 变量作为 [环境级变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) 这样就不会在生产、暂存和集成环境之间共享文件。 通过在环境级别设置变量，可以灵活地在选定的环境中仅使用远程存储，例如排除集成环境使用远程存储。

**使用云CLI添加远程存储变量**：

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

这将创建 `REMOTE_STORAGE` 变量填充文件路径。 此 `REMOTE_STORAGE` 变量使用JSON字符串来配置远程存储。 以下是JSON配置示例：

```json
{
  "driver": "aws-s3",
  "prefix": "uat",
  "config": {
    "bucket": "aws-bucket-id",
    "region": "aws-region-id",
    "key": "optional-key",
    "secret": "optional-secret"
  }
}
```

在创建配置和部署后，部署日志应包含有关远程存储配置的信息，例如 `INFO: Remote storage driver set to: "aws-s3"`

### 使用Project Web Interface设置变量

或者，您可以使用Project Web Interface将变量添加到适当的环境中。

**使用Project Web界面添加远程存储变量**：

1. 在 _Project Web界面_，从左侧选择环境。

1. 单击 **配置环境** 图标。

1. 在 _配置环境_ 视图，单击 **变量** 选项卡。

1. 单击 **添加变量**.

1. 在 _名称_ 字段，输入 `REMOTE_STORAGE`

1. 在 _值_ 字段中，添加JSON配置。

1. 选择 **JSON值** 和 **敏感**；取消选择 **可按子环境继承**.

1. 单击 **添加变量**.

### 使用可选身份验证

此 `key` 和 `secret` 是可选的。 创建变量时，您可以隐藏 `key` 和 `secret` 通过选择 `sensitive` 选项。 使用此设置时，值在Web界面中不可见。 参见 [变量可见性](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) 在 _云基础架构上的Commerce指南_.

如果要使用其他身份验证方法，请忽略 `key` 和 `secret` 从JSON配置中， 。 配置替代身份验证方法，并确认服务器已获得对S3存储段的授权。

### 同步远程存储

启用远程存储模块后，将当前媒体文件同步到远程存储位置。

**启动同步**：

1. 使用SSH登录到配置了远程存储的远程环境。

1. 启动同步。

```bash
bin/magento remote-storage:sync 
```

## Fastly配置

如果您选择将远程存储解决方案与Adobe Commerce on cloud infrastructure项目一起使用，请使用 [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) 中的指南 _Fastly_ 文档，以确保Fastly图像优化可与AWS S3配合使用。

做好准备 [Fastly凭据](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). 在Pro项目中，使用SSH连接到您的服务器并从 `/mnt/shared/fastly_tokens.txt` 文件。 暂存环境和生产环境具有独特的凭据。 您必须获取每个环境的凭据。

通过执行以下任务，继续为云项目设置远程存储：

1. 配置 [Fastly后端集成](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. 为创建VCL逻辑 [AWS S3身份验证](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. 为创建VCL逻辑 [对AWS S3存储桶的后端请求](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
