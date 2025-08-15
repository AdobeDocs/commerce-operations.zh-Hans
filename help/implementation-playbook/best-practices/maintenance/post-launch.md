---
title: 启动后支持和维护
description: 通过我们全面的启动后支持和维护最佳实践，确保Adobe Commerce商店的最佳性能和安全性。
role: Admin, User, Developer
feature: Best Practices
exl-id: f02a13ca-c851-4508-a2bd-e5bc196a330c
source-git-commit: 60444d3ef7208d12af3f06af6e3cab2cae93700b
workflow-type: tm+mt
source-wordcount: '2116'
ht-degree: 0%

---

# Adobe Commerce的启动后支持和维护

上市后支持和维护对于确保Adobe Commerce商店平稳运行、性能良好、安全无虞并继续实现您的业务目标至关重要。 此阶段涉及持续监控、优化、错误修复、更新和用户支持。 以下部分将&#x200B;**启动后支持**&#x200B;划分为关键类别：

## 定期站点监控和性能优化

### 性能监控

- **站点速度和负载测试**： Adobe Commerce可能会占用大量资源，因此定期性能监控至关重要。

   - **要使用的工具**：云基础架构项目上的所有Adobe Commerce都包括对New Relic的访问，这有助于监控Commerce应用程序和云基础架构中的性能并调查事件。 其他工具包括Google PageSpeed Insights和GTMetrix。

   - **要监视的项目**：以下是云基础架构上要监视的Adobe Commerce的主要项目：

      - **运行状况通知**：磁盘空间和环境运行状况警报。

      - **观察**：综合监视组合来自多个源的日志数据，以实现有效的站点管理。

      - **New Relic服务**：监视暂存和生产中的性能，侧重于关键量度。

      - **托管警报策略**：跟踪具有预定义阈值的量度，以触发影响性能的基础结构或应用程序问题的通知。

  >[!TIP]
  >
  >请参阅[云指南](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/monitor/performance)中的&#x200B;_性能监视_。


- **优化数据库性能**：要在Adobe Commerce Cloud中优化数据库性能，请实施以下操作：

   - **监视和优化MySQL查询**：识别并解决运行缓慢的查询，可以使用MySQL的SHOW FULL PROCESSLIST和EXPLAIN命令完成此操作。 对于更复杂的设置，Pro体系结构用户可以利用Percona Toolkit分析查询日志以了解性能问题。

   - **索引管理**：确保每个表都有一个主键并删除任何重复的索引，因为这样会降低效率，并在同时写入时导致冲突。

   - **Cron作业优化**：应将Cron作业安排在非高峰时段，以将对性能的影响降至最低，尤其是在频繁执行索引等后台任务的情况下。

  >[!TIP]
  >
  >请参阅[解决数据库性能问题的最佳实践](resolve-database-performance-issues.md)。

- **监视CDN**：若要在Adobe Commerce Cloud中监视Fastly CDN性能，可以执行以下操作：

   - **利用New Relic进行监控**： Adobe Commerce提供New Relic功能，可监控暂存和生产环境中的Fastly性能及其他指标。 此工具可深入分析一段时间内的服务器运行状况、CDN缓存和网络请求，从而帮助识别模式并优化CDN设置。

   - **Fastly日志分析**：对于Adobe Commerce Cloud Pro项目，您可以使用New Relic日志来查看和分析Fastly CDN和WAF日志数据，以跟踪性能趋势、安全事件并诊断错误或延迟问题。

   - **使用cURL命令**：运行带有Fastly特定标头的cURL命令来检查网站的缓存状态。 关键响应标头包括`X-Cache` (HIT/MISS)、`Fastly-Module-Enabled`、`Fastly-Magento-VCL-Uploaded`和`Cache-Control`以验证缓存和模块状态。 Adobe为暂存环境和生产环境提供了示例cURL命令。

   - **检查标头信息**：检查标头（如`Cache-Control`、`Pragma`和`X-Magento-Tags`）以确认对缓存的内容执行适当的缓存行为和标记处理。 正确的标头值指示缓存配置是否在CDN间得到有效应用。

   - **Fastly调试和测试**：使用Fastly的调试功能识别并解决缓存HIT和MISS率、缓存逻辑或标头响应不正确的问题，这些问题可能指向配置问题或与预期的缓存规则不一致。

