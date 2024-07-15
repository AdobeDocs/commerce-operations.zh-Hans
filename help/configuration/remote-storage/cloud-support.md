---
title: 云基础架构上适用于Commerce的远程存储
description: 请参阅有关如何为云基础架构上的Adobe Commerce设置远程存储的指南。
feature: Configuration, Cloud, Storage
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# 在云基础架构上为Commerce配置远程存储

从`ece-tools`包2002.1.5开始，您可以使用环境变量来启用远程存储模块；但是，在云基础架构上，远程存储模块在Adobe Commerce上具有&#x200B;_有限的_&#x200B;支持。 Adobe无法完全排除第三方storage adapter服务的故障。

## 环境变量

`REMOTE_STORAGE`变量在云基础架构项目的[部署阶段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html)中使用。

### `REMOTE_STORAGE`

- **默认值**—_未设置_
- **版本**—Commerce 2.4.2及更高版本

配置&#x200B;_存储适配器_&#x200B;以使用存储服务(如AWS S3)将媒体文件存储在永久性的远程存储容器中。 启用远程存储模块以提高云项目的性能，这些项目具有必须共享资源的复杂、多服务器配置。 以下是使用`.magento.env.yaml`文件的远程存储配置示例：

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

将`REMOTE_STORAGE`变量设置为[环境级变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html)，以便文件不在生产、暂存和集成环境之间共享。 在环境级别设置变量后，可以灵活地在选定环境中仅使用远程存储，例如排除使用远程存储的集成环境。

**要使用Cloud CLI添加远程存储变量**，请执行以下操作：

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

这会使用指定的JSON配置创建一个`REMOTE_STORAGE`变量。 `REMOTE_STORAGE`变量使用JSON字符串来配置远程存储。 以下是JSON配置示例：

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

在创建配置和部署后，部署日志应包含有关远程存储配置的信息，例如`INFO: Remote storage driver set to: "aws-s3"`

### 使用Project Web界面设置变量

或者，您可以使用Project Web Interface将变量添加到适当的环境中。

**使用Project Web界面添加远程存储变量**：

1. 在&#x200B;_Project Web界面_&#x200B;中，从左侧选择环境。

1. 单击&#x200B;**配置环境**&#x200B;图标。

1. 在&#x200B;_配置环境_&#x200B;视图中，单击&#x200B;**变量**&#x200B;选项卡。

1. 单击&#x200B;**添加变量**。

1. 在&#x200B;_名称_&#x200B;字段中，输入`REMOTE_STORAGE`

1. 在&#x200B;_值_&#x200B;字段中，添加JSON配置。

1. 选择&#x200B;**JSON值**&#x200B;和&#x200B;**敏感**；取消选择&#x200B;**可由子环境继承**。

1. 单击&#x200B;**添加变量**。

### 使用可选身份验证

`key`和`secret`是可选的。 创建变量时，您可以通过选择`sensitive`选项来隐藏`key`和`secret`。 使用此设置，Web界面中不会显示这些值。 请参阅&#x200B;_云基础架构上的Commerce指南_&#x200B;中的[变量可见性](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility)。

如果要使用其他身份验证方法，请从JSON配置中忽略`key`和`secret`。 配置替代身份验证方法，并验证服务器是否有权使用S3存储桶。

### 同步远程存储

启用远程存储模块后，将当前媒体文件同步到远程存储位置。

**要启动同步**：

1. 使用SSH登录到配置了远程存储的远程环境。

1. 启动同步。

```bash
bin/magento remote-storage:sync 
```

## Fastly配置

如果选择将远程存储解决方案与Adobe Commerce on cloud infrastructure项目一起使用，请使用&#x200B;_Fastly_&#x200B;文档中的[Amazon S3](https://docs.fastly.com/en/guides/amazon-s3)指南来确保Fastly图像优化可与AWS S3配合使用。

准备好您的[Fastly凭据](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials)。 在Pro项目中，使用SSH连接到您的服务器并从`/mnt/shared/fastly_tokens.txt`文件中获取Fastly凭据。 暂存环境和生产环境具有唯一的凭据。 您必须获取每个环境的凭据。

请通过以下任务继续为云项目设置远程存储：

1. 配置[Fastly后端集成](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md)。

1. 为[AWS S3身份验证](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket)创建VCL逻辑。

1. 为AWS S3存储桶](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/)的[后端请求创建VCL逻辑。
