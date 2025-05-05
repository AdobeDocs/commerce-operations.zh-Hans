---
title: 配置远程存储
description: 了解如何为本地Commerce应用程序配置远程存储模块。
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 419a21604d1fda0a76dd0375ae2340fd6e59ec89
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# 配置远程存储

“远程存储”模块提供了使用存储服务(如AWS S3)将媒体文件存储到永久性的远程存储容器中并安排导入和导出的选项。

默认情况下，Adobe Commerce应用程序会将媒体文件存储在包含该应用程序的同一文件系统中。 这对于复杂的多服务器配置而言效率低下，并可能导致在共享资源时性能降低。 使用远程存储模块，您可以将媒体文件存储在`pub/media`目录中，并将文件导入/导出到远程对象存储的`var`目录中，以利用服务器端映像大小调整功能。

>[!BEGINSHADEBOX]

不能同时启用远程存储&#x200B;_和_&#x200B;数据库存储。 在启用远程存储之前，必须禁用数据库存储。

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

启用远程存储可能会影响您既定的开发体验。 例如，某些PHP文件函数可能无法按预期工作。 必须强制使用Commerce Framework进行文件操作。 禁止的PHP本机函数列表可在[magento-coding-standard](https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php)存储库中找到。

>[!ENDSHADEBOX]

>[!INFO]
>
>- 远程存储仅适用于Commerce版本2.4.2及更高版本。 请参阅[2.4.2发行说明](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/release/notes/magento-open-source/2-4-2)。
>
>- 在云基础架构上的Adobe Commerce上，远程存储模块具有&#x200B;_有限的_&#x200B;支持。 Adobe无法完全排除第三方storage adapter服务的故障。 有关为云项目实施远程存储的指导，请参阅[在云基础架构上为Commerce配置远程存储](cloud-support.md)。

![架构图像](../../assets/configuration/remote-storage-schema.png)

## 远程存储选项

您可以使用`remote-storage`选项和[`setup` CLI命令](../../installation/tutorials/deployment.md)来配置远程存储。 `remote-storage`选项使用以下语法：

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

`parameter-name`引用特定的远程存储参数名称。 下表列出了可用于配置远程存储的参数：

| 命令行参数 | 参数名称 | 描述 | 默认值 |
|--- |--- |--- |--- |
| `remote-storage-driver` | 驱动因素 | 适配器名称<br>可能的值： <br>**文件**：禁用远程存储并使用本地文件系统&#x200B;<br>**aws-s3**：使用[Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md) | 无 |
| `remote-storage-bucket` | 分段 | 对象存储或容器名称 | 无 |
| `remote-storage-prefix` | 前缀 | 可选前缀（对象存储内的位置） | 空 |
| `remote-storage-region` | 区域 | 区域名称 | 无 |
| `remote-storage-key` | 访问密钥 | 可选访问密钥 | 空 |
| `remote-storage-secret` | 密钥 | 可选密钥 | 空 |

### 存储适配器

默认存储位置位于本地文件系统中。 通过&#x200B;_存储适配器_，您可以连接到存储服务并将文件存储到任何位置。 [!DNL Commerce]支持配置以下存储服务：

- [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

## 启用远程存储

您可以在Adobe Commerce安装期间安装远程存储，也可以将远程存储添加到现有Commerce实例。 以下示例演示了使用一组`remote-storage`参数和Commerce `setup` CLI命令的每个方法。 最低限度，您必须提供存储`driver`、`bucket`和`region`。

- 示例：使用远程存储安装Commerce

  ```bash
  bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

- 示例：在现有Commerce上启用远程存储

  ```bash
  bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

>[!TIP]
>
>有关云基础架构上的Adobe Commerce，请参阅[在云基础架构上为Commerce配置远程存储](cloud-support.md)。

## 迁移内容

为特定适配器启用远程存储后，可以使用CLI将现有&#x200B;_媒体_&#x200B;文件迁移到远程存储。

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>同步命令只迁移`pub/media`目录中的文件，_而不是_&#x200B;目录`var`中的导入/导出文件。 请参阅&#x200B;_Commerce 2.4用户指南_&#x200B;中的[计划导入/导出](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html?lang=zh-Hans)。

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
