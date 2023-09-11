---
title: Adobe Commerce可扩展性策略
description: 了解Adobe Commerce的可扩展性模型如何让您能够自定义实施。
exl-id: fac4630d-8a41-40dc-899a-01eabceaa61e
feature: Extensibility
source-git-commit: 4873a51fbf67d305fdd1898f3740c73ac5ccbad8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# 可扩展性策略

Adobe Commerce的可扩展性平台允许品牌公司高效地定制流程、集成系统和部署新功能，同时保持可升级性。

## Commerce扩展策略概述

扩展Commerce平台的功能包括以下高级方法：

* 扩展Commerce平台的本机功能。 例如，商家可以安装Marketplace应用程序（通常由第三方构建），以扩展和优化平台的本机功能，例如，可在结账期间验证配送地址并促进与UPS运营商地址API快速集成的扩展。

* 将第三方应用程序/扩展与Commerce平台集成。 开发人员可以使用Commerce现有的全面REST和GraphQL API将Commerce与第三方解决方案直接集成。

但是，平台架构决定了扩展平台的最佳策略。 Commerce为Headless部署提供了丰富的GQL和REST API范围。 核心Commerce代码库继续朝着模块化程度更高的架构和单一集成层发展，后者提供了新的改进自定义工具：

* [适用于Adobe Commerce的App Builder](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder.html) 是基于Adobe基础架构构建的开发框架和工具集。 开发人员可以使用此插件创建Commerce扩展，范围从用户体验/店面自定义到中间件和业务逻辑扩展。

* [适用于Adobe Developer App Builder的API网格](https://developer.adobe.com/graphql-mesh-gateway/) 允许开发人员将多个数据源合并到单个API端点中。 这支持私有API和第三方API的API编排或集成，以及其他软件接口与Adobe Commerce API和使用Adobe I/O的其他Adobe产品。

* [Adobe Commerce的Adobe I/O事件](https://developer.adobe.com/commerce/events/get-started/) 使事务型数据可供使用App Builder和第三方Web挂接开发的应用程序使用，从而支持创建事件驱动型应用程序。

这些工具提供对Adobe Developer控制台和Adobe开发人员工具的访问权限，以便创建API并集成自定义插件和集成。

下图重点介绍了Commerce扩展性策略的主要组件。

![Adobe Commerce可扩展性策略图](../../assets/playbooks/extensibility-strategy-overview.png)
