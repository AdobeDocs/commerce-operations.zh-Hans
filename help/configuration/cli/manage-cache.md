---
title: 管理缓存
description: 管理缓存类型和查看缓存状态。
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---

# 管理缓存

{{file-system-owner}}

## 缓存类型

Commerce 2具有以下缓存类型：

| 缓存类型“友好”名称 | 缓存类型代码名称 | 描述 |
|--- |--- |--- |
| 配置 | config | Commerce从所有模块中收集配置，合并该配置，并将合并的结果保存到缓存中。 此缓存还包含存储在文件系统和数据库中的特定于存储的设置。 修改配置文件后，清除或刷新此缓存类型。 |
| 版面 | 布局 | 已编译的页面布局（即来自所有组件的布局组件）。 修改布局文件后，清理或刷新此缓存类型。 |
| 阻止HTML输出 | block_html | 每个块的页面片段HTML。 修改视图层后，清除或刷新此缓存类型。 |
| 收藏集数据 | 收藏集 | 数据库查询的结果。 如有必要，Commerce会自动清理此缓存，但第三方开发人员可以将任何数据放入缓存的任何区段中。 如果您的自定义模块使用的逻辑导致Commerce无法清理的缓存条目，请清理或刷新此缓存类型。 |
| DDL | db_ddl | 数据库模式。 如有必要，Commerce会自动清理此缓存，但第三方开发人员可以将任何数据放入缓存的任何区段中。 在对数据库架构进行自定义更改后，清除或刷新此缓存类型。 （换言之，是Commerce本身不存在的更新。） 自动更新数据库模式的一种方法是使用 `magento setup:db-schema:upgrade` 命令。 |
| 已编译的配置 | compiled_config | 编译配置 |
| 实体属性值(EAV) | eav | 与EAV属性相关的元数据（例如，存储标签、指向相关PHP代码的链接、属性渲染、搜索设置等）。 您通常不需要清理或刷新此缓存类型。 |
| 页面缓存 | full_page | 生成的HTML页。 如有必要，Commerce会自动清理此缓存，但第三方开发人员可以将任何数据放入缓存的任何区段中。 在修改影响HTML输出的代码级别后，清理或刷新此缓存类型。 建议启用此缓存，因为缓存HTML可显着提升性能。 |
| Reflection | 反射 | 删除Webapi模块与客户模块之间的依赖关系。 |
| 翻译 | translate | 合并来自所有模块的翻译后，合并器缓存将被清理。 |
| 集成配置 | 配置集成 | 已编译的集成。 在更改或添加集成后，清理或刷新此缓存。 |
| 集成API配置 | config_integration_api | 存储集成的编译集成API配置。 |
| Web服务配置 | config_webservice | 缓存Web API结构。 |
| 客户通知 | customer_通知 | 显示在用户界面中的临时通知。 |

## 查看缓存状态

要查看高速缓存的状态，请输入

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
                           eav: 1
         customer_notification: 1
                     full_page: 1
            config_integration: 1
        config_integration_api: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

## 启用或禁用缓存类型

使用此命令可以启用或禁用所有高速缓存类型或仅指定高速缓存类型。 在开发期间禁用缓存类型很有用，因为您无需刷新缓存即可查看更改的结果；但是，禁用缓存类型会对性能产生不利影响。

>[!INFO]
>
>从版本2.2开始，在生产模式下运行Commerce时，您只能使用命令行启用或禁用缓存类型。 如果在开发人员模式下运行Commerce，则可以使用命令行或手动启用或禁用缓存类型。 在执行此操作之前，您必须手动进行 `<magento_root>/app/etc/env.php` 可由 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).

您可以清洁(也称为 _刷新_ 或 _刷新_)缓存类型。

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
>从版本2.3.4开始，Commerce会在检索所有系统EAV属性时缓存这些属性。 通过这种方式缓存EAV属性可提高性能，因为它减少了对DB的插入/选择请求量。 但是，它也会增加缓存网络大小。 开发人员可以通过运行 `bin/magento config:set dev/caching/cache_user_defined_attributes 1` 命令。 这还可以在执行时从管理员完成 [开发人员模式](../bootstrap/application-modes.md) 通过设置 **商店** >设置 **配置** > **高级** > **开发人员** > **缓存设置** > **缓存用户定义的属性** 到 **是**.

## 清理和刷新缓存类型

要从缓存中清除过期的项目，您可以 _clean_ 或 _刷新_ 缓存类型：

- 清理缓存类型只会从启用的Commerce缓存类型中删除所有项目。 换言之，此选项不会影响其他进程或应用程序，因为它仅清理Commerce使用的缓存。

   禁用的缓存类型不会清除。

   >[!TIP]
   >
   >在升级Magento Open Source或Adobe Commerce版本、从Magento Open Source升级到Adobe Commerce，或安装B2B for Adobe Commerce或任何模块后，请始终清理缓存。

- 刷新缓存类型会清除缓存存储，这可能会影响使用相同存储的其他进程应用程序。

刷新缓存类型（如果已尝试清除缓存，但仍存在无法隔离的问题）。

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
   config_webservice
   translate
```

>[!TIP]
>
>您还可以在“管理员”中清理和刷新缓存类型。 转到 **系统** > **工具** > **缓存管理**. **刷新缓存存储** 相当于 `bin/magento cache:flush`. **刷新Magento缓存** 相当于 `bin/magento cache:clean`.
