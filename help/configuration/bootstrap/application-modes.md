---
title: 应用模式
description: 商务应用程序可以根据您的需求以不同的模式运行。 查看可用应用程序模式的详细列表。
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 应用模式

您可以在以下任意位置运行Commerce应用程序 _模式_:

| 模块名称 | 描述 |
| ----------- | ----------- |
| 默认 | 允许您在单台服务器上部署商务应用程序，而无需更改任何设置。 但是，默认模式未针对生产进行优化。<br>要在多台服务器上部署商务应用程序或优化其生产，请更改为其他模式之一。<ul><li>已启用静态视图文件缓存</li><li>不会向用户显示异常；而是会将例外写入日志文件。</li><li>隐藏自定义 `X-Magento-*` HTTP请求和响应头</li></ul> |
| 开发人员 | 此模式仅供开发使用：<ul><li>禁用静态视图文件缓存</li><li>提供详细日志记录</li><li>启用 [自动代码编译](../cli/code-compiler.md)</li><li>启用增强的调试功能</li><li>显示自定义 `X-Magento-*` HTTP请求和响应头</li><li>结果性能最慢</li><li>在前端显示错误</li></ul> |
| 生产 | 此模式旨在用于在生产系统上部署：<ul><li>不向用户显示异常（例外仅写入日志）。</li><li>仅从缓存中提供静态视图文件。</li><li>阻止自动代码文件编译。 新文件或更新的文件不会写入文件系统。</li><li>**不允许在管理员中启用或禁用缓存类型。** 请参阅 [启用和禁用缓存](../cli/manage-cache.md#enable-or-disable-cache-types).</li><li>某些字段（如“管理员”中的“高级”和“开发人员”系统配置部分）在生产模式下不可用。</li></ul> |
| 维护 | 此模式旨在防止在站点更新或重新配置时对其进行访问：<ul><li>将网站访客重定向到默认 `Service Temporarily Unavailable` 页面。</li><li>当站点处于维护模式时， `var/` 目录包含 `.maintenance.flag` 文件。</li><li>您可以配置维护模式，以允许访客从指定的IP地址列表访问。</li></ul> |

>[!INFO]
>
>[Adobe Commerce云基础架构](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/overview.html) 仅支持生产和维护模式。

## 默认模式

由于其名称暗示，默认模式是在未指定其他模式时商务的操作方式。 默认模式允许您在单台服务器上部署商务应用程序，而无需更改任何设置。 但是，默认模式没有生产模式那样优化。

要在多台服务器上部署商务应用程序或优化其生产，请更改为其他模式之一。

在默认模式下：

- 错误记录到服务器上的文件报表，从不向用户显示
- 静态视图文件已缓存
- 默认模式未针对生产环境进行优化，这主要是因为 [静态文件](https://glossary.magento.com/static-files) 是动态生成的，而不是实现的。 换言之，创建静态文件并缓存它们比使用静态文件创建工具生成它们对性能的影响更大。

请参阅 [设置操作模式](../cli/set-mode.md).

## 开发人员模式

扩展或自定义商务应用程序时，请在开发人员模式下运行该应用程序。

在开发人员模式下：

- 静态视图文件不会缓存；写给 `pub/static` 目录
- 未捕获的异常显示在浏览器中
- 系统登录 `var/report` 表示verbose
- 安 [例外](https://glossary.magento.com/exception) 在错误处理程序中引发，而不是被记录
- 当 [事件](https://glossary.magento.com/event) 无法调用订阅者

请参阅 [设置操作模式](../cli/set-mode.md).

## 生产模式

将商务部署到生产服务器后，在生产模式下运行该商务。 优化服务器环境（如数据库和Web服务器）后，应运行 [静态视图文件部署工具](../cli/static-view-file-deployment.md) 将静态视图文件写入 `pub/static` 目录访问Advertising Cloud的帮助。

这通过在部署时提供所有必需的静态文件，而不是强制Commerce在运行期间根据需要动态查找和复制（实体化）静态文件，从而提高性能。

在生产模式下：

- 静态视图文件不会实现，并且会动态构建它们的URL。 静态视图文件从 [缓存](https://glossary.magento.com/cache) 仅。
- 错误记录到文件系统，从不向用户显示。
- 您可以启用和禁用缓存类型 _仅_ 使用 [命令行](../cli/manage-cache.md#config-cli-subcommands-cache-en).
- 您 _无法_ 使用“管理员”启用或禁用缓存类型。

## 维护模式

在维护模式下运行商务应用程序，以在您完成维护、升级或配置任务时使您的站点脱机。 在维护模式下，网站会将访客重定向到默认 `Service Temporarily Unavailable` 页面。

您可以创建 [自定义维护页面](../../upgrade/troubleshooting/maintenance-mode-options.md)，手动启用和禁用维护模式，并配置维护模式以允许来自授权IP地址的访客正常查看存储。 请参阅 [启用和禁用维护模式](../../installation/tutorials/maintenance-mode.md).

如果您在云基础架构上使用商务，则商务应用程序会在部署阶段以维护模式运行。 成功完成部署后，Commerce应用程序将返回到在生产模式下运行。 请参阅 [部署挂钩](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) 在 _云基础架构上的商务指南_.
