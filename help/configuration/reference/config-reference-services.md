---
title: 服务配置路径参考
description: 请参阅服务配置值列表。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# 服务配置路径参考

此部分列出了可用于管理员下方选项的变量名称和配置路径 **商店** >设置> **配置** > **服务**.

的 [`magento app:config:dump` 命令](../cli/export-configuration.md) 将这些值写入共享配置文件， `app/etc/config.php`，它应位于源代码管理中。 要选择覆盖任何配置设置或设置敏感设置，请参阅 [使用环境变量覆盖配置设置](override-config-settings.md#environment-variables). 本主题包含 _not_ 列表 [敏感值和系统特定值](config-reference-sens.md).

## 商务Web API路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **服务** > **Web API**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 默认响应字符集 | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 允许匿名来宾访问 | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## OAuth路径

这些配置值在的“管理员”中可用 **商店** >设置> **配置** > **服务** > **OAuth**.

| 名称 | 配置路径 | 仅限商业？ |
|--------------|--------------|--------------|
| 客户令牌生命周期（小时） | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理员令牌生命周期（小时） | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 清除概率 | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 过期期限 | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 过期期限 | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth消费者凭据HTTP Post最大重定向 | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth用户凭据HTTP帖子超时 | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
