---
title: Beta版本
description: 了解Adobe Commerce测试版以及如何参与。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 1c0dd720df944a5784c850a3f4ea63b8984069f1
workflow-type: tm+mt
source-wordcount: '963'
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

### Adobe Commerce Optimizer

Adobe Commerce Optimizer通过高性能店面提升您的电子商务体验，从而提升有机流量、客户参与度和收入。

借助Adobe Commerce Optimizer，您可以：

- 扩大并扩展您的目录，而无需重新规划您的整个商业栈栈。
- 从任何源引入目录数据。
- 定义业务渠道和策略。
- 使用AI和ML创建个性化搜索和推荐。
- 查看重要的产品数据可用性，包括同步状态和店面事件数据，以便准确实施和故障排除。

[了解有关Adobe Commerce Optimizer的更多信息](https://experienceleague.adobe.com/docs/commerce/optimizer/overview.html?lang=zh-Hans)。 如果您有兴趣进一步了解[!DNL Adobe Commerce Optimizer]抢先体验计划，请完成[抢先体验申请表](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4WOxhjY2doZPikS2hIbfmL5UMlhTMTYzVDhPQVFNTUFYUjJHNlRKTE5TWS4u)。

### 增强了实时搜索的搜索功能(公共Beta)

此测试版支持[`productSearch`查询](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/)中的三种新功能：

- **分层搜索** — 在另一个搜索上下文中搜索 — 使用此功能，您最多可以为搜索查询执行两层搜索。 例如：

   - **第1层搜索** — 在“product_attribute_1”上搜索“motor”。
   - **第2层搜索** — 在“product_attribute_2”上搜索“部件号123”。 此示例在结果中搜索“motor”的“部件号123”。

  分层搜索可用于`startsWith`搜索索引和`contains`搜索索引，如下所述：

- **startsWith搜索索引** — 使用`startsWith`索引进行搜索。 此新功能允许：

   - 搜索属性值以特定字符串开头的产品。
   - 配置“结尾为”搜索，以便购物者可以搜索属性值以特定字符串结尾的产品。 要启用“结束于”搜索，需要反向摄取产品属性，并且API调用也应该是一个反向字符串。

- **包含搜索索引** — 使用包含索引搜索属性。 此新功能允许：

   - 在较大的字符串中搜索查询。 例如，如果购物者搜索字符串“HAPE-123”中的产品编号“PE-123”。

      - 注意：此搜索类型不同于现有的[短语搜索](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase)，后者执行自动完成搜索。 例如，如果您的产品属性值为“outdoor pants”，则短语搜索会返回“out pan”的响应，但不会返回“oor ants”的响应。 但是，包含搜索会返回“或蚂蚁”的响应。

这些新条件增强了搜索查询过滤机制以细化搜索结果。 这些新条件不会影响主搜索查询。 要参与测试版，请向[commerce-storefront-services](mailto:commerce-storefront-services@adobe.com)发送电子邮件请求。

要安装实时搜索测试版，请参阅[实时搜索指南](https://experienceleague.adobe.com/zh-hans/docs/commerce/live-search/install#install-the-live-search-beta)。

### IBM Sterling Order Management系统集成(Private Beta)

借助适用于IBM Sterling Order Management的集成加速器，Adobe Commerce客户可以开始使用由IBM Sterling OMS提供支持的高级订单管理功能。 通过此集成，商家可以：

- 实时了解客户的库存水平和准确的交付日期。
- 基于可配置规则的订单自动来源补充，因此您可以优化履行网络和库存。
- 通过单个仪表板跨渠道统一查看订单，以便您的支持团队能够提供卓越的服务并快速识别和处理异常。
- 简化退货管理的模板化退货管理流程。

要参与此测试版，请向[sbieber@adobe.com](mailto:sbieber@adobe.com)发送电子邮件请求。

### Adobe Commerce基础(公共Alpha/Beta)

每个Adobe Commerce Foundation Alpha和测试版都包括在计划发布日期之前交付给Adobe Commerce核心代码的所有更改，包括但不限于以下功能区域：

- 最新的安全修复
- 性能改进
- GraphQL改进
- 常规质量错误修复
- 社区贡献
- 支持与[Adobe Commerce服务](https://experienceleague.adobe.com/zh-hans/docs/commerce/user-guides/home)的兼容性所需的更改

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

要提交与Alpha版和Beta版相关的反馈，请按照[GitHub](https://github.com/magento/magento2)上的[常规问题报告流程](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)操作。

Adobe会监控针对最新Alpha或Beta版本报告的所有严重问题，并排定在GA发行日期之前需要解决这些问题的优先级。
