---
title: 配置远程存储
description: 了解如何为本地商务应用程序配置远程存储模块。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# 配置远程存储

远程存储模块提供了一个选项，用于存储媒体文件，并使用存储服务(如AWS S3)在永久的远程存储容器中计划导入/导出。 默认情况下， [!DNL Commerce] 应用程序将媒体文件存储在包含应用程序的同一文件系统中。 对于复杂的多服务器配置而言，这一效率很低，并且在共享资源时可能会导致性能降低。 使用远程存储模块，您可以在 `pub/media` 目录和导入/导出文件(位于 `var` 远程对象存储的目录，以利用服务器端图像大小调整。

>[!INFO]
>
>远程存储仅在版本2.4.2及更高版本中可用。 请参阅 [2.4.2发行说明](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).

>[!INFO]
>
>远程存储模块具有 _有限_ 在Adobe Commerce上支持云基础架构。 Adobe无法对第三方存储适配器服务进行完全故障诊断。

![模式图像](../../assets/configuration/remote-storage-schema.png)

## 远程存储选项

您可以使用 `remote-storage` 选项 [`setup` CLI命令][setup]. 的 `remote-storage` 选项使用以下语法：

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

的 `parameter-name` 是指特定的远程存储参数名称。 下表列出了可用于配置远程存储的参数：

| 命令行参数 | 参数名称 | 描述 | 默认值 |
|--- |--- |--- |--- |
| `remote-storage-driver` | 驱动程序 | 适配器名称<br>可能值：<br>**文件**:禁用远程存储并使用本地文件系统&#x200B;<br>**aws-s3**:使用 [Amazon Simple Storage Service(Amazon S3)](remote-storage-aws-s3.md) | 无 |
| `remote-storage-bucket` | 桶 | 对象存储或容器名称 | 无 |
| `remote-storage-prefix` | 前缀 | 可选前缀（对象存储内的位置） | 空 |
| `remote-storage-region` | 地区 | 区域名称 | 无 |
| `remote-storage-key` | 访问密钥 | 可选访问密钥 | 空 |
| `remote-storage-secret` | 密钥 | 可选密钥 | 空 |

### 存储适配器

默认存储位置位于本地文件系统中。 A _存储适配器_ 使您能够连接到存储服务并将文件存储到任何位置。 [!DNL Commerce] 支持配置以下存储服务：

- [Amazon Simple Storage Service(Amazon S3)](remote-storage-aws-s3.md)

## 启用远程存储

您可以在新 [!DNL Commerce] 安装或添加到现有商务实例 `remote-storage` 参数名称和值对，带有 `setup` CLI命令。 至少，你必须提供存储 `driver`, `bucket`和 `region`.

以下示例使用美国的AWS S3存储适配器启用远程存储：

- 安装新 [!DNL Commerce] 具有远程存储

   ```bash
   bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

- 在现有存储上启用远程存储 [!DNL Commerce]

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

## 限制

不能同时启用远程存储和数据库存储。 如果使用远程存储，请禁用数据库存储。

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

启用远程存储可能会影响您已建立的开发体验。 例如，某些PHP文件函数可能无法按预期工作。 必须对文件操作强制使用商务框架。

禁止使用的PHP本机函数列表可在 [Magento编码标准] 存储库。

## 迁移内容

为特定适配器启用远程存储后，可以使用CLI迁移现有 _媒体_ 文件到远程存储。

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>sync命令只迁移 `pub/media` 目录， _not_ 在 `var` 目录访问Advertising Cloud的帮助。 请参阅 [计划导入/导出][import-export] 在 _Commerce 2.4用户指南_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
[nginx-module]: http://nginx.org/en/docs/http/ngx_http_image_filter_module.html
[Magento编码标准]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php
[setup]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-deployment.html#instgde-cli-subcommands-configphp
