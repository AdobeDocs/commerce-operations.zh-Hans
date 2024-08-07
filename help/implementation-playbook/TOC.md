---
user-guide-title: 实施行动手册
user-guide-description: 了解规划和实施成功的 Adobe Commerce 网站的策略。
mini-toc-levels: 3
source-git-commit: 36a2a86cbafab1e4913573b1c8431524ba43dc6a
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 12%

---


# 实施行动手册 {#implementation-playbook}

- [概述](overview.md)
- Commerce {#intro}
   - [关于Adobe Commerce](intro/about-commerce.md)
   - [平台开发原则](intro/platform-development.md)
- 项目范围{#project-scope}
   - [知识就是力量](project-scope/knowledge.md)
   - [关键利益相关者](project-scope/key-stakeholders.md)
   - [流程和时间线](project-scope/process-timeline.md)
   - [交付成果](project-scope/deliverables.md)
   - [需求核对清单](project-scope/requirement-checklists.md)
- 开发{#development}
   - [平台工具](development/platform-tools.md)
   - [项目管理工具](development/project-management-tools.md)
   - [项目执行方法](development/delivery.md)
   - [质量控制](development/quality-control.md)
- 规划和治理{#planning}
   - [交付和规划方法](planning/delivery.md)
   - [责任和所有权](planning/ownership.md)
   - [项目治理](planning/governance.md)
- 架构和集成{#architecture}
   - [企业参考](architecture/enterprise-blueprint.md)
   - 全局参考体系结构{#global-reference-architecture}
      - [概述](architecture/global-reference/overview.md)
      - [示例](architecture/global-reference/examples.md)
      - 编辑器开发{#composer}
         - [概述](architecture/global-reference/composer/overview.md)
         - [项目结构](architecture/global-reference/composer/project-structure.md)
         - [提示和技巧](architecture/global-reference/composer/tips-and-tricks.md)
- 基础结构和部署{#infrastructure}
   - [概述](infrastructure/overview.md)
   - 自托管{#self-hosting}
      - [概述](infrastructure/self-hosting/overview.md)
      - [内部部署基础结构](infrastructure/self-hosting/on-premises.md)
      - [安全概念](infrastructure/self-hosting/security-concepts.md)
      - [监测遥测和工具](infrastructure/self-hosting/monitoring-tools.md)
      - [灾难恢复想法](infrastructure/self-hosting/disaster-recovery-ideas.md)
      - [性能提示](infrastructure/self-hosting/performance-tips.md)
   - 云基础架构{#cloud}
      - [概述](infrastructure/cloud/overview.md)
      - [地区](infrastructure/cloud/regions.md)
      - [技术](infrastructure/cloud/technology.md)
      - [安全性和合规性](infrastructure/cloud/security.md)
   - 性能优化{#performance}
      - [典型问题](infrastructure/performance/optimization.md)
      - [基准](infrastructure/performance/benchmarks.md)
      - [Recommendations](infrastructure/performance/recommendations.md)
- 启动准备就绪{#launch}
   - [概述](launch/overview.md)
   - [启动前步骤](launch/pre-launch-steps.md)
   - [启动步骤](launch/launch-steps.md)
   - [Post — 启动步骤](launch/post-launch-steps.md)
- 维护和支持{#maintenance}
   - [概述](maintenance/overview.md)
   - [AdobeManaged Services](maintenance/adobe-managed-services.md)
- 最佳实践{#best-practices}
   - [概述](best-practices/phases.md)
   - 规划{#planning}
      - [概述](best-practices/planning/overview.md)
      - [目录管理](best-practices/planning/catalog-management.md)
      - [站点、商店和商店视图配置](best-practices/planning/sites-stores-store-views.md)
      - [报告配置](best-practices/planning/reporting-configuration.md)
      - [云部署的数据库配置&#x200B;。](best-practices/planning/database-on-cloud.md)
      - [MySQL配置](best-practices/planning/mysql-configuration.md)
      - [Redis服务配置](best-practices/planning/redis-service-configuration.md)
      - [OPcache内存大小](best-practices/planning/opcache-memory-size.md)
      - [Realpath缓存大小](best-practices/planning/realpath-cache-size.md)
      - [扩展](best-practices/planning/extensions.md)
      - [合作伙伴升级](best-practices/planning/partner-escalation.md)
      - [支付存储处理](best-practices/planning/payment-processing-storage.md)
   - 开发{#development}
      - [概述](best-practices/development/overview.md)
      - [一般最佳实践](best-practices/development/general.md)
      - [代码管理](best-practices/development/code-management.md)
      - [代码审查](best-practices/development/code-review.md)
      - [调试](best-practices/development/debugging.md)
      - [异常处理](best-practices/development/exception-handling.md)
      - [Git分支](best-practices/development/git-branching.md)
      - [目录图像大小调整](best-practices/development/catalog-image-resizing.md)
      - [图像优化](best-practices/development/image-optimization.md)
      - [故障排除](best-practices/development/troubleshooting.md)
      - [优化CSS和JS文件](best-practices/development/optimize-css-js-files.md)
      - [私有内容块](best-practices/development/private-content-block-configuration.md)
      - [静态内容部署](best-practices/development/static-content-deployment.md)
      - [修改数据库表](best-practices/development/modifying-core-and-third-party-tables.md)
      - [正在修改核心代码和第三方代码](best-practices/development/modifying-core-and-third-party-code.md)
   - 启动{#launch}
      - [概述](best-practices/launch/overview.md)
      - [配置Web爬网程序](best-practices/launch/robots-txt.md)
      - [保护您的站点和基础架构](best-practices/launch/security-best-practices.md)
   - 维护{#maintenance}
      - [概述](best-practices/maintenance/overview.md)
      - [审核前端性能](best-practices/maintenance/frontend-performance.md)
      - [优化后端性能](best-practices/maintenance/backend-performance.md)
      - [索引器配置](best-practices/maintenance/indexer-configuration.md)
      - [大规模修补](best-practices/maintenance/patching-at-scale.md)
      - [订单处理](best-practices/maintenance/order-processing-configuration.md)
      - [解决数据库性能问题](best-practices/maintenance/resolve-database-performance-issues.md)
      - [响应安全事件](best-practices/maintenance/respond-to-security-incident.md)
      - [正在安排生产站点上的管理员更新](best-practices/maintenance/scheduling-admin-updates-in-production.md)
      - [更新服务](best-practices/maintenance/update-services.md)
      - [升级核对清单](best-practices/maintenance/upgrade-checklist.md)
      - [升级MariaDB的先决条件](best-practices/maintenance/mariadb-upgrade.md)
- [返回操作指南](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)
