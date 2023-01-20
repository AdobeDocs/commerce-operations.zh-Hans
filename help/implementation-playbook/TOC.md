---
user-guide-title: 实施行动手册
user-guide-description: 了解规划和实施成功的 Adobe Commerce 网站的策略。
mini-toc-levels: 3
source-git-commit: 338a99f4f047640ac4bb944ac8599301cba5f646
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 6%

---


# 实施行动手册 {#implementation-playbook}

- [概述](overview.md)
- 商务 {#intro}
   - [关于Adobe Commerce](intro/about-commerce.md)
   - [平台开发原则](intro/platform-development.md)
- 项目范围 {#project-scope}
   - [知识就是力量](project-scope/knowledge.md)
   - [主要利益相关方](project-scope/key-stakeholders.md)
   - [流程和时间表](project-scope/process-timeline.md)
   - [交付项](project-scope/deliverables.md)
   - [要求核对表](project-scope/requirement-checklists.md)
- 开发 {#development}
   - [平台工具](development/platform-tools.md)
   - [项目管理工具](development/project-management-tools.md)
   - [项目实施方法](development/delivery.md)
   - [质量控制](development/quality-control.md)
- 规划和治理 {#planning}
   - [交付和规划方法](planning/delivery.md)
   - [责任和所有权](planning/ownership.md)
   - [项目管理](planning/governance.md)
- 架构和集成 {#architecture}
   - [功能](architecture/capabilities.md)
   - [集成策略](architecture/integration-strategy.md)
   - [可扩展性策略](architecture/extensibility-strategy.md)
   - [集成选项](architecture/integration-options.md)
   - [全局参考架构](architecture/global-reference.md)
   - 无头商务 {#headless}
      - [优点](architecture/headless/benefits.md)
      - [历程到无头](architecture/headless/journey-to-headless.md)
      - [微服务](architecture/headless/microservices.md)
      - [无头进化](architecture/headless/evolution.md)
      - [耦合式店面结构](architecture/headless/legacy-storefront.md)
      - [无头架构](architecture/headless/adobe-commerce.md)
- 基础架构和部署 {#infrastructure}
   - [概述](infrastructure/overview.md)
   - [内部基础设施](infrastructure/on-premises.md)
   - 云基础架构 {#cloud}
      - [概述](infrastructure/cloud/overview.md)
      - [地区](infrastructure/cloud/regions.md)
      - [技术](infrastructure/cloud/technology.md)
      - [环境](infrastructure/cloud/environments.md)
      - [托管服务](infrastructure/cloud/managed-services.md)
      - [安全性和合规性](infrastructure/cloud/security.md)
   - 性能优化 {#performance}
      - [典型问题](infrastructure/performance/optimization.md)
      - [基准](infrastructure/performance/benchmarks.md)
      - [Recommendations](infrastructure/performance/recommendations.md)
- 启动就绪 {#launch}
   - [概述](launch/overview.md)
   - [启动前步骤](launch/pre-launch-steps.md)
   - [启动步骤](launch/launch-steps.md)
   - [启动后步骤](launch/post-launch-steps.md)
- 维护和支持 {#maintenance}
   - [概述](maintenance/overview.md)
   - [Adobe Managed Services](maintenance/adobe-managed-services.md)
- 最佳实践 {#best-practices}
   - [概述](best-practices/phases.md)
   - 规划 {#planning}
      - [概述](best-practices/planning/overview.md)
      - [站点、存储和存储视图配置](best-practices/planning/sites-stores-store-views.md)
      - [报表配置](best-practices/planning/reporting-configuration.md)
      - [云部署的数据库配&#x200B;置](best-practices/planning/database-on-cloud.md)
      - [MySQL从连接配&#x200B;置](best-practices/planning/configure-mysql-slave-connection-on-cloud.md)
      - [MySQL触发器用法](best-practices/planning/mysql-triggers-usage.md)
      - [Redis服务配置](best-practices/planning/redis-service-configuration.md)
      - [OPcache内存大小](best-practices/planning/opcache-memory-size.md)
      - [Realpath缓存大小](best-practices/planning/realpath-cache-size.md)
      - [类别](best-practices/planning/category-limits.md)
      - [产品](best-practices/planning/product-sku-limits.md)
      - [产品变量](best-practices/planning/product-variations.md)
      - [产品选项](best-practices/planning/product-options.md)
      - [产品属性](best-practices/planning/product-attributes-and-options.md)
      - [产品列表分页](best-practices/planning/product-listing-pagination.md)
      - [产品购物车限制](best-practices/planning/product-cart.md)
      - [促销活动](best-practices/planning/product-cart-promotions.md)
      - [扩展](best-practices/planning/extensions.md)
      - [合作伙伴升级](best-practices/planning/partner-escalation.md)
      - [支付存储处理](best-practices/planning/payment-processing-storage.md)
   - 开发 {#development}
      - [概述](best-practices/development/overview.md)
      - [图像优化](best-practices/development/image-optimization.md)
      - [疑难解答](best-practices/development/troubleshooting.md)
      - [优化CSS和JS文件](best-practices/development/optimize-css-js-files.md)
      - [专用内容块](best-practices/development/private-content-block-configuration.md)
      - [静态内容部署](best-practices/development/static-content-deployment.md)
      - [修改数据库表](best-practices/development/modifying-core-and-third-party-tables.md)
   - Launch {#launch}
      - [概述](best-practices/launch/overview.md)
      - [Adobe安全通知服务](best-practices/launch/security-notification-service.md)
      - [配置robots.txt文件](best-practices/launch/robots-txt.md)
      - [预防和应对安全事件](best-practices/launch/prevent-respond-security-incident.md)
   - 维护 {#maintenance}
      - [概述](best-practices/maintenance/overview.md)
      - [审核前端绩效](best-practices/maintenance/frontend-performance.md)
      - [索引器配置](best-practices/maintenance/indexer-configuration.md)
      - [订单处理](best-practices/maintenance/order-processing-configuration.md)
      - [在生产站点上计划管理员更新](best-practices/maintenance/scheduling-admin-updates-in-production.md)
      - [更新服务](best-practices/maintenance/update-services.md)
      - [升级核对清单](best-practices/maintenance/upgrade-checklist.md)
      - [解决数据库性能问&#x200B;题](best-practices/maintenance/resolve-database-performance-issues.md)
      - [Adobe Commerce 2.3.5 MariaDB升级先决条件&#x200B;](best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [返回操作指南](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)
