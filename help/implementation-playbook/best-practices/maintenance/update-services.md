---
title: 更新服务最佳实践
description: 了解如何使您的Adobe Commerce on cloud infrastructure技术栈栈保持更新。
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# 更新服务最佳实践

本文提供了有关保持Adobe Commerce on cloud infrastructure技术栈栈更新的建议，并提供有用资源的链接。

## 受影响的产品和版本

云基础架构上的Adobe Commerce 2.4.x及更高版本

## 更新服务

在Adobe Commerce使用的服务和组件达到或接近生命周期结束日期之前升级它们。 这有助于遵守PCI法规并减少安全漏洞。

入门计划客户可自助服务升级。 请参阅 [更改服务版本](https://devdocs.magento.com/cloud/project/services.html#change-service-version) 以了解有关如何执行此操作的详细信息。

Pro计划的客户只能自助服务以下计划中的服务升级： [集成环境](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html). 对于在生产环境中升级服务，您必须 [提交支持服务单](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 请求升级。

>[!WARNING]
>
>如果没有48个工作小时的通知，就无法将服务升级推送到生产环境。 这是必需的，因为我们需要确保我们有一名基础架构支持工程师在所需时间范围内更新您的配置，同时最大限度地减少生产环境的停机时间。

您可以在以下文件中查看服务版本和生命周期结束日期的列表： [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>此文件不能被视为单个真实来源。 如有疑问，请参阅官方供应商网站以了解这些技术。

## 其他信息

[系统要求](../../../installation/system-requirements.md)
