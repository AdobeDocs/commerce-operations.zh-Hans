---
title: 报表配置最佳实践
description: 如果不使用报表模块，请通过删除报表模块来优化网站性能。
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 1%
---
# 报告配置最佳实践

如果您的企业不需要报告或动态客户区段功能，请禁用[报告功能](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/config/general/reports)以提高存储性能。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md)，共：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 禁用报告

如果不使用报表或动态客户区段，请禁用报表功能。

1. 从管理员中，导航到&#x200B;**商店** > **设置** > **配置** > **常规** > **报告**。
1. 在&#x200B;**常规选项**&#x200B;下，将&#x200B;**启用报表**&#x200B;设置为&#x200B;*否*。
1. 通过运行`php bin/magento cache:flush`或在&#x200B;**系统** > **工具** > **缓存管理**&#x200B;下的管理员中刷新缓存。

## 其他信息

- [在Adobe Commerce中生成报表](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/start/reporting/reports-menu)
- [客户动态区段](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/customers/segments/customer-segments)
