---
title: 响应安全事件
description: 通过遵循最佳实践处理安全事件，以响应和修复影响站点可用性和性能的安全问题。
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: e63f68dd469564e70269154810cbfbd95d2b2e57
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 0%

---

# 应对安全事件的最佳实践

以下文章总结了响应安全事件和修复影响Adobe Commerce站点可用性、可靠性和性能的问题的最佳实践。

遵循这些最佳实践有助于防止未经授权的访问和恶意软件攻击。 如果确实发生了安全事件，这些最佳实践可帮助您准备立即响应、执行根本原因分析并管理修正过程以恢复正常操作。

>[!TIP]
>
>Adobe发现，大多数安全事件都发生在威胁行为者利用Commerce应用程序和基础架构配置中现有的未修补漏洞、较差的密码以及较弱的所有权和权限设置时。 在设置、配置和更新Adobe安装时，通过查看并遵循Adobe Commerce安全最佳实践来最大限度地减少安全事件的发生。 查看[保护您的Commerce站点和基础架构](../launch/security-best-practices.md)。


## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md)，共：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 响应事件

如果您怀疑云基础架构项目上的Adobe Commerce受到安全事件的影响，重要的首要步骤是：

- 审核所有管理员用户帐户访问权限
- 启用高级多重身份验证(MFA)控制
- 保留关键日志
- 查看您的Adobe Commerce版本的安全升级。

更多建议详见下文。

## 发生攻击时立即采取措施

万一发生站点损坏的不幸事件，请遵循以下主要建议：

- 请您的系统集成商和适当的安全人员参与调查和补救工作。

- 确定攻击的范围：
   - 是否访问过信用卡信息？
   - 哪些信息被盗？
   - 妥协后已经过了多少时间？
   - 信息是否加密？

- 通过查看服务器日志文件和文件更改，尝试查找攻击向量，以确定网站何时遭到破坏，以及如何遭到破坏。

   - 在某些情况下，建议擦除并重新安装所有内容，或者在虚拟托管的情况下创建一个新实例。 恶意软件可能隐藏在不受怀疑的位置，只是等待自我恢复。

   - 删除所有不必要的文件。 然后，从已知干净的来源重新安装所需的文件。 例如，您可以使用版本控制系统中的文件或Adobe中的原始分发文件来重新安装。

   - 重置所有凭据，包括数据库、文件访问、付款和送货集成、Web服务以及管理员登录。 同时重置所有可能用于攻击系统的集成和API密钥和帐户。

## 分析事件

事件分析的第一步是尽可能快速地收集尽可能多的事实。 收集有关事件的信息有助于确定事件的潜在原因。 Adobe Commerce提供以下工具以帮助进行事件分析。

- [审核管理员操作日志](https://experienceleague.adobe.com/docs/commerce-admin/systems/action-logs/action-log-report.html?lang=zh-Hans)。

  操作日志报告显示所有启用日志记录的管理员操作的详细记录。 每个记录都加盖时间戳，并注册用户的IP地址和名称。 日志详细信息包括管理员用户数据以及在操作期间所做的相关更改。

- 使用Adobe Commerce工具[的](../../../tools/observation-for-adobe-commerce/intro.md)观察分析事件。

  Adobe Commerce观察工具允许您分析复杂的问题，帮助确定根本原因。 您可以花时间来关联事件和错误，而不是跟踪不同的数据，以便更深入地了解性能瓶颈的原因。

  使用工具中的&#x200B;**安全性**&#x200B;选项卡可清楚地了解潜在的安全问题，从而帮助确定根本原因并保持网站性能处于最佳状态。

- 使用[New Relic日志](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html?lang=zh-Hans)分析日志

  云基础架构Pro项目上的Adobe Commerce包括[New Relic日志](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management.html?lang=zh-Hans)服务。 该服务已预配置为汇总暂存和生产环境中的所有日志数据，以便在集中式日志管理功能板中显示这些数据，您可以在其中搜索和可视化汇总的数据。

  对于其他Commerce项目，您可以设置并使用[New Relic日志](https://docs.newrelic.com/docs/logs/get-started/get-started-log-management/)服务来完成以下任务：
   - 使用[New Relic查询](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs)搜索聚合日志数据。
   - 通过New Relic日志应用程序可视化日志数据。

## 审核帐户、代码和数据库

查看Commerce管理员和用户帐户、应用程序代码以及数据库配置和日志，以识别和清理可疑代码，并确保帐户、站点和数据库访问的安全。 然后，根据需要重新部署。

发生事件后继续密切监视站点，因为许多站点在数小时内再次受到威胁。 确保持续进行日志审查和文件完整性监控，以快速发现任何新的损坏迹象。

### 审核管理员用户帐户

- [查看管理员用户访问权限](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html?lang=zh-Hans) — 删除旧的、未使用的或可疑的帐户，并为所有管理员用户轮换密码。

- [查看管理员安全设置](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=zh-Hans) — 验证管理员安全设置是否遵循安全最佳实践。

- [在云基础架构项目中检查Adobe Commerce的用户帐户](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=zh-Hans) — 删除旧的、未使用的或可疑的帐户，并为所有云项目管理员用户轮换密码。 确保正确配置帐户安全设置。

- 在云基础架构上[审核Adobe Commerce的SSH密钥](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=zh-Hans) — 审核、删除和轮换SSH密钥。

### 审核代码

- 从管理员中，查看所有范围级别（包括[和](https://experienceleague.adobe.com/docs/commerce-admin/content-design/design/page-setup.html?lang=zh-Hans)）的`website`HTML页眉和页脚配置`store view`。 从脚本和样式表中删除任何未知的JavaScript代码，以及其他HTML设置。 仅保留已识别的代码，例如跟踪片段。

- 将当前的生产代码库与版本控制系统(VCS)中存储的代码库进行比较。

- 隔离任何可疑代码。

- 通过将代码库重新部署到生产环境，确保没有可疑代码的残留。

### 审核数据库配置和日志

- 查看任何存储过程以进行修改。

- 验证数据库是否只能由Commerce实例访问。

- 使用公开可用的恶意软件扫描工具扫描网站，验证恶意软件是否不再存在。

- 通过更改管理员面板的名称并验证站点`app/etc/local.xml`和`var` URL是否不可公开访问来保护该面板。

- 发生事件后继续密切监视站点，因为许多站点在数小时内再次受到威胁。 确保持续进行日志审查和文件完整性监控，以快速发现任何新的损坏迹象。

## 删除Google警告

如果Google已将该站点标记为包含恶意代码，则请在清理完该站点后请求审查。 审查感染了恶意软件的站点需要几天时间。 在Google确定站点干净后，搜索结果中的警告和浏览器应会在72小时内消失。 请参阅[请求审阅](https://web.dev/articles/request-a-review)。

## 查看恶意软件结果核对清单

如果公开可用的恶意软件扫描工具确认存在恶意软件攻击，请调查该事件。 与解决方案集成商合作，清除现场并遵循建议的修复流程。

## 执行其他审核

处理复杂的攻击时，最好的做法是与经验丰富的开发人员、第三方专家或解决方案集成商合作，全面修复站点并审查安全实践。 与经验丰富的安全专业人士合作，可确保采取全面而先进的措施，确保您的企业及其客户的安全。

## 其他信息

- [根本原因分析框架](https://sansec.io/kb/incident-response/magento-root-cause-analysis)。
