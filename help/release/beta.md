---
title: Beta版本
description: 了解Adobe Commerce测试版以及如何参与。
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
badgePaas: label="PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于云项目（Adobe管理的PaaS基础架构）和内部部署项目上的Adobe Commerce 。"
badgeSaas: label="SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce as a Cloud Service和Adobe Commerce Optimizer项目（Adobe管理的SaaS基础架构）。"
source-git-commit: bf0f269900468870a1da7b5360548d49e009097c
workflow-type: tm+mt
source-wordcount: '1400'
ht-degree: 0%

---

# Adobe Commerce测试版

适用于[Adobe Commerce产品解决方案](https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions)的Beta程序是商家访问预发行版功能和代码、提供反馈以及引导Adobe Commerce未来的一种方式。 有两种类型的测试版计划：

- 公共Beta：公共Beta计划可供所有Adobe Commerce客户和合作伙伴使用
- Private Beta：私人测试版计划可能需要根据参与资格标准进行审批

>[!IMPORTANT]
>
>**法律免责声明**<br/>
>Beta版本包括预发行版功能和代码，这些功能和代码可能包含缺陷，并“按原样”提供，不提供任何形式的担保。Adobe自行决定是否公开发布Beta版本。Adobe没有义务维护、更正、更新、更改、修改、支持（通过Adobe支持服务或其他方式），或在任何特定日期之前交付此类Beta版本。如果测试版正式发布，则可能需要遵守其他条款和条件，包括适用的费用。Beta版本如有更改，恕不另行通知，包括停止使用。建议客户谨慎使用，并且不要以任何方式依赖测试版的不中断或无错误功能或性能。 因此，使用测试版完全由客户自行承担风险。

## 参与的优势

抢先体验Adobe正在开发的功能可以让客户和合作伙伴提供反馈、制定产品开发方案，并准备在正式发布之前采用新功能。

## 当前的Beta项目

请参阅以下部分，了解活动Beta程序的列表。

### 搜索匹配和排名(Private Beta)

Adobe正在改进产品发现如何对[!DNL Adobe Commerce]上的[!DNL Live Search]和[!DNL Adobe Commerce Optimizer]的搜索结果进行排名。 更新会优先处理&#x200B;**精确和接近短语匹配项**，然后匹配，其中&#x200B;**所有查询词都出现在同一可搜索属性**&#x200B;中，最后&#x200B;**跨字段**&#x200B;匹配（包括支持自动完成样式建议的行为）。 该分层模型可帮助高意图查询首先显示最相关的产品，同时仍会返回有用的替代项。

同一相关性模型与&#x200B;**搜索权重**、**智能排名**、**同义词**&#x200B;和&#x200B;**促销规则**(pin、boost、bury)交互。 德语店面可以将&#x200B;**分解**&#x200B;用于复合单词，其总体优先级方法相同。

**主要优势**

- 更强地促进精确和接近短语匹配（包括规范化形式，如单数和复数）。
- 当所有查询词一起出现在一个可搜索字段中时排名较高。
- 更明确地期望在查询时权重、智能排名和手动规则如何组合。
- 有关验证高值查询和在更改后调整Boost规则的指南。

在[Adobe Commerce Optimizer (SaaS)](https://experienceleague.adobe.com/en/docs/commerce/optimizer/manage-results/search-relevance-matching)和[实时搜索(PaaS)](https://experienceleague.adobe.com/en/docs/commerce/live-search/live-search-admin/search-relevance-matching)中了解有关搜索匹配和排名策略的更多信息。

若要请求此私人测试版的邀请，请发送电子邮件至[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)。 Adobe团队将通过后续步骤和资格要求做出响应。

### 推荐价格过滤器（公共Beta） {#recommendation-price-filters-public-beta}

仅[!BADGE SaaS]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce as a Cloud Service和Adobe Commerce Optimizer项目（Adobe管理的SaaS基础架构）。"}

[!DNL Adobe Commerce Optimizer]将&#x200B;**价格筛选器**&#x200B;添加到产品推荐中，以便在创建或编辑推荐单位时，您可以根据价格包含或排除推荐的产品。 筛选器使用店面的&#x200B;**有效价格手册**&#x200B;中每个产品的&#x200B;**最终计算价格**，包括来自该价格手册的折扣和促销活动（不限于标价）。 价格规则可优化候选集；它们不会重新对产品进行排名。

您可以使用商店的基本货币定义具有固定最小值和最大值的&#x200B;**静态**&#x200B;范围，或者定义产品详细信息页面上的&#x200B;**动态**&#x200B;规则，这些规则将推荐的产品与当前查看的&#x200B;**产品**&#x200B;进行比较，并使用诸如小于或等于、大于或等于之类的运算符，或者在锚价的某个值或百分比范围内的运算符。 动态筛选器可用于在产品上下文中运行的与SKU相关的推荐类型（例如，*查看了这个项目，也查看了*&#x200B;和&#x200B;*更多与此类似的项目*）。

**主要优势**

- 在&#x200B;**筛选产品**&#x200B;步骤中使用包含和排除规则，按价格包含或排除推荐候选项。
- 将静态价格区间用于固定促销目标（例如，预算友好的插件或高级追加销售）。
- 使用产品详细信息页面上的动态价格规则，可显示相对于所查看产品的可比价格范围内的替代产品。
- 将筛选与购物者看到的价格保持一致，这是用于筛选和显示的活动价格手册中的相同最终价格。

若要了解更多信息，请参阅商家指南中的[推荐过滤器 — 价格](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/recommendations/filters#price)和店面放置指南中的[产品推荐设置](https://experienceleague.adobe.com/developer/commerce/storefront/merchants/content-customizations/product-recommendations/)。

若要在使用此测试版功能时分享您的反馈，请发送电子邮件至[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)。

### Cloud Automation修补服务(Private Beta)

仅[!BADGE PaaS]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于云项目（Adobe管理的PaaS基础架构）和内部部署项目上的Adobe Commerce 。"}

[Cloud Automation Patching Service](../tools/caps-tool/intro.md)自动将隔离的安全修补程序应用到Cloud Infrastructure](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview)环境上的[Adobe Commerce。

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

### 商家生产率人工智能助理（公共Beta）

商家生产效率AI助手是一个内嵌在Adobe Commerce管理员中的对话界面，可帮助商家使用自然语言完成日常任务并根据需要访问业务洞察。 它使商家能够直接在其现有工作流程中管理促销、更新产品目录信息和检索运营数据（如最近订单或有效促销）。 该助理还提供上下文指导，以帮助商家更有效地导航和使用管理员。

**主要优势**

- 使用自然语言说明自动执行常见的促销任务，包括促销创建和目录元数据更新。
- 直接在管理工作流中访问上下文帮助和指导。
- 按需查询实时商店数据 — 例如，检索最近10个订单，查看当前有效的促销或检查库存状态。
- 减少在重复性的管理任务上花费的时间，使商家能够专注于战略和增长。

要参与此测试版，请发送电子邮件至[commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com)。

### Adobe Commerce基础（公共Alpha/Beta）

仅[!BADGE PaaS]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于云项目（Adobe管理的PaaS基础架构）和内部部署项目上的Adobe Commerce 。"}

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

要提交与Alpha版和Beta版相关的反馈，请按照[GitHub](https://github.com/magento/magento2)上的[常规问题报告流程](https://developer.adobe.com/commerce/contributor/guides/code-contributions/)操作。

Adobe会监控针对最新Alpha或Beta版本报告的所有严重问题，并排定在GA发行日期之前需要解决这些问题的优先级。
