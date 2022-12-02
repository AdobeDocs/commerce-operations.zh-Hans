---
title: 云基础架构上的商务远程存储
description: 请参阅有关如何在云基础架构上为Adobe Commerce设置远程存储的指南。
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 在云基础架构上为Commerce配置远程存储

如果您选择将远程存储解决方案与云基础架构上的Adobe Commerce项目结合使用，请使用 [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) 指南 _Fastly_ 文档，以确保Fastly Image Optimization能够与AWS S3配合使用。

准备好 [Fastly凭据](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). 在Pro项目中，使用SSH连接到服务器并从 `/mnt/shared/fastly_tokens.txt` 文件。 暂存环境和生产环境具有唯一的凭据。 您必须获取每个环境的凭据。

通过以下任务，继续为云项目设置远程存储：

1. 配置 [Fastly后端集成](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. 为创建VCL逻辑 [AWS S3身份验证](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. 为创建VCL逻辑 [后端对AWS S3存储段的请求](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
