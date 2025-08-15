---
title: 应用程序模式
description: Commerce应用程序可以根据您的需求以不同的模式运行。 查看可用的应用程序模式的详细列表。
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: c415c3427f513255b9d4ebe1d24ba4024df21928
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# 应用程序模式

您可以在以下&#x200B;_种模式_&#x200B;中运行该Commerce应用程序：

| 模式名称 | 描述 | 云支持 |
| ------------------------ | ------------------- | ------------- |
| [默认值](#default-mode) | 无需更改设置，即可在单个服务器上部署和运行Commerce应用程序。 _Not_&#x200B;已针对生产进行优化。 | 否 |
| [开发人员](#developer-mode) | 非常适合在扩展或自定义Commerce应用程序时进行开发。 | 否 |
| [生产](#production-mode) | 将Commerce应用程序部署到生产系统并运行该应用程序。 | 是 |
| [维护](#maintenance-mode) | 在执行更新和配置时阻止对站点的访问。 | 是 |

请参阅[设置操作模式](../cli/set-mode.md)，了解如何手动更改Adobe Commerce操作模式。

## 云支持

由于文件系统为只读，因此对更改远程云环境中的模式有严格的限制，并且不能被Adobe Commerce支持覆盖。 请勿尝试通过修改`app/etc/env.php`文件来更改模式，因为`ece-tools`包会基于多个配置源覆盖该文件。

云基础架构上的Adobe Commerce在部署期间以&#x200B;_维护_&#x200B;模式自动运行应用程序，这将使您的网站脱机，直到部署完成。 否则，应用程序将保持在&#x200B;_生产_&#x200B;模式下。 请参阅[Commerce on Cloud Infrastructure指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase)中的&#x200B;_部署进程_。

如果您使用Cloud Docker for Commerce作为开发工具，则可以在&#x200B;_开发人员_&#x200B;模式下在Docker环境中部署云基础架构项目，但由于额外的文件同步操作，性能会降低。 请参阅[Cloud Docker for Commerce指南](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode)中的&#x200B;_部署Docker环境_。


## 默认模式

通过&#x200B;_默认_&#x200B;模式，您可以在一台服务器上部署Commerce应用程序，而无需更改任何设置。 但是，由于静态文件对性能的不利影响，默认模式未针对生产进行优化。 与使用静态文件创建工具生成静态文件相比，创建静态文件并缓存这些文件会对性能产生更大的影响。

在默认模式下：

- 异常会写入日志文件而不是显示
- 静态视图文件已缓存
- 隐藏自定义`X-Magento-*` HTTP请求和响应标头

如果未指定其他模式，Commerce将在默认模式下运行。

## 开发人员模式

建议使用&#x200B;_开发人员_&#x200B;模式来扩展和自定义Commerce应用程序。 静态视图文件不缓存，而是根据需要写入`pub/static`目录。

在开发人员模式下：

- 启用[自动代码编译](../cli/code-compiler.md)和增强型调试
- 浏览器中显示未捕获的异常
- `var/report`中的系统日志记录是详细的
- 错误处理程序中会引发异常，而不是被记录
- 当无法调用事件订阅者时，将引发异常
- 显示自定义`X-Magento-*` HTTP请求和响应标头

>[!NOTE]
>
>Adobe Commerce Cloud环境不支持此模式，并且Adobe Commerce支持部门无法促进更改应用程序模式。

## 生产模式

_生产_&#x200B;模式最适合在生产系统上部署Commerce应用程序。 优化服务器环境（如数据库和Web服务器）后，您应该运行[静态视图文件部署工具](../cli/static-view-file-deployment.md)以将静态视图文件写入`pub/static`目录。 通过在部署时提供所有必需的静态文件而不是强制Commerce应用程序在运行时动态查找和复制（具体化）静态文件，从而提高性能。

某些字段，例如管理员中的高级和开发人员系统配置部分，在生产模式下不可用。 例如，您&#x200B;_无法_&#x200B;使用Admin启用或禁用缓存类型。 您可以使用&#x200B;_命令行_&#x200B;启用和禁用缓存类型[only](../cli/manage-cache.md#config-cli-subcommands-cache-en)。

在生产模式下：

- 静态视图文件仅从缓存中提供
- 错误和异常会记录到文件系统，并且永远不会向用户显示
- 管理员中的一些配置字段不可用

## 维护模式

_维护_&#x200B;模式限制或禁止在改进、更新和配置任务期间访问站点。 默认情况下，网站将访客重定向到默认的`Service Temporarily Unavailable`页面。

您可以创建[自定义维护页面](../../upgrade/troubleshooting/maintenance-mode-options.md)，手动启用和禁用维护模式，并配置维护模式以允许来自授权IP地址的访客正常查看存储区。 请参阅[安装指南](../../installation/tutorials/maintenance-mode.md)中的&#x200B;_启用和禁用维护模式_。

如果您在云基础架构上使用Commerce，则Commerce应用程序将在部署阶段以维护模式运行。 成功完成部署后，Commerce应用程序将恢复以生产模式运行。 请参阅[云基础架构上的Commerce指南](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks)中的&#x200B;_部署挂接_。

在维护模式下：

- 网站访客被重定向到默认`Service Temporarily Unavailable`页面
- `var/`目录包含`.maintenance.flag`文件
- 您可以根据IP地址限制访客访问
