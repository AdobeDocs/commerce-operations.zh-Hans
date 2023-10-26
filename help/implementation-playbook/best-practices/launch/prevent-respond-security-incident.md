---
title: 预防和响应安全事件
description: 了解避免和响应Adobe Commerce云基础架构项目中的安全事件的最佳实践。
role: Admin, Developer, Leader, User
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: 19ff1fee74e3c5ece13da49648252b32e549eafd
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 0%

---

# 帮助预防和响应安全事件的最佳实践

Adobe Commerce安全性在 [分担责任](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) 模型。 了解Adobe和技术团队的职责很关键。 以下文章总结了安全最佳实践，以确保您的项目具有最佳安全控制，并且您可以规划对安全事件的最佳响应。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce

## 响应事件

在响应安全事件时，有很多考虑事项。 如果您怀疑近期在云基础架构项目上遇到Adobe Commerce安全事件，请务必审核所有管理员用户帐户访问权限、启用高级多重身份验证(MFA)控制、保留关键日志以及查看Adobe Commerce版本的安全升级。

更多建议详见下文。 它们有助于防止未经授权的访问，并启动进一步事件分析的过程。

## 如何预防安全事件

遵循这些安全最佳实践，主动预防影响Adobe Commerce站点和店面的安全事件：

- [启用2FA以获得管理员访问权限](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
二元身份验证被广泛使用，通常在同一应用程序上为不同的网站生成访问代码。 这样可以确保只有您可以登录到用户帐户。 如果您丢失了密码或机器人猜到了密码，则双重身份验证会增加一层保护。
- [为SSH访问启用MFA](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
在项目上启用MFA后，所有具有SSH访问权限的Adobe Commerce基础架构帐户都必须遵循身份验证工作流，该工作流需要双重身份验证(2FA)代码或API令牌和SSH证书才能访问环境。
- 升级到最新版本的Adobe Commerce。
Adobe会为每个受支持的Adobe Commerce版本发布安全和功能修补程序。
- 设置和使用 [非默认管理员URL](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
Adobe建议您使用唯一的自定义管理员URL，而不是默认的URL `admin` 或常用术语，例如 *后端*. 虽然此配置更改不会直接保护您的站点免受确定性错误操作者的攻击，但它可以减小尝试获得未经授权访问的脚本的暴露程度。
- 通过使用，防止在管理员中编辑或更新配置值  [`bin/magento config:set` CLI命令与 `lock env` 配置选项](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). 此选项会锁定配置值，使其无法在管理员中进行编辑，或者阻止对已锁定的设置进行更改。 使用此选项时，配置更改将写入 `<Commerce base dir>/app/etc/env.php` 文件。
- 设置并运行 [Adobe Commerce安全扫描工具](https://docs.magento.com/user-guide/magento/security-scan.html).
增强的安全扫描允许您监视每个Adobe Commerce站点(包括PWA)，以发现已知的安全风险和恶意软件，并接收修补程序更新和安全通知。
- [查看和更新管理员用户访问权限](https://docs.magento.com/user-guide/system/permissions-users-all.html) 和 [安全设置](https://docs.magento.com/user-guide/stores/security-admin.html).
   - 删除所有旧帐户、未使用的帐户或可疑帐户，并为所有管理员用户轮换密码。
   - 查看并更新项目的高级安全设置&lt;。 Admin安全配置使您能够向URL添加密钥，要求密码区分大小写，并限制管理员会话的长度，包括密码的存留期以及在锁定Admin用户帐户之前允许的登录尝试次数。 为了提高安全性，您可以配置在当前会话过期之前键盘处于非活动状态的长度，并要求用户名和密码区分大小写。
- 审核Adobe Commerce [云项目用户](https://devdocs.magento.com/cloud/project/user-admin.html).
删除任何旧帐户、未使用帐户或可疑帐户，并请求用户更改密码。
- 审核 [SSH密钥](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) 适用于Adobe Commerce的云基础架构。
查看、删除和轮换SSH密钥。
- 为管理员实施访问控制列表(ACL)。
您可以过滤传入请求，并通过实施Fastly Edge ACL列表与自定义内容结合使用，按IP地址配置管理员访问 [VCL代码段](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html).

## 分析事件

事件分析的第一步是尽可能快速地收集尽可能多的事实。 收集有关事件的信息可能会帮助您确定导致该事件的潜在原因。 Adobe Commerce提供以下工具以帮助进行事件分析。

- [审核管理员操作日志](https://docs.magento.com/user-guide/system/action-log-report.html).
操作日志报告显示所有启用日志记录的管理员操作的详细记录。 每个记录都加盖时间戳，并注册用户的IP地址和名称。 日志详细信息包括管理员用户数据以及在操作期间所做的相关更改。
- 使用分析事件 [Adobe Commerce工具的观察结果](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
Adobe Commerce观察工具允许您分析复杂的问题，帮助确定根本原因。 您可以花时间来关联事件和错误，而不是跟踪不同的数据，以便更深入地了解性能瓶颈的原因。
该工具旨在让您清楚地了解一些潜在的站点问题，以帮助您确定根本原因，并使站点保持最佳性能。 单击上面的Adobe Commerce观察工具文档链接以访问工具文档。 文档中有一部分详细介绍可在 **安全性** 选项卡。
- 分析日志 [New Relic日志](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). Adobe Commerce on cloud infrastructure Pro项目包括 [New Relic日志](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) 服务。 该服务已预配置为聚合暂存和生产环境中的所有日志数据，以便在集中式日志管理功能板中显示这些数据。
您可以使用New Relic日志服务完成以下任务：
   - 使用 [New Relic查询](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) 以搜索汇总的日志数据。
   - 通过New Relic日志应用程序可视化日志数据。

## 其他信息

- [根本原因分析框架](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
