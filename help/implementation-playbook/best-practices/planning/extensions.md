---
title: 扩展最佳实践
description: 了解如何避免由第三方Adobe Commerce扩展引起的性能问题。
role: Admin
feature: Best Practices, Extensions
exl-id: 95d2c7bf-fd2f-4c98-8293-96d69b86341f
source-git-commit: 1fdbded7738365593ef7da64f4dbe6713984bff3
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---

# 扩展最佳实践

Adobe Commerce第三方扩展（模块）可能会导致各种问题，这些问题可能会对店面性能产生负面影响。 您可以按照以下最佳实践来避免这些问题：

- 尽可能使用[进程外可扩展性](https://developer.adobe.com/commerce/extensibility/)来开发Commerce集成和自定义项，以便轻松进行维护和升级。
- 从受信任的来源(如[Commerce Marketplace](https://marketplace.magento.com/extensions.html))下载并购买第三方扩展。
- 将所有第三方扩展更新到最新版本。
- 如果无法保持更新第三方扩展，请考虑使用不同的扩展。
- 在计划升级到新版Adobe Commerce时，请验证安装的第三方扩展是否与新版本兼容，并根据需要升级扩展。

>[!NOTE]
>
> 要保持与新Commerce版本的兼容性，需要使用Adobe Commerce Marketplace中提供的所有扩展。 请参阅[版本兼容性](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases/)。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md)，共：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 其他信息

- [规划升级的最佳实践](../../../upgrade/prepare/best-practices.md)
- 在云基础架构上将第三方扩展与Adobe Commerce结合使用
   - [技术和要求 — 开发和测试](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-devtest)
   - [为何要在集成和暂存环境中完全测试？](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/overview#why-test-fully-in-integration-staging-and-production)
