---
title: 测试版
description: 了解Adobe Commerce测试版以及如何参与。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: d761bd089fbd2046e993d4652e9e0e2b3c4d2777
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Adobe Commerce测试版

Adobe Commerce测试版程序是一种商户访问预发行版功能和代码、提供反馈以及引导Adobe Commerce未来的方式。 有两种类型的测试版计划：

- 公共测试版：公共测试版计划可供所有Adobe Commerce客户和合作伙伴使用
- 私人测试版：私人测试版计划可能需要根据资格条件获得批准才能参与

>[!IMPORTANT]
>
>Beta版可能包含缺陷，并“按原样”提供，不提供任何形式的担保。 Adobe没有义务维护、更正、更新、更改、修改或以其他方式支持(通过Adobe支持服务或其他方式)测试版。 建议客户谨慎使用，并且不要以任何方式依赖测试版和/或任何随附的文档或材料的正确功能或性能。 Beta版中的功能和API如有更改，恕不另行通知。 因此，使用测试版完全由客户自行承担风险。

## 参与的优势

通过抢先使用Adobe正在开发的功能，客户和合作伙伴将能够提供反馈、制定产品开发方案，并准备在正式发布之前采用新功能。

## 当前测试版计划

请参阅以下部分，了解活动Beta程序的列表。

### IBM Sterling Order Management系统集成（私人测试版）

IBM Sterling Order Management的这项集成加速器使Adobe Commerce客户能够开始使用由IBM Sterling OMS提供支持的高级订单管理功能。 通过此集成，商家可以：
- 实时了解客户的库存水平和准确的交付日期。
- 基于可配置规则的订单自动来源补充，因此您可以优化履行网络和库存。
- 通过单个仪表板跨渠道统一查看订单，以便您的支持团队能够提供卓越的服务并快速识别和处理异常。
- 简化退货管理的模板化退货管理流程。

要参与此测试版，请发送电子邮件请求至 [sbieber@adobe.com](mailto:sbieber@adobe.com).

### 数据连接和Audience Activation（公共测试版）

扩展了Adobe Commerce和Adobe Experience Platform之间的数据共享，以推动提供更强大的个性化体验。 此功能使商家能够：
- 共享Commerce客户配置文件
- 创建自定义属性
- 在Real-Time CDP和Adobe Journey Optimizer中获取Commerce见解
- 支持多个数据集和数据流

要参与此测试版，请发送电子邮件请求至 [DataConnection@adobe.com](mailto:DataConnection@adobe.com).

### Adobe Commerce Foundation（公共测试版）

每个Adobe Commerce Foundation测试版都包括在计划发布日期之前交付给Adobe Commerce核心代码的所有更改，包括但不限于以下功能领域：

- 最新的安全修复
- 性能改进
- GraphQL改进
- 常规质量错误修复
- 社区贡献
- 支持与的兼容性所需的更改 [Adobe Commerce服务](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

#### 命名惯例和时间表

Adobe通常每年发布两次测试版修补程序。

测试版发行包具有 `-betaX` 后缀。 例如，Adobe Commerce 2.4.7测试版发行包使用以下命名约定：

- `2.4.7-beta1`
- `2.4.7-beta2`

请参阅 [发布计划](schedule.md) ，以了解即将发布的公共测试版发布日期。


#### Beta版访问权限

Adobe Commerce测试版的发布方式与任何其他Adobe Commerce补丁版本相同： `https://repo.magento.com`. 源代码位于 [GitHub](https://github.com/magento/magento2).

请参阅 [编辑器安装快速入门](../installation/composer.md) 以了解更多详细信息。

#### 问题报告

Adobe不提供测试版的标准Adobe支持服务。

要提交与测试版相关的反馈，请按照我们 [常规问题报告流程](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) 日期 [GitHub](https://github.com/magento/magento2).

我们的内部团队将监控针对最新测试版报告的所有严重问题，并在GA发布日期之前优先解决这些问题。
