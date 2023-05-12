---
title: 性能基准
description: 查看在Adobe云基础架构上托管的Adobe Commerce实施的性能基准结果。
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
source-git-commit: 09a42dc68836b34eab2c9d90879b897729cd1b09
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# 基准摘要

Adobe Commerce 2.4.5性能基准结果反映了在使用以下基础架构和其他组件部署的Adobe Commerce实例上所衡量的性能。
- [Pro云环境](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) with [扩展架构](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- [B2B for Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe CommerceInventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

没有其他自定义设置。

以下信息汇总了基准结果，并提供了有关测试期间使用的环境和数据的信息。

## 关键性能量度

下图显示了性能基准的商务商店配置以及测试结果中的关键性能量度。

![性能基准JMeter和生产基础架构](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

根据模拟企业B2C组织的测试标准，系统可以在标准负载流量处于高峰时间处理请求的流量和订单编号。

### 性能亮点

- **订单数** — 每分钟处理3,481个订单，同时在第99个百分位数的响应时间保持在2秒以下（99%的请求在响应时间少于2秒的情况下得到服务）。
- **页面查看次数** — 每小时处理超过200万次页面查看，同时在第99个百分位数的响应时间保持在2秒以下。
- **有效SKU** — 客户资料包括2.42亿种不同的价格变动(<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKU</a>)，用于250,000个产品。
- **GraphQL请求** — 系统缩放到每分钟10,500个GraphQL未缓存请求，同时在第99个百分位数的响应时间保持在2秒以下。
- **并发管理员用户** — 系统可缩放为支持500个并行管理员用户，同时在第99个百分位数内保持响应时间不到2秒。

## 测试环境

针对在具有缩放架构的Pro云环境中部署的Adobe Commerce 2.4.5实例进行测试，以获得性能基准结果。 实例还安装、配置和启用了Adobe Commerce B2B、Inventory management和Adobe Stock集成模块。

测试用户档案的性能测试数据是使用 <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">Performance Toolkit</a>.

性能衡量基于针对客户和企业用户的模拟日常商店活动。 这些值反映的是每个案例接近最大的吞吐量，但并不反映独特的业务模型，如私人销售或闪电销售。

- **LUMA Storefront**
   - 店面上3000个并发用户
   - 设置为30%的CDN缓存点击率

      缓存层的有效使用会增加每小时的页面查看次数。

- **GraphQL API**
   - 250个并发线程
   - 设置为0%的CDN缓存点击率

      在GraphQL前面设置缓存层，响应时间显着缩短。

- **管理Web**
   - 500个并发用户
   - 设置为0%的CDN缓存点击率

## 测试环境规范

已使用针对Adobe Commerce实例运行的JMeter加载配置文件完成负载测试。 在测试过程中使用了3个Web节点和3个服务节点。 下图详细介绍了JMeter和生产基础架构的入口点。

![性能基准JMeter和生产基础架构](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### 应用程序

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a> 部署在具有Pro架构的云基础架构上。

### 基础架构

对于性能基准，在 [可扩展基础架构](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) 具有以下容量。

- **Web节点规范**
   - vCPU 216（72 x 3节点）
   - 内存432 GiB（144 x 3节点）
   - 网络带宽768 Gbps（256 x 3节点）
   - 已配置的存储100 GB

- **服务节点规范**
   - vCPU 192（64 x 3节点）
   - 内存768 GiB（256 x 3节点）
   - 网络带宽60 Gbps（20 x 3节点）
   - EBS带宽40800 Mbps(13600 x 3节点)
   - 已配置的存储1100 GB