这些监控步骤有助于保持最佳的CDN性能，并解决影响站点速度和可靠性的问题。

>[!TIP]
>
>请参阅[云指南](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/cdn/fastly)中的&#x200B;_Fastly服务概述_。

#### 定期安全监控

为了在Adobe Commerce Cloud中维护常规安全监控，Adobe建议采用多层面的方法，其中涉及持续扫描、日志记录和主动安全实践。 以下是确保持续安全的一些核心操作：

- **安全扫描**：使用Adobe的安全扫描工具监视Commerce站点上的已知漏洞和恶意软件。 此工具可针对潜在的安全风险和合规性问题发出警报。

- **定期修补程序和更新维护**：在有Adobe的安全修补程序和更新可用时应用这些修补程序和更新。 升级到最新的Adobe Commerce版本可确保针对威胁进行最新的防御。

- **审核和日志监控**：利用New Relic Logs（适用于Pro项目）等工具集中和分析来自暂存环境和生产环境的安全日志，增强潜在安全问题和违规的可见性。

- **帐户和访问管理**：定期审核用户和管理员帐户以删除任何未经授权或已过期的帐户。 通过针对管理员用户的多重身份验证(MFA)加强访问控制。

- **Web应用程序防火墙(WAF)**：使用集成的Fastly WAF检测和缓解来自恶意通信模式的威胁，例如未经授权的数据提取尝试。

- **自定义代码和扩展安全性**：通过定期执行代码审核并将扩展限制为Adobe审核的扩展来保护任何自定义代码或第三方扩展。

>[!TIP]
>
>请参阅[管理员系统指南](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/security/security)中的&#x200B;_安全性_。

#### 错误日志记录和监控

为了监控Adobe Commerce Cloud中的错误日志记录，Adobe提供了多种工具和实践，以有效进行故障排除和性能管理：

- **使用New Relic进行日志聚合**： New Relic从Adobe Commerce应用程序中收集并集中日志，包括与基础架构、CDN和WAF相关的日志。 这种设置允许简化错误跟踪、创建功能板和查询日志，以便更深入地了解应用程序性能和问题。 访问New Relic日志可按各种属性搜索和筛选日志，以便快速诊断问题。

- **错误日志类型**： Adobe Commerce Cloud中的密钥错误日志包括`cloud.log`和`cloud.error.log`，前者包含部署反馈，后者记录部署警告和错误。 用于调试的其他特定日志包括`debug.log`、`system.log`和`exception.log`，其中每个日志在整个Commerce平台的错误和事件跟踪中提供不同的角色。

- **使用Monolog进行自定义日志记录**： Adobe Commerce支持通过Monolog进行自定义日志记录，这允许开发人员将日志消息定向到各种目标，如文件、数据库甚至警报。 此灵活性对于构建高级日志记录策略非常有用，可满足开发和生产环境中的不同监控需求。

- **使用站点范围分析工具进行异常监视**：站点范围分析工具可帮助监视和管理异常日志，识别部署和应用程序事件中重复出现的问题。 此工具会突出显示常见问题，从而更轻松地确定优先顺序并解决影响性能的关键问题。

>[!TIP]
>
>有关Adobe Commerce Cloud中的日志记录和错误跟踪实践的更多详细信息，请参阅[New Relic日志管理](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management)和[异常监控](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/site-wide-analysis-tool/exceptions)。

### 安全和更新

#### 安全补丁和更新

为了保持更新并确保Adobe Commerce Cloud系统的安全性，以下是监控安全补丁和更新的一些关键实践：

