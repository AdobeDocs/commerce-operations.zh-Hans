---
title: 升级清单最佳实践
description: 了解如何创建并使用升级核对清单来规划Adobe Commerce升级策略。
role: Leader
feature: Best Practices
exl-id: c9b644fa-290c-4f33-b5a7-19f7122ff08e
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# 升级清单最佳实践

在与您的电子商务团队进行年度和季度对话时使用此清单。 许多公司根据年度预算和路线图开展工作。 在这些年度讨论中，您一定要谈论平台的运行状况、方向和年度升级策略，以及它如何适应业务的总体目标和KPI。 在季度对话中，请确保您创建的年度计划仍然与您的当前情况保持一致，或者如果不一致，请重点考虑问题。 此升级计划核对清单的目标是帮助您规划和安排Adobe Commerce升级，以确保在年内成功升级。 此核对清单旨在由以下受众用于年度规划和季度审查：

- Director/IT经理
- 电子商务管理器
- 解决方案合作伙伴/顾问

>[!NOTE]
>
>有关成功升级的技术步骤的详细说明，请参阅 [完成升级先决条件](../../../upgrade/prepare/prerequisites.md) 在我们的用户文档中。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 目标

▢查看当前KPI并根据需要进行调整。

## 扩展和自定义

▢查看所有当前的扩展和自定义项，确保根据业务需求仍然需要它们。

▢请考虑替换任何在Adobe Commerce版本中不具备良好跟踪记录的扩展。

## 团队

▢确保您拥有适当的团队，以及适当的Adobe Commerce认证和技能组合。

## 预算和时间

▢使用Adobe Commerce [发布计划](../../../release/schedule.md) 以计划下次升级并提前准备。

▢根据预期需求，讨论您认为将采用哪个版本（完全版本或仅限安全版本）。

▢为升级预留预算和团队容量。

## 第三方集成

▢查看当前的Adobe Commerce第三方集成及其年度维护时段，并考虑将升级工作与维护计划保持一致。

## 范围和部署规划

▢早访问活动

- 合作伙伴参与 [测试版](../../../release/beta.md)
- 测试版发行说明审查。

▢就预算、时间表和范围达成一致。

▢运行 [升级兼容性工具](../../../upgrade/upgrade-compatibility-tool/overview.md)

▢考虑使用升级来解决 [站点范围分析工具](../../../tools/site-wide-analysis-tool/intro.md).

▢文档依赖项和所需的任何技术栈栈更改，如PHP或Elastic Search版本。

▢收集具有Adobe Commerce认证的项目团队。

▢制定利益相关者沟通计划。

▢如果预计停机，则计划维护时段。

▢审查和批准测试策略；考虑使用Adobe Commerce [测试框架](https://developer.adobe.com/commerce/testing/) 或第三方自动化套件。

▢确认所有扩展和自定义项都兼容。

▢查看并更新启动后的行动手册；在升级期间或升级后发现问题时使用。

## 部署后

▢监测站点是否存在问题 — 性能、订单处理、分析等。

▢执行Adobe Commerce [安全扫描](https://account.magento.com/scanner/dashboard/) 或其他第三方扫描并审查潜在的安全漏洞。

▢与所有利益相关者一起回顾并记录哪些方面进展顺利、哪些方面未进展以及如何改进。

▢用汲取的经验教训修改您的下次升级计划。
