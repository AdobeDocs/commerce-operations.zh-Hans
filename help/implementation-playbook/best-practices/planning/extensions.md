---
title: 扩展最佳实践
description: 了解如何避免由第三方Adobe Commerce扩展导致的性能问题。
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# 扩展最佳实践

Adobe Commerce第三方扩展（模块）可能会导致各种可能会对店面性能造成负面影响的问题。 您可以按照以下最佳实践来避免这些问题：

- 从可信来源(如 [Commerce Marketplace](https://marketplace.magento.com/extensions.html).
- 将所有第三方扩展更新到最新版本。
- 如果无法保持第三方扩展的更新，请考虑使用不同的扩展。
- 计划升级到新版Adobe Commerce时，请验证已安装的第三方扩展是否与新版本兼容，并根据需要升级扩展。

>[!NOTE]
>
> 要保持与新的Commerce版本的兼容性，需要Adobe Commerce Marketplace中提供的所有扩展。 请参阅 [版本兼容性](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases/).

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## 其他信息

- [规划升级的最佳实践](../../../upgrade/prepare/best-practices.md)
- 在云基础架构上将第三方扩展与Adobe Commerce结合使用
   - [技术和要求 — 开发和测试](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-devtest)
   - [为何要在集成和暂存环境中进行全面测试？](https://devdocs.magento.com/cloud/live/live.html#whytest)
