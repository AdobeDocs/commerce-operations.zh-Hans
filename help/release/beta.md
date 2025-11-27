---
title: Beta版本
description: 了解Adobe Commerce测试版以及如何参与。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 0%

---

# Adobe Commerce测试版

Adobe Commerce测试版程序是一种商户访问预发行版功能和代码、提供反馈以及引导Adobe Commerce未来的方式。 有两种类型的测试版计划：

- 公共Beta：公共Beta计划可供所有Adobe Commerce客户和合作伙伴使用
- Private Beta：私人测试版计划可能需要根据参与资格标准进行审批

>[!IMPORTANT]
>
>Beta版本可能包含缺陷，并“按原样”提供，无任何类型的担保。 Adobe没有义务维护、更正、更新、更改、修改或以其他方式支持(通过Adobe支持服务或其他方式)Beta版。 建议客户谨慎使用，并且不要以任何方式依赖测试版和/或任何随附的文档或材料的正确功能或性能。 Beta版中的功能和API如有更改，恕不另行通知。 因此，使用测试版完全由客户自行承担风险。

## 参与的优势

抢先体验Adobe正在开发的功能可以让客户和合作伙伴提供反馈、制定产品开发方案，并准备在正式发布之前采用新功能。

## 当前的Beta项目

请参阅以下部分，了解活动Beta程序的列表。

### 语义搜索：更智能、上下文感知的购物体验（私有测试版）

语义搜索是一种电子商务搜索技术，它理解购物者查询后面的&#x200B;*含义*，而不仅仅是确切的单词。 传统基于关键字的搜索在查询包含不熟悉或拼写错误的术语时通常失败，与此不同，这种AI支持的方法使用自然语言处理(NLP)和上下文来解释意图，以提供更相关的结果。

这项技术解决了传统搜索的一个主要限制：当购物者使用目录中不存在的单词时，会出现零结果页面。 它利用AI技术，将用户查询和产品数据映射到共享语义空间。 例如，系统识别“跑鞋”和“慢跑运动鞋”是指同一类型的产品，从而启用：

- 同义词识别
- 上下文相关性
- 智能处理模糊、拼写错误或复合查询
- 理解自然的对话语言

若要请求加入Beta计划的邀请，请发送电子邮件至[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)。 Adobe团队将通过后续步骤和资格要求做出响应。

### Cloud Automation修补服务(Private Beta)

[Cloud Automation Patching Service](../tools/caps-tool/intro.md)自动将隔离的安全修补程序应用到Cloud Infrastructure[环境上的](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview)Adobe Commerce。

2025年10月，Cloud Automation Patching Service的Beta版本将添加到[全站点分析工具仪表板](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard)。 此服务通过简化的修补工作流为Commerce项目管理员提供支持，包括：

- 自动安装修补程序
- 回滚恢复
- 部署后验证。

该服务确保您能够以最小的手动操作和风险维护安全、稳定和更新的环境。

Beta版包括以下功能：

- **自动安装修补程序**：简化并自动执行跨环境修补关键漏洞的过程。
- **将风险降至最低**：使用部署后运行状况检查和回滚功能防止站点中断。

>[!NOTE]
>
>由于Cloud Automation Patching Service自动应用独立的安全修补程序，因此您必须具有[参与者或项目管理员角色](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/user-access)才能使用它。

要参与此测试版，请完成并提交[Cloud Automation Patching Service - Beta注册表单](https://forms.office.com/r/3Wfxj5nPdB)。

### IBM Sterling Order Management系统集成(Private Beta)

借助适用于IBM Sterling Order Management的集成加速器，Adobe Commerce客户可以开始使用由IBM Sterling OMS提供支持的高级订单管理功能。 通过此集成，商家可以：

- 实时了解客户的库存水平和准确的交付日期。
- 基于可配置规则的订单自动来源补充，因此您可以优化履行网络和库存。
- 通过单个仪表板跨渠道统一查看订单，以便您的支持团队能够提供卓越的服务并快速识别和处理异常。
- 简化退货管理的模板化退货管理流程。

要参与此测试版，请向[sbieber@adobe.com](mailto:sbieber@adobe.com)发送电子邮件请求。

### Adobe Commerce基础(公共Alpha/Beta)

每个Adobe Commerce Foundation Alpha和测试版都包含在计划发布日期前交付给Adobe Commerce核心代码的所有更改，包括但不限于以下功能区域：

- 最新的安全修复
- 性能改进
- GraphQL改进
- 常规质量错误修复
- 社区贡献
- 支持与[Adobe Commerce服务](https://experienceleague.adobe.com/en/docs/commerce/user-guides/home)的兼容性所需的更改

#### 命名惯例和时间表

Adobe通常会每年发布多次alpha和beta修补程序。

Alpha版本包具有`-alphaX`后缀。 例如，Adobe Commerce 2.4.7 alpha发行版包使用以下命名约定：

- `2.4.7-alpha1`
- `2.4.7-alpha2`

Beta版本包具有`-betaX`后缀。 例如，Adobe Commerce 2.4.7测试版发行包使用以下命名约定：

- `2.4.7-beta1`
- `2.4.7-beta2`

有关即将发布的公共Alpha和Beta版本的日期列表，请参阅[发布计划](schedule.md)。

#### 发布访问权限

Adobe Commerce alpha和beta版本的发布方式与任何其他Adobe Commerce补丁版本相同：作为`https://repo.magento.com`上的编辑器中继包。 源代码在[GitHub](https://github.com/magento/magento2)上可用。

有关详细信息，请参阅[Composer安装快速入门](../installation/composer.md)。

#### 问题报告

Adobe不为alpha和beta版本提供标准的Adobe支持服务。

要提交与Alpha版和Beta版相关的反馈，请按照[GitHub](https://developer.adobe.com/commerce/contributor/guides/code-contributions)上的[常规问题报告流程](https://github.com/magento/magento2)操作。

Adobe会监控针对最新Alpha或Beta版本报告的所有严重问题，并排定在GA发行日期之前需要解决这些问题的优先级。
