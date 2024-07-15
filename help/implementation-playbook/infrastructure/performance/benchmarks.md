---
title: 性能指标评测
description: 查看在Adobe云基础架构上托管的Adobe Commerce实施的性能基准结果。
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# 准则摘要

Adobe Commerce 2.4.5性能基准结果反映了在Adobe Commerce实例上衡量的性能，该实例部署了以下基础架构和其他组件。
- 具有[缩放体系结构](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)的[专业云环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html)
- Adobe Commerce的[B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe Commerce Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

没有其他自定义项。

以下信息总结了基准测试结果，并提供了有关测试期间使用的环境和数据的信息。

## 关键绩效指标

下图显示了性能基准的Commerce存储配置以及测试结果中的关键性能指标。

![性能基准JMeter和生产基础架构](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

基于模拟企业B2C组织的测试标准，该系统可以在高峰期以标准负载流处理请求的流量和订单数。

### 性能亮点

- **订单数** — 每分钟处理3,481个订单，同时在第99个百分位数中保持不到2秒的响应时间（99%的请求均以不到2秒的响应时间提供服务）。
- **页面查看次数** — 每小时处理的页面查看次数超过200万次，而第99个百分位数的响应时间保持在2秒以内。
- **有效SKU** — 客户配置文件包含250,000种产品的2.42亿种不同的价格变化(<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKU</a>)。
- **GraphQL请求** — 系统可扩展到每分钟10,500个GraphQL未缓存请求，同时将第99百分位数的响应时间保持在2秒以内。
- **并发管理员用户** — 系统扩展为支持500个并发管理员用户，同时在第99个百分位数的响应时间保持在2秒以内。

## 测试环境

通过在具有缩放架构的Pro云环境中部署的Adobe Commerce 2.4.5实例进行测试，获得了性能基准结果。 该实例还安装、配置和启用了Adobe Commerce B2B、Inventory management和Adobe Stock集成模块。

测试配置文件的性能测试数据是使用<a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">性能工具包</a>生成的。

绩效衡量基于针对客户和商业用户的模拟日常店铺活动。 这些值反映每个案例的接近最大吞吐量，但并不反映独特的业务模式，如私有销售或闪电销售。

- **LUMA店面**
   - 店面有3000个并发用户
   - 设置为30% CDN缓存命中率

     缓存层的有效使用增加了每小时的页面查看次数。

- **GraphQL API**
   - 250个并发线程
   - 设置为0% CDN缓存命中率

     通过在GraphQL前面放置缓存层，可显着缩短响应时间。

- **管理Web**
   - 500个并发用户
   - 设置为0% CDN缓存命中率

## 测试环境规范

加载测试已使用针对Adobe Commerce实例运行的JMeter加载配置文件完成。 测试过程中使用了3个Web节点和3个服务节点。 下图详细说明了JMeter和生产基础架构的入口点。

![性能基准JMeter和生产基础架构](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### 应用程序

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a>部署在具有Pro架构的云基础架构上。

### 基础架构

对于性能基准，Adobe Commerce 2.4.5部署在[可扩展的基础架构](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)上，具有以下容量。

- **Web节点规范**
   - vCPU 216（72 x 3节点）
   - 内存432 GiB（144 x 3节点）
   - 网络带宽768 Gbps （256 x 3节点）
   - EBS带宽57000 Mbps (19000 x 3个节点)
   - 已调配存储100 GB

- **服务节点规范**
   - vCPU 192（64 x 3节点）
   - 内存768 GiB（256 x 3节点）
   - 网络带宽60 Gbps （20 x 3节点）
   - EBS带宽40800 Mbps (13600 x 3个节点)
   - 已调配存储1100 GB
