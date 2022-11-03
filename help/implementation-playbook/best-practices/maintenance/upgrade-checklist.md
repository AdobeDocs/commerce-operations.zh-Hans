---
title: 升级核对清单最佳实践
description: 了解如何创建和使用升级核对清单来规划Adobe Commerce和Magento Open Source升级策略。
role: Leader
feature: Best Practices
feature-set: Commerce
source-git-commit: 644970b350c7591896f7c00d4c94661c76495c73
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---


# 升级核对清单最佳实践

在与您的电子商务团队进行年度和季度对话时使用此核对清单。 许多公司从年度预算和路线图中开展工作。 在这些年度讨论中，您必须介绍您的平台在本年度的运行状况、方向和升级策略，以及该策略如何适应业务的总体目标和KPI。 在每季度对话中，确保您创建的年度计划与当前情况保持一致，或者如果不符合，则重新引导。 此升级计划核对清单旨在帮助您计划和计划Adobe Commerce升级，以确保在年内成功升级。 以下受众将使用此核对清单进行年度规划和季度审核：

- Director / Manager IT
- 电子商务经理
- 解决方案合作伙伴/顾问

>[!NOTE]
>
>有关成功升级的技术步骤的详细说明，请参阅 [完成升级先决条件](../../../upgrade/prepare/prerequisites.md) （位于我们的用户文档中）。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 目标

▢审查当前KPI并根据需要进行调整。

## 扩展和自定义

▢查看所有当前扩展和自定义，并根据业务需求确保仍然需要这些扩展和自定义。

▢请考虑替换任何没有良好记录且无法使用Adobe Commerce版本保持最新的扩展。

## 团队

▢确保您拥有适当的Adobe Commerce认证和技能组，并拥有适当的团队。

## 预算和时间

▢使用Adobe Commerce [发布计划](../../../release/schedule.md) 计划下次升级并提前做好准备。

▢根据预期需求讨论您认为将采用的版本（完整版或仅安全版）。

▢为升级预留预算和团队容量。

## 第三方集成

▢查看当前Adobe Commerce第三方集成及其本年度维护时段，并考虑将升级工作与您的维护计划保持一致。

## 范围和部署规划

▢抢先体验活动

- 合作伙伴参与 [Beta](../../../release/beta-program.md)
- 测试版发行说明审阅。

▢就预算、时间表、范围达成一致。

▢运行 [升级兼容性工具](../../../upgrade/upgrade-compatibility-tool/overview.md)

▢考虑使用升级来解决 [站点范围分析工具](../../../tools/site-wide-analysis-tool/intro.md).

▢记录依赖项和所需的任何技术堆栈更改，如PHP或Elastic Search版本。

▢收集具有Adobe Commerce认证的项目团队。

▢制定利益相关方沟通计划。

▢计划维护时间（如果预计会出现停机）。

▢审查并批准测试策略；考虑使用Adobe Commerce [测试框架](https://developer.adobe.com/commerce/testing/) 或第三方自动化套件。

▢确认所有扩展和自定义项都兼容。

▢审查和更新启动后的手册；在升级期间或升级后发现问题时使用。

## 部署后

▢监控网站以了解问题 — 性能、订单处理、分析等。

▢执行Adobe Commerce [安全扫描](https://account.magento.com/scanner/dashboard/) 或其他第三方扫描并审查潜在的安全漏洞。

▢与所有利益相关方进行回顾，记录哪些项目运行良好、哪些项目未运行以及如何改进。

▢利用汲取的经验教训修改您的下一次升级计划。
