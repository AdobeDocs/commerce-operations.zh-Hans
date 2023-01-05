---
title: 更新服务最佳实践
description: 了解如何保持Adobe Commerce在云基础架构技术堆栈上更新。
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: cf8626bfab170a1e12cc72f0bc344c9beb9349a7
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# 更新服务最佳实践

本文提供了使您的Adobe Commerce保持云基础架构技术堆栈更新的建议，并提供了指向有用资源的链接。

## 受影响的产品和版本

Adobe Commerce on cloud infrastructure 2.4.x及更高版本

## 更新服务

在Adobe Commerce使用的服务和组件到达或接近生命周期终止日期之前，请对其进行升级。 这有助于跟上PCI合规性并减少安全漏洞。

入门计划客户可以在服务升级时自助服务。 请参阅 [更改服务版本](https://devdocs.magento.com/cloud/project/services.html#change-service-version) 以了解有关如何执行此操作的详细信息。

专业计划客户只能在其 [集成环境](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html). 对于生产服务升级，您必须 [提交支持票证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 请求升级。

>[!WARNING]
>
>如果没有向基础架构团队发出48个工作小时的通知，服务升级就无法推送到生产环境。 这是必需的，因为我们需要确保我们有基础架构支持工程师来在所需的时间范围内更新您的配置，同时将生产环境的停机时间降到最低。

您可以在以下文件中查看服务版本和终止日期的列表： [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>此文件不能被视为一个真相来源。 如有疑问，请参阅官方供应商网站以了解这些技术。

## 其他信息

[系统要求](../../../installation/system-requirements.md)
