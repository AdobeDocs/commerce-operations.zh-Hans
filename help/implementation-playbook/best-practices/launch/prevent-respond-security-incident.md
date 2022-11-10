---
title: 防止和响应安全事件
description: 了解在云基础架构项目中避免和响应Adobe Commerce安全事件的最佳实践。
role: Admin, Developer, Leader, User
feature-set: Commerce
feature: Best Practices
source-git-commit: bb9b8cc9993a70ea50667f08c8260759ab0f91dc
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---


# 帮助防止和响应安全事件的最佳实践

Adobe Commerce安全机构在 [分担责任](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) 模型。 了解Adobe和您的技术团队应负责哪些工作至关重要。 下面我们总结一下 [安全最佳实践](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf) 以确保项目具有最佳的安全控制，以及如何对安全事件做出最佳响应。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构

## 响应事件

在对安全事件做出响应时，有许多注意事项。 如果您怀疑在云基础架构项目上遇到了Adobe Commerce的最近安全事件，则务必要审核所有管理员用户帐户访问权限，启用高级多重身份验证(MFA)控制，保留关键日志，并查看Adobe Commerce版本的安全升级。

下面详细介绍了更多建议。 它们有助于防止未经授权的访问，并开始进一步的事件分析过程。

## 如何预防安全事件

遵循以下安全最佳实践，主动防止影响您的Adobe Commerce站点和店面的安全事件：

- [启用2FA以进行管理员访问](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
双重身份验证被广泛使用，在同一应用程序上为不同网站生成访问代码是常见的做法。 这可确保只有您才能登录到您的用户帐户。 如果您丢失了密码或机器人猜测了密码，则双重身份验证会添加一层保护。
- [为SSH访问启用MFA](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
在项目上启用MFA后，具有SSH访问权限的云基础架构帐户上的所有Adobe Commerce都必须遵循一个身份验证工作流程，该工作流程需要双重身份验证(2FA)代码或API令牌和SSH证书才能访问环境。
- 升级到最新版本的Adobe Commerce。
Adobe为每个受支持版本发布安全性和功能修补程序Adobe Commerce。
- 设置和使用 [非默认管理员URL](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
Adobe建议您使用唯一的自定义管理员URL，而不是默认URL `admin` 或常用术语，例如 *后端*. 尽管此配置更改不会直接保护您的网站免受已确定的坏主体的侵害，但它可以减少尝试获取未经授权访问权限的脚本的暴露。
- 使用  [`bin/magento config:set` 使用 `lock env` 配置选项](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). 此选项会锁定配置值，以便无法在管理员中对其进行编辑，或者阻止对已锁定的设置进行更改。 使用此选项时，配置更改将写入 `<Commerce base dir>/app/etc/env.php` 文件。
- 设置并运行 [Adobe Commerce安全扫描工具](https://docs.magento.com/user-guide/magento/security-scan.html).
增强的安全扫描功能允许您监视包括PWA在内的每个Adobe Commerce站点，以发现已知的安全风险和恶意软件，并接收补丁更新和安全通知。
- [查看和更新管理员用户访问权限](https://docs.magento.com/user-guide/system/permissions-users-all.html) 和 [安全设置](https://docs.magento.com/user-guide/stores/security-admin.html).
   - 我们建议删除任何旧帐户、未使用帐户或可疑帐户，并为所有管理员用户轮换密码。
   - 查看并更新项目的高级安全设置&lt;。 通过管理员安全配置，您能够向URL添加密钥，要求密码区分大小写，并限制管理员会话的长度，包括密码的生命周期以及在锁定管理员用户帐户之前可进行的登录尝试次数。 为了提高安全性，您可以配置当前会话过期前键盘不活动状态的时长，并要求用户名和密码区分大小写。
- 审核Adobe Commerce [云项目用户](https://devdocs.magento.com/cloud/project/user-admin.html).
我们建议删除任何旧帐户、未使用帐户或可疑帐户，并请用户更改其密码。
- 审核 [SSH密钥](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) 适用于云基础架构上的Adobe Commerce。
我们建议查看、删除和旋转SSH密钥。
- 为管理员实施访问控制列表(ACL)。
您可以结合自定义的Fastly Edge ACL列表 [VCL代码段](https://devdocs.magento.com/cloud/cdn/fastly-vcl-allowlist.html#vcl) 过滤传入请求并允许按IP地址向管理员访问。

## 分析事件

事件分析的第一步是尽可能快地收集尽可能多的事实。 收集有关事件的信息可能有助于确定事件的潜在原因。 Adobe Commerce提供了以下工具来协助您进行事件分析。

- [审核管理员操作日志](https://docs.magento.com/user-guide/system/action-log-report.html).
操作日志报告显示为日志记录启用的所有管理员操作的详细记录。 每条记录都加盖时间戳，并注册用户的IP地址和名称。 日志详细信息包括管理员用户数据以及在操作期间进行的相关更改。
- 使用 [Adobe Commerce工具观察](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
Adobe Commerce观察工具允许您分析复杂问题，以帮助确定根本原因。 您可以花时间关联事件和错误，而不是跟踪不同的数据，以便更深入地了解性能瓶颈的原因。
该工具旨在明确显示一些潜在的站点问题，以帮助您确定根本原因并保持站点的最佳性能。 单击上面Adobe Commerce工具文档的观察链接以访问该工具文档。 文档中有一个部分详细介绍了 **安全性** 选项卡。
- 分析日志 [新旧日志](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). Adobe Commerce on cloud infrastructure Pro项目包括 [新旧日志](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) 服务。 该服务已预配置为聚合暂存和生产环境中的所有日志数据，以将其显示在集中的日志管理仪表板中。
您可以使用New Relic Logs服务完成以下任务：
   - 使用 [新旧查询](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) 搜索聚合的日志数据。
   - 通过New Relic Logs应用程序可视化日志数据。

## 其他信息

- [根本原因分析框架](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
