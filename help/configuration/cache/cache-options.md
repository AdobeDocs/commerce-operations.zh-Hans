---
title: 缓存后端选项和存储参考
description: 了解Adobe Commerce中的缓存后端选项，包括文件系统、Redis、Valkey和数据库存储。 发现基于Zend的(RemoteSynchronizedCache)和Symfony缓存选项。
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="内部部署" type="Informative" url="https://experienceleague.adobe.com/zh-hans/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce本地项目。"
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 23f63c896760992da9b0d30b756a37de2117f6b8
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%
---
# 缓存后端选项和存储参考

>[!NOTE]
>
>此页面记录本地`app/etc/env.php`配置。
>
>对于[!DNL Adobe Commerce on Cloud]项目，`ece-tools`包在部署期间根据`.magento.env.yaml`中的部署变量配置生成结果`app/etc/env.php`配置。 您不编辑`env.php`文件。  查看[Valkey和Redis服务配置的最佳实践](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration)和[部署变量](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)。

Commerce应用程序使用低级缓存前端和后端来提供对缓存存储的访问。 Commerce支持多种缓存后端和策略，每种后端和策略都适用于不同的用例。 本页介绍可用的后端及其差异。

>[!NOTE]
>
>[Varnish](config-varnish-install.md)在HTTP级别处理内部部署的整页缓存。 [Fastly服务](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/cdn/fastly)为云部署处理它。 这两种解决方案都未使用低级缓存后端。

## 后端缓存选项

下表汇总了可用的后端缓存：

| 后端 | 描述 | 配置指南 |
| ------- | ----------- | ------------------- |
| 文件系统 | 默认。 将缓存数据存储在`var/cache/`下的文件中。 无需配置。 | 不适用 |
| Redis | 用于高性能缓存的内存中数据存储。 | [对默认缓存使用Redis](redis-pg-cache.md) |
| Valkey | 开源、与Redis兼容的替代方案。 | [对默认缓存使用Valkey](valkey-pg-cache.md) |
| 数据库 | 由数据库支持的自定义缓存引擎 | [创建自定义缓存引擎](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching){target="_blank"} （Adobe Developer文档） |

>[!IMPORTANT]
>
>Adobe Commerce 2.4.9或更高版本的2.4.5-p16、2.4.6-p14、2.4.7-p9和2.4.8-p4修补程序不支持Redis缓存。 如果您要升级到其中一个版本，请配置Valkey并更新缓存配置以使用它。 有关[!DNL Adobe Commerce on-premises]，请参阅[设置Valkey](config-valkey.md)。

## 缓存后端和L2实施 {#implementation-approaches}

Commerce支持直接缓存后端和L2缓存。 直接后端选择缓存存储。 二级缓存在远程存储前添加了一个本地缓存层。

### 直接缓存后端

下表汇总了`<Commerce-install-dir>/app/etc/env.php`的缓存后端配置值。 它不会启用L2缓存。

| Commerce版本 | 后端 | 配置值 |
| ---------------- | ------- | -------------------- |
| 2.4.8及更早版本，如果支持 | 文件 | 默认。 无需配置 |
| 2.4.8及更早版本，如果支持 | Redis | `Magento\Framework\Cache\Backend\Redis` |
| 2.4.8及更早版本，如果支持 | Valkey | `Magento\Framework\Cache\Backend\Valkey` |
| 2.4.9及更高版本，以及支持的后端端口 | 文件 | `file` |
| 2.4.9及更高版本，以及支持的后端端口 | Valkey | `valkey` |

有关修补程序级别的准确支持，请参阅[系统要求](../../installation/system-requirements.md)。

>[!TAB 基于Zend的缓存（2.4.8及更早版本）]

#### 后端示例

对于内部部署，以下示例在`<Commerce-install-dir>/app/etc/env.php`中配置直接缓存后端。 它们不会启用L2缓存。 请勿对[!DNL Adobe Commerce on Cloud]部署使用这些示例，部署期间使用`ece-tools`包生成生成的`app/etc/env.php`配置。

>[!BEGINTABS]

>[!TAB 红色]

仅在支持Redis的版本上使用完整的Redis类名称：

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!TAB Valkey]

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!ENDTABS]

## L2缓存

二级缓存(L2)在共享远程缓存存储前面的每个Web节点上添加了一个本地缓存层，从而减少了Commerce和远程缓存之间的网络流量。 有关实施选项、版本支持和配置步骤，请参阅[二级缓存配置](level-two-cache.md)。

对于云项目，请通过[部署变量](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"}中描述的部署变量配置L2缓存。

- [将Redis用于默认缓存](redis-pg-cache.md)
- [将Valkey用于默认缓存](valkey-pg-cache.md)
- [二级缓存配置](level-two-cache.md)