- **订阅Adobe Commerce安全警报**：通过[注册来自Adobe的通知](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/systems/security/security)，随时了解安全漏洞。

- **检查发行说明**：定期查看[安全修补程序发行说明](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/release/notes/security-patches/overview)，这些发行说明在版本（如2.3.5-p1）中标记为“ — pN”，并包含关键修复和改进。

- **立即应用安全修补程序**：一旦有安全修补程序可用，立即应用安全修补程序。 这包括更新到最新版本或应用特定的修补程序文件。

- **使用云修补程序**：对于Adobe Commerce Cloud，可以在云工具包中捆绑安全修补程序。 请确保升级该套件或Commerce版本以接收这些修复。

- **自动修补程序管理**：考虑使用集中式修补程序等工具来[自动跨多个存储区管理和应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale)。

>[!TIP]
>
>有关应用修补程序和维护安全性的更多详细信息和分步说明，请参阅[安全修补程序发行说明](../../../release/release-notes/security/overview.md)和[如何应用安全修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches)。 您还应查看[全站点分析工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/site-wide-analysis-tool/access)报告。

#### PCI合规性

要确保Adobe Commerce Cloud中的PCI合规性，请遵循以下关键实践：

- **保护持卡人数据**：不要在Adobe Commerce中存储持卡人数据。 如果需要存储，请使用加密和标记化的方法来保护存储。

- **使用安全传输协议**：始终通过诸如TLS之类的安全协议传输付款数据，同时进行加密和适当的密钥管理。

- **利用Web应用程序防火墙(WAF)**： Fastly-powered WAF服务可在恶意流量到达您的网站之前阻止恶意流量，从而帮助满足PCI DSS 6.6要求并抵御常见漏洞。 在[此处](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage)和[此处](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service)查看更多信息。

- **限制访问**：确保只有授权人员才能访问敏感付款数据，并[应用访问控制以降低暴露风险](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage)。

- **常规安全扫描**：执行常规PCI ASV扫描和[监视环境](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/security-and-compliance/shared-responsibility)以解决潜在漏洞。

>[!TIP]
>
>有关维护Adobe Commerce PCI合规性的更详细准则，请参阅[付款处理和存储的最佳实践](../planning/payment-processing-storage.md)。

### 用户和客户支持

#### 设置

- **支持渠道**：实施客户支持渠道，例如：

   - **实时聊天**：提供实时聊天支持以立即获得帮助。 流行的解决方案包括Zendesk、Intercom和Tidio。

   - **电子邮件支持**：使用Freshdesk或Zoho Desk等支持票证系统有效管理客户查询。

   - **电话支持**：如果您有大量客户，请考虑在工作时间提供电话支持。

#### 管理员用户培训

- **内部培训**：培训您的员工如何使用Adobe Commerce管理员、处理订单、管理产品和处理客户服务问题。

- **文档**：维护内部知识库或用户手册，以了解常见问题(FAQ)、故障排除和常见任务。

#### 客户体验优化

- **调查和反馈**：使用调查收集客户反馈并优化客户体验。 Adobe Commerce支持与SurveyMonkey或Google Forms等工具的集成。

- **审核管理**：管理客户对您产品的审核和评级。 鼓励快乐的客户离开审阅，同时恰当地响应负面评论。

- **Personalization**：实施个性化功能，如个性化产品推荐或定向促销。

### 日常存储维护和优化

#### 搜索引擎优化(SEO)

- **内容优化**：定期更新产品描述、博客文章和类别页面，以使内容保持最新状态并与搜索引擎相关。

- **SEO审核**：使用Google Search Console或Screaming Frog等工具执行常规SEO审核，以识别SEO问题（例如，链接损坏、缺少元数据、内容重复）。

- **URL结构**：保持简洁的逻辑URL结构，并确保没有断开的链接或重定向。

#### 转化率优化(CRO)

