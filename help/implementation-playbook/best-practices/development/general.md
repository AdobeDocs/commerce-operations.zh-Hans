---
title: 一般开发最佳实践
description: 了解开发Adobe Commerce项目的一般最佳实践。
feature: Best Practices
role: Developer
exl-id: 35de9849-2d19-4bb6-b920-9ce3838bc8bc
source-git-commit: 68dc4635df9fc411925fe0d48a578edece8895dc
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Adobe Commerce的一般开发最佳实践

本主题介绍正常Adobe Commerce开发过程的基准。 它描述了基本流程、编码原则和应用程序设计原则，以指导开发人员。

>[!NOTE]
>
>Adobe技术架构师在涉及开发的参与过程中将这些最佳实践作为参考。

这些最佳实践是在开发和交付Commerce项目的多年经验的基础上开发的。 Adobe建议技术计划遵循这些最佳实践，并且您改进现有流程和代码以符合这些最佳实践。

## 文本惯例

本主题中的关键词“必须”、“不得要”、“必需”、“应”、“不应”、“应”、“不应该”、“建议”、“可能”和“可选”将解释为[RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119)中所述。

## 进程

1. 在开始项目活动之前，必须商定一个确定的项目方法。 它可以是Scrum、Waterfall或任何其它方法或方法组合，只要它有定义即可。
1. 在开发团队获得版本控制系统的分支策略之前，不应开始开发。
1. 在签署技术规范、签署用户故事和用例以及签署测试用例之后开发团队才应该开始。
1. 在至少有一个开发和QA环境可用之前，不应开始开发。
1. 对于开发必须开始的项目特定要求，可以在&#x200B;_Ready_&#x200B;的定义中记录。
1. 签核应由有权签核项目交付件的客户代表完成。
1. 在Agile项目方法中，签核后可能会提出其他要求。 应将这些需求视为新需求，并应相应地捕获、构建和规划这些需求。
1. 在提交之前，所有开发都必须由开发人员进行功能测试。
1. 所有开发都应先通过自动化测试，然后再提交进行代码审查。 在创建拉取请求后，可将此配置为自动流程。
1. 所有开发都必须通过技术架构师或主要开发人员的手动代码审查，然后才能提交以进行质量保证。
1. 所有开发都必须先通过质量保证，然后才能交付给客户端。
1. 交付时强制执行的项目特定要求可能会记录在“完成的定义”中。

## 环境

1. 所有开发人员应使用相同的IDE。 PhpStorm是推荐用于Adobe Commerce开发的IDE。
1. 所有开发人员应使用与在（未来）生产服务器上使用的相同技术栈栈进行开发和测试。 此技术栈栈中的软件版本必须与生产服务器上安装的软件的主要版本和次要版本匹配。 有关Adobe Commerce的典型技术栈栈的详细信息，请参阅[系统要求](../../../installation/system-requirements.md)。
1. 系统管理员或技术架构师可以为团队提供集中维护的本地开发环境，以确保和促进平等和最新的本地环境。
1. 开发人员和QA工程师必须能够访问QA环境的命令行、数据库和日志文件。 这可能需要VPN连接。

## 版本控制

模块版本必须遵循[语义版本控制2.0.0标准](https://semver.org/)。
Adobe Commerce代码库的依赖项应遵循[模块版本依赖项准则](https://developer.adobe.com/commerce/php/development/versioning/dependencies/)。

## 修订控制

提交必须伴有有意义的提交消息。

## 安全性

1. [不应使用非安全函数](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/)。
1. 应应用[XSS预防策略](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)。
1. 应应用[内容安全策略](https://developer.adobe.com/commerce/php/development/security/content-security-policies/)。
1. 新的Adobe Commerce实例应在尚未达到“安全修复程序结束”日期的最新安全版本上交付。 请参阅[Adobe Commerce软件生命周期策略](../../../release/lifecycle-policy.md)。
