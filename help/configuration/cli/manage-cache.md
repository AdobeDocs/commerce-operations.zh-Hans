---
title: 管理缓存
description: 管理缓存类型并查看缓存状态。
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 管理缓存

{{file-system-owner}}

## 缓存类型

商务2具有以下缓存类型：

| 缓存类型“友好”名称 | 缓存类型代码名称 | 描述 |
|--- |--- |--- |
| 配置 | 配置 | Commerce从所有模块收集配置、合并该配置，并将合并结果保存到缓存中。 此缓存还包含存储在文件系统和数据库中的特定存储设置。 修改配置文件后，清除或刷新此缓存类型。 |
| 布局 | 布局 | 编译的页面布局（即，所有组件的布局组件）。 修改布局文件后，清除或刷新此缓存类型。 |
| 块HTML输出 | block_html | HTML每个块的页面片段。 修改视图层后，清除或刷新此缓存类型。 |
| 集合数据 | 收藏集 | 数据库查询的结果。 如有必要，商务会自动清理此缓存，但第三方开发人员可以将任何数据放入缓存的任何区段中。 如果您的自定义模块使用导致Commerce无法清除的缓存条目的逻辑，则清除或刷新此缓存类型。 |
| DDL | db_ddl | 数据库模式。 如有必要，商务会自动清理此缓存，但第三方开发人员可以将任何数据放入缓存的任何区段中。 在对数据库架构进行自定义更改后，清除或刷新此缓存类型。 （换言之，Commerce不会自行更新。） 自动更新数据库模式的一种方法是使用 `magento setup:db-schema:upgrade` 命令。 |
| 编译的配置 | compiled_config | 编译配置 |
| 实体属性值(EAV) | eav | 与EAV属性相关的元数据（例如，存储标签、指向相关PHP代码的链接、属性渲染、搜索设置等）。 通常不应该清除或刷新此缓存类型。 |
| 页面缓存 | full_page | 生成的HTML页面。 如有必要，商务会自动清理此缓存，但第三方开发人员可以将任何数据放入缓存的任何区段中。 修改影响HTML输出的代码级别后，清除或刷新此缓存类型。 建议保持此缓存处于启用状态，因为缓存HTML可显着提高性能。 |
| 反射 | 反射 | 删除Webapi模块与客户模块之间的依赖关系。 |
| 翻译 | 翻译 | 从所有模块合并转换后，将清理合并缓存。 |
| 集成配置 | config_integration | 编译集成。 更改或添加集成后，清除或刷新此缓存。 |
| 集成API配置 | config_integration_api | 对商店集成的编译集成API配置。 |
| Web服务配置 | config_webservice | 缓存Web API结构。 |
| 客户通知 | customer_notification | 用户界面中显示的临时通知。 |

## 查看缓存状态

要查看缓存的状态，请输入

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

示例如下：

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

此命令允许您启用或禁用所有缓存类型或您指定的缓存类型。 禁用缓存类型在开发过程中非常有用，因为您无需刷新缓存即可看到更改的结果；但是，禁用缓存类型会对性能产生不利影响。

>[!INFO]
>
>从版本2.2开始，您只能在生产模式下运行商务时使用命令行启用或禁用缓存类型。 如果在开发人员模式下运行商务，则可以使用命令行或手动启用或禁用缓存类型。 在执行此操作之前，您必须手动 `<magento_root>/app/etc/env.php` 可由写入 [文件系统所有者](../../installation/prerequisites/file-system/overview.md).

您可以清理(也称为 _刷新_ 或 _刷新_)缓存类型。

命令选项：

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

省略 `[type]` 同时启用或禁用所有缓存类型。 的 `type` 选项是以空格分隔的缓存类型列表。

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

要列出缓存类型及其状态，请执行以下操作：

```bash
bin/magento cache:status
```

例如，要禁用完整页缓存和DDL缓存，请执行以下操作：

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
>启用缓存类型会自动清除该缓存类型。

>[!INFO]
>
>自版本2.3.4起，Commerce在检索到所有系统EAV属性时会缓存这些属性。 以这种方式缓存EAV属性会提高性能，因为它会减少对数据库的插入/选择请求数量。 但是，它也会增加缓存网络大小。 开发人员可以通过运行 `bin/magento config:set dev/caching/cache_user_defined_attributes 1` 命令。 也可以在 [开发人员模式](../bootstrap/application-modes.md) 通过设置 **商店** >设置 **配置** > **高级** > **开发人员** > **缓存设置** > **缓存用户定义的属性** to **是**.

## 清理和刷新缓存类型

要从缓存中清除过期项目，您可以 _清洁_ 或 _刷新_ 缓存类型：

- 清除缓存类型仅会从已启用的商务缓存类型中删除所有项目。 换句话说，此选项不会影响其他进程或应用程序，因为它只清理Commerce使用的缓存。

   未清除禁用的缓存类型。

   >[!TIP]
   >
   >升级Magento Open Source或Adobe Commerce版本、从Magento Open Source升级到Adobe Commerce，或为Adobe Commerce或任何模块安装B2B后，应始终清除缓存。

- 刷新缓存类型会清除缓存存储，这可能会影响使用相同存储的其他进程应用程序。

如果您已尝试清除缓存，但仍然遇到无法隔离的问题，则刷新缓存类型。

命令用法：

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

其中 `[type]` 是以空格分隔的缓存类型列表。 省略 `[type]` 同时清除或刷新所有缓存类型。 例如，要刷新所有缓存类型，请输入

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
>您还可以在管理员中清除和刷新缓存类型。 转到 **系统** > **工具** > **缓存管理**. **刷新缓存存储** 等于 `bin/magento cache:flush`. **刷新Magento缓存** 等于 `bin/magento cache:clean`.