- **A/B测试**：对不同的页面元素（如产品页面或结账流程）运行A/B测试以提高转化率。

- **购物车放弃**：实施购物车放弃电子邮件促销活动或退出意图弹出窗口，以恢复失去的销售额。

- **签出优化**：通过减少步骤数并提供来宾签出以提高转化率来简化您的签出过程。

#### 营销集成

- **电子邮件营销活动**：为欢迎电子邮件、放弃的购物车电子邮件和购买后跟进设置自动电子邮件营销流程。 Adobe Marketo、Mailchimp或Klaviyo等平台可与Adobe Commerce很好地集成。

- **社交媒体和广告集成**：与Facebook、Instagram和Google Ads等平台集成，以运行有针对性的营销活动并跟踪效果。

#### 移动优化

- **移动响应能力**：定期测试您网站的移动响应能力和可用性。 鉴于移动商务正在增长，移动优先方针对于持续成功至关重要。

- **移动性能**：使用Google的移动友好测试和性能工具优化您的移动商店体验。

### 扩展和新功能开发

- **自动缩放流量处理**：

   - Adobe Commerce Cloud支持自动缩放，以根据实时流量需求动态调整服务器资源（例如Web节点），从而确保您的商店无需手动干预即可处理高访客量。 请参阅[云指南](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/architecture/autoscaling)中的&#x200B;_自动缩放_。

   - Web层和服务层可以独立扩展，添加更多Web节点以增加流量，并扩展数据库或服务节点以在高峰期实现后端性能。 请参阅[云指南](https://experienceleague.adobe.com/zh-hans/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture)中的&#x200B;_缩放架构_。

- **性能监视**：

   - 使用&#x200B;**New Relic**&#x200B;监控实时性能指标(如CPU使用情况、流量级别)并根据需要进行调整。

   - 在缩放之前在暂存环境中测试性能以避免生产中出现问题。

- **新功能的开发**：

   - 集成高级功能，如&#x200B;**AI驱动的个性化**、**订阅管理**&#x200B;和自定义解决方案。

   - 在部署到生产环境之前，在暂存环境中不断测试和优化功能，以将停机时间降至最低。

- **正在进行站点维护**：

   - 定期查看系统日志和性能量度，以找出需要改进的方面。

   - 确保基础架构保持可扩展并适应新的业务需求和增长。

>[!TIP]
>
>有关详细指导，请参阅[维护最佳实践](overview.md)、[个性化](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization)和[功能开发](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization)。

### 报告和分析

- **Adobe Commerce Intelligence：** Commerce Intelligence是Adobe Commerce的一项核心功能，可提供跨多个数据源的最佳实践见解，从而允许商家做出科学的数据驱动型决策并采取清晰、知情的操作。 请参阅&#x200B;[_Commerce Intelligence用户指南_](https://experienceleague.adobe.com/zh-hans/docs/commerce-business-intelligence/mbi/getting-started)。

- **Adobe Analytics：** Adobe Analytics提供了一个强大的解决方案，用于跟踪、分析和优化您的在线商店的性能。 Adobe Analytics帮助电子商务企业更深入地了解客户行为、产品表现、转化率和其他关键指标，从而实现数据驱动型决策。

- **Google Analytics：**&#x200B;使用Google Analytics跟踪客户行为、流量源和转化率。

- **其他Commerce Intelligence工具：** Adobe Commerce包含高级报告。 此功能允许您访问基于您的产品、订单和客户数据的一组动态报告，以及针对您的业务需求定制的个性化仪表板。有关详细信息，请参阅[管理员用户指南](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting)中的&#x200B;_高级报告_。

### 结论

启动后支持和维护是一项持续的工作，需要定期关注这些工作，以确保您的Adobe Commerce商店持续正常运行、保持安全并适应您的业务需求。 实施结构化网站监控、客户支持、优化和更新方法对长期成功至关重要。
