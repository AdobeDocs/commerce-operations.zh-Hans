---
title: Adobe Commerce微服务
description: 能够区分Headless和Adobe Commerce相关的微服务。
exl-id: 078e0e8e-7acc-4913-8b78-585a950f3f5e
feature: Integration, Services
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Headless和微服务

不要将headless与微服务混淆，这一点很重要。 很多时候，我们听到的关于微服务的对话都和Headless一样。 它们是完全不同的事物。 它们可以一起使用，但它们是完全不同的概念。

微服务架构是一个术语，用于描述将应用程序拆分为一系列较小的、松散耦合的服务。 微服务使单个后端服务能够：

- **相互隔离** — 例如，定价服务不依赖于目录服务。

- **部署了单点** — 客户只部署他们需要的应用程序部分。

- **独立缩放** — 可以将资源分配给高需求服务，如库存查询。

- **自主开发** — 可以相互独立地开发和部署。

微服务与斩断商业栈栈或API的头无关。 当我们想到那些商业服务时那些核心代码位于Adobe Commerce的后台，就是将这些服务相互隔离。 因此，微服务架构正在松散地分解所有这些服务，如定价服务、目录服务和库存服务，并使每一项服务彼此隔离。

微服务可以独立扩展和自主开发。 微服务类似于多租户SaaS开发过程。 许多现代多租户SaaS产品都是采用多服务方法开发的。 甚至Adobe自己的SaaS产品(如Order Management、AI驱动的新产品Recommendations工具)以及Adobe Commerce的其他SaaS组件也在使用微服务方法进行开发。 需要明确的是，Adobe Commerce 2.4.x不是微服务架构，而是Headless架构。
