---
title: 缓存后端选项和存储参考
description: 了解Adobe Commerce中的缓存后端选项，包括文件系统、Redis、Valkey和数据库存储。 探索传统和现代方法。
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="内部部署" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce本地项目。"
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 8c5dc151b00fd73e939c32fdc083fb0e8fc41dc8
workflow-type: tm+mt
source-wordcount: 761
ht-degree: 0%

---

# 缓存后端选项和存储参考

>[!NOTE]
>
>此页面记录本地`app/etc/env.php`配置。
>
>对于[!DNL Adobe Commerce on Cloud]项目，`ece-tools`包在部署期间根据`.magento.env.yaml`中的部署变量配置生成结果`app/etc/env.php`配置。 您不编辑`env.php`文件。  查看[Valkey和Redis服务配置的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration)和[部署变量](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)。

Commerce应用程序使用低级缓存前端和后端来提供对缓存存储的访问。 Commerce支持多种缓存后端和策略，每种后端和策略都适用于不同的用例。 本页介绍可用的后端及其差异。

>[!NOTE]
>
>[Varnish](config-varnish-install.md)在HTTP级别处理内部部署的整页缓存。 [Fastly服务](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly)为云部署处理它。 这两种解决方案都未使用低级缓存后端。

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

以下PHP示例在`<Commerce-install-dir>/app/etc/env.php`中配置缓存后端。 它们不会启用L2缓存。

| Commerce版本 | 实现 | 后端 | 配置值 |
| ---------------- | -------------- | ------- | ------------------- |
| 2.4.8及更早版本，如果支持 | 旧版 | 文件系统（默认） | 无需配置 |
| 2.4.8及更早版本，如果支持 | 旧版 | Redis | `Magento\Framework\Cache\Backend\Redis` |
| 2.4.8及更早版本，如果支持 | 旧版 | Valkey | `Magento\Framework\Cache\Backend\Valkey` |
| 2.4.9及更高版本，以及支持的后端端口 | 新版Symfony缓存 | 文件系统（默认） | `file` |
| 2.4.9及更高版本，以及支持的后端端口 | 新版Symfony缓存 | Valkey | `valkey` |

有关修补程序级别的准确支持，请参阅[系统要求](../../installation/system-requirements.md)。

>[!NOTE]
>
>新式实现接受`redis`类型名称，但Redis不是官方支持的缓存服务，它需要Valkey。 请改用`valkey`。

#### 基于Zend的旧版后端示例

对于内部部署，以下示例在`<Commerce-install-dir>/app/etc/env.php`中配置直接缓存后端。 它们不会启用L2缓存。 请勿对[!DNL Adobe Commerce on Cloud]部署使用这些示例，部署期间使用`ece-tools`包生成生成的`app/etc/env.php`配置。

>[!BEGINTABS]

>[!TAB 旧版后端Redis]

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

>[!TAB 旧版后端Valkey]

在支持旧版Valkey后端的版本上使用完整的Valkey类名称：

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

#### 新版Symfony缓存后端

默认的直接后端是文件系统。 要将Valkey与现代实施结合使用，请使用简化的`valkey`后端类型。

以下配置示例适用于Adobe Commerce 2.4.9及更高版本，在使用新版Symfony Cache实施配置直接默认缓存时，该示例还支持支持Valkey的反向移植。

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

>[!TIP]
>
>Symfony缓存实施支持可选的性能功能，例如igbinary序列化、压缩、Lua脚本和永久连接。 有关详细信息，请参阅[为默认和页面缓存配置Valkey](valkey-pg-cache.md)。

### 二级缓存实施

二级缓存(L2)在共享远程缓存存储前面的每个Web节点上添加了一个本地缓存层，从而减少了Commerce和远程缓存之间的网络流量。

| Commerce版本 | L2实施 | 远程后端 |
| ---------------- | ------------------ | --------------- |
| 在2.4.9之前，如果支持 | remotesynchronizedcache | Redis或Valkey，具体取决于Commerce版本和修补程序级别的支持列表 |
| 2.4.9及更高版本 | symfony_l2 | Valkey |

有关内部部署配置，请参阅[二级缓存配置](level-two-cache.md)。

对于云项目，请通过[部署变量](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"}中描述的部署变量配置L2缓存。

#### 二级缓存配置

- 有关&#x200B;**[!DNL Adobe Commerce on-premises]**&#x200B;配置详细信息，请参阅[二级缓存配置](level-two-cache.md)。

- 对于&#x200B;**[!DNL Adobe Commerce on Cloud]**，请通过相应的部署变量配置L2缓存，而不是直接编辑`app/etc/env.php`。 请参阅&#x200B;_云上的Adobe Commerce_&#x200B;文档中的[部署变量](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"}。
