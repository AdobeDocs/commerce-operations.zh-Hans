---
title: 服务配置路径参考
description: 请参阅服务配置值列表。
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# 服务配置路径参考

此部分列出了“管理员”中选项可用的变量名称和配置路径，位于 **商店** >设置> **配置** > **服务**.

此 [`magento app:config:dump` 命令](../cli/export-configuration.md) 将这些值写入共享配置文件， `app/etc/config.php`，它应该在源代码控制中。 要选择性地覆盖任何配置设置或设置敏感设置，请参阅 [使用环境变量覆盖配置设置](override-config-settings.md#environment-variables). 此主题可以 _非_ 列表 [敏感值和系统特定的值](config-reference-sens.md).

## Commerce Web API路径

这些配置值在管理员的以下位置提供： **商店** >设置> **配置** > **服务** > **Web API**.

| 名称 | 配置路径 | 仅限商务？ |
|--------------|--------------|--------------|
| 默认响应字符集 | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许匿名访客访问 | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## OAuth路径

这些配置值在管理员的以下位置提供： **商店** >设置> **配置** > **服务** > **OAuth**.

| 名称 | 配置路径 | 仅限商务？ |
|--------------|--------------|--------------|
| 客户令牌生命周期（小时） | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理令牌生命周期（小时） | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 清理概率 | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有效期 | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有效期 | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth使用者凭据HTTP帖子最大重定向 | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth使用者凭据HTTP Post超时 | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
