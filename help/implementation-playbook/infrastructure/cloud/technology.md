---
title: 云基础架构技术
description: 更详细地了解Adobe在云基础架构上用于Adobe Commerce的技术集合。
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
feature: Cloud
source-git-commit: c737a8e902c960c933e54e2521107475bb1e5a22
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# 技术

云基础架构上的Adobe Commerce使用多种软件解决方案来支持该平台。 有关更多详细信息，请参阅&#x200B;_云指南_&#x200B;中的以下主题：

- [专业环境体系结构](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#production-technology-stack)
- [入门环境体系结构](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-architecture.html#production-and-staging-technology-stack)

## 功能和优点

- 虚拟专用云(VPC)中的三个专用实例，具有跨三个独立可用区或数据中心的弹性负载平衡器。
- 针对可能导致单个实例失败的事件的更高恢复能力。 例如，整个AWS可用区或数据中心的中断。
- 零停机时间跨整个栈栈（包括Web 、缓存、搜索和数据库）扩展。
