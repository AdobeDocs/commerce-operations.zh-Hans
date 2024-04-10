---
title: 管理缓存
description: 使用Commerce CLI从命令行管理缓存类型和查看缓存状态
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: 1070291396144f866cadd5e42ebca3e77a484a9b
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# 管理缓存

{{file-system-owner}}

## 缓存类型

您可以使用Adobe Commerce缓存管理系统来提高站点的性能。 本主题介绍系统管理员或有权访问Commerce应用程序服务器的开发人员如何从命令行管理缓存。

>[!NOTE]
>
>
>Commerce站点管理员可以使用缓存管理系统工具从管理员管理缓存。 请参阅 [缓存管理](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) 在 _管理系统指南_.


## 查看缓存状态

在Commerce应用程序服务器的命令行中，使用 `cache:status` Commerce CLI命令。

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

下面是一个示例：

```terminal
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
             webhooks_response: 1
                           eav: 1
         customer_notification: 1
 graphql_query_resolver_result: 1
            config_integration: 1
        config_integration_api: 1
                  admin_ui_sdk: 1
                     full_page: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

>[!TIP]
>
>有关Adobe Commerce支持的默认缓存类型的详细说明，请参阅 [缓存](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#caches) 在 _管理系统指南_.


## 启用或禁用缓存类型

使用此命令可以启用或禁用所有高速缓存类型或仅指定高速缓存类型。 在开发期间禁用缓存类型很有用，因为您无需刷新缓存即可看到更改的结果；但是，禁用缓存类型会对性能产生不利影响。

>[!INFO]
>
>从版本2.2开始，在生产模式下运行Commerce时，只能使用命令行启用或禁用缓存类型。 如果在开发人员模式下运行Commerce，则可以使用命令行或手动启用或禁用缓存类型。 在执行此操作之前，必须手动执行 `<magento_root>/app/etc/env.php` 可由 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).

您可以清洁(也称为 _刷新_ 或 _刷新_)使用命令行或Admin缓存类型。

命令选项：

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

在何处忽略 `[type]` 同时启用或禁用所有缓存类型。 此 `type` option是以空格分隔的缓存类型列表。

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

要列出高速缓存类型及其状态，请执行以下操作：

```bash
bin/magento cache:status
```

例如，要禁用全页高速缓存和DDL高速缓存，请执行以下操作：

```bash
bin/magento cache:disable db_ddl full_page
```

示例结果：

```terminal
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>启用高速缓存类型会自动清除该高速缓存类型。

>[!INFO]
>
>从版本2.3.4开始，Commerce在检索所有系统EAV属性时对其进行缓存。 以这种方式缓存EAV属性可改进性能，因为它减少了向数据库插入/选择请求的数目。 但是，它也会增加缓存网络大小。 开发人员可以通过运行 `bin/magento config:set dev/caching/cache_user_defined_attributes 1` 命令。 这也可以由管理员在中完成 [开发人员模式](../bootstrap/application-modes.md) 通过设置 **商店** >设置 **配置** > **高级** > **开发人员** > **缓存设置** > **缓存用户定义的属性** 到 **是**.

## 清理和刷新缓存类型

>[!NOTE]
>
>多个页面缓存可同时自动失效 **_不含_** 这些实体进行编辑。 例如，当目录中的任何产品被分配给任何类别时，或者当任何 [!UICONTROL related product rule] 已修改。

要从缓存中清除过期的项目，您可以 _清洁_ 或 _刷新_ 缓存类型：

- 清理缓存类型仅会删除已启用Commerce缓存类型中的所有项目。 换言之，此选项不会影响其他进程或应用程序，因为它只清理Commerce使用的缓存。

  禁用的缓存类型不会清除。

  >[!TIP]
  >
  >在升级Magento Open Source或Adobe Commerce的版本、从Magento Open Source升级到Adobe Commerce，或安装B2B for Adobe Commerce或任何模块后，请始终清理缓存。

- 刷新缓存类型会清除缓存存储，这可能会影响使用相同存储的其他进程应用程序。

如果已经尝试清除缓存并且仍然遇到无法隔离的问题，请刷新缓存类型。

命令用法：

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

位置 `[type]` 是以空格分隔的缓存类型列表。 省略 `[type]` 同时清除或刷新所有高速缓存类型。 例如，要刷新所有缓存类型，请输入

```bash
   bin/magento cache:flush
```

示例结果：

```terminal
   Flushed cache types:
   config
   layout
   block_html
   collections
   reflection
   db_ddl
   compiled_config
   eav
   customer_notification
   config_integration
   config_integration_api
   full_page
   graphql_query_resolver_results
   config_webservice
   translate
```

>[!TIP]
>
>您还可以在管理员中清理和刷新缓存类型。 转到 **系统** > **工具** > **缓存管理**. **刷新缓存存储** 相当于 `bin/magento cache:flush`. **刷新Magento缓存** 相当于 `bin/magento cache:clean`.
