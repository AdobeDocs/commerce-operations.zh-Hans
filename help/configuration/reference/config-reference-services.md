---
title: 服务配置路径参考
description: 了解Adobe Commerce管理设置中的服务配置路径和值。 发现Web API、OAuth和服务集成配置选项。
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 1%
---
# 服务配置路径参考

此部分列出了&#x200B;**商店** >设置> **配置** > **服务**&#x200B;下的管理员中选项可用的变量名称和配置路径。

[`magento app:config:dump`命令](../cli/export-configuration.md)将这些值写入到共享配置文件`app/etc/config.php`中，该文件应位于源代码控制中。 若要选择性地覆盖任何配置设置或设置敏感设置，请参阅[使用环境变量覆盖配置设置](override-config-settings.md#environment-variables)。 此主题&#x200B;_不_&#x200B;列出[敏感且特定于系统的值](config-reference-sens.md)。

## Commerce Web API路径

这些配置值在&#x200B;**存储** >设置> **配置** > **服务** > **Web API**&#x200B;的管理员中可用。

| 名称 | 配置路径 | 仅限Commerce？ |
|--------------|--------------|--------------|
| 默认响应字符集 | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许匿名访客访问 | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## OAuth路径

这些配置值在&#x200B;**存储** >设置> **配置** > **服务** > **OAuth**&#x200B;的管理员中可用。

| 名称 | 配置路径 | 仅限Commerce？ |
|--------------|--------------|--------------|
| 客户令牌生命周期（小时） | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理令牌生命周期（小时） | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 清理概率 | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有效期 | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有效期 | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth使用者凭据HTTP帖子最大重定向 | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth使用者凭据HTTP Post超时 | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
