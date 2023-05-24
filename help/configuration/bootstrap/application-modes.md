---
title: 应用程序模式
description: Commerce应用程序可以根据您的需求以不同的模式运行。 查看可用的应用程序模式的详细列表。
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---

# 应用程序模式

您可以通过以下任意方式运行Commerce应用程序 _模式_：

| 模式名称 | 描述 | 云支持 |
| ------------------------ | ------------------- | ------------- |
| [默认](#default-mode) | 在单个服务器上部署和运行Commerce应用程序，而不更改设置。 _非_ 针对生产进行了优化。 | 否 |
| [开发人员](#developer-mode) | 非常适合在扩展或自定义Commerce应用程序时进行开发。 | 否 |
| [生产](#production-mode) | 将Commerce应用程序部署并运行到生产系统。 | 是 |
| [维护](#maintenance-mode) | 在执行更新和配置时阻止对站点的访问。 | 是 |

参见 [设置操作模式](../cli/set-mode.md) 了解如何手动更改Adobe Commerce操作模式。

## 云支持

无需管理云基础架构项目的应用程序模式。 由于只读文件系统，您不能更改远程云环境中的模式。 云基础架构上的Adobe Commerce会在中自动运行应用程序 _维护_ 模式，可使网站离线，直到部署完成。 否则，应用程序将保留在 _生产_ 模式。 参见 [部署过程](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) 在 _云基础架构上的Commerce指南_.

如果您使用Cloud Docker for Commerce作为开发工具，则可以在以下位置在Docker环境中部署云基础架构项目： _开发人员_ 模式，但由于额外的文件同步操作而降低性能。 参见 [部署Docker环境](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) 在 _Cloud Docker for Commerce指南_.

## 默认模式

此 _默认_ 模式允许您在单个服务器上部署Commerce应用程序，而无需更改任何设置。 但是，由于静态文件对性能的不利影响，默认模式未针对生产进行优化。 与使用静态文件创建工具生成静态文件相比，创建静态文件并缓存这些文件对性能的影响更大。

在默认模式下：

- 异常将写入日志文件而不是显示
- 静态视图文件已缓存
- 隐藏自定义 `X-Magento-*` HTTP请求和响应标头

如果未指定其他模式，则Commerce在默认模式下运行。

## 开发人员模式

此 _开发人员_ 建议使用模式来扩展和自定义Commerce应用程序。 静态视图文件不缓存，而是写入 `pub/static` 按需目录。

在开发人员模式下：

- 启用 [自动代码编译](../cli/code-compiler.md) 和增强型调试
- 浏览器中显示未捕获的异常
- 系统登录 `var/report` 冗长
- 错误处理程序中会引发异常，而不是被记录
- 当无法调用事件订阅者时，将引发异常
- 显示自定义 `X-Magento-*` HTTP请求和响应标头

## 生产模式

此 _生产_ 模式最适合在生产系统上部署Commerce应用程序。 优化服务器环境（如数据库和Web服务器）后，您应该运行 [静态视图文件部署工具](../cli/static-view-file-deployment.md) 将静态视图文件写入 `pub/static` 目录。 通过在部署时提供所有必要的静态文件而不是强制Commerce应用程序在运行时动态查找和复制（具体化）静态文件，从而提高性能。

一些字段在生产模式下不可用，例如“管理员”中的“高级”和“开发人员”系统配置部分。 例如，您 _无法_ 使用Admin启用或禁用缓存类型。 您可以启用和禁用缓存类型 _仅限_ 使用 [命令行](../cli/manage-cache.md#config-cli-subcommands-cache-en).

在生产模式下：

- 静态视图文件仅从缓存中提供
- 错误和异常会记录到文件系统，并且永远不会向用户显示
- 管理员中的一些配置字段不可用

## 维护模式

此 _维护_ 在改进、更新和配置任务期间，模式会限制或阻止对站点的访问。 默认情况下，网站会将访客重定向到默认位置 `Service Temporarily Unavailable` 页面。

您可以创建 [自定义维护页面](../../upgrade/troubleshooting/maintenance-mode-options.md)，手动启用和禁用维护模式，并配置维护模式以允许来自授权IP地址的访客正常查看存储区。 参见 [启用和禁用维护模式](../../installation/tutorials/maintenance-mode.md) 在 _安装指南_.

如果您在云基础架构上使用Commerce，则Commerce应用程序在部署阶段以维护模式运行。 成功完成部署后，Commerce应用程序将返回到生产模式下运行。 参见 [部署挂接](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) 在 _云基础架构上的Commerce指南_.

在维护模式下：

- 网站访客将被重定向到默认值 `Service Temporarily Unavailable` 页面
- 此 `var/` 目录包含 `.maintenance.flag` 文件
- 您可以根据IP地址限制访客访问
