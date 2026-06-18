---
title: 云版本升级实施策略
description: 了解Adobe Commerce在云中的版本升级实施 — Adobe为何实施升级、实施日期、停用和所需操作。 请参阅生命周期政策，以了解过渡性规定和迁移路径。
nudge: true
source-git-commit: eacee993ec38cce7763d4c99b1bbb67a319d8c1a
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# 适用于Adobe Commerce on Cloud的版本升级实施策略

当对Adobe Commerce版本的常规支持和扩展支持终止时，Adobe保留在仍运行该不受支持版本的云环境中停用Adobe Commerce的权利。 版本升级强制实施仅适用于云环境上的Adobe Commerce ；本地客户管理自己的基础架构。

您必须移至支持的Adobe Commerce版本，或在发布行的[扩展支持结束](lifecycle-policy.md#end-of-support-dates)日期之前迁移到[!DNL Adobe Commerce as a Cloud Service]。

以下部分将说明Adobe为何强制执行升级、如何计算强制执行日期以及在强制执行日期将发生什么情况。 有关特定于版本的实施日期，请参阅生命周期策略中的[支持结束日期](lifecycle-policy.md#end-of-support-dates)表。

>[!NOTE]
>
>本主题仅介绍云升级实施。 有关支持层定义、[支持结束日期](lifecycle-policy.md#end-of-support-dates)表、[仅安全过渡条款](lifecycle-policy.md#security-only-transitional-period)、[第三方软件依赖项](lifecycle-policy.md#platform-dependencies)、[PHP生命周期结束和PCI合规性](lifecycle-policy.md#php-end-of-life-and-pci-compliance)以及[升级和迁移选项](lifecycle-policy.md#upgrade-and-migration-options)，请参阅[生命周期策略](lifecycle-policy.md)。 除了升级到支持的Adobe Commerce版本之外，Adobe还要求您在主动支持的版本上保留第三方软件依赖项。

## Adobe为何要推出这项政策

Adobe负责托管平台基础设施的安全性和合规性，Adobe Commerce on Cloud客户可以在该基础设施上运行。 这包括使所有基础软件依赖项保持最新，应用安全补丁程序，以及满足客户所依赖的合规性标准（如PCI）。

当供应商正式终止对基础软件依赖项的安全支持时，Adobe将无法再提供所需级别的安全保护范围和平台支持。 如果继续在不支持的基础设施上运营商店，客户、购物者和Adobe将面临不可接受的风险。 因此，Adobe将引入正式的版本升级实施策略，该策略定义何时将停用运行不支持的Adobe Commerce版本的云环境上的Commerce。

## 如何计算升级实施日期

对于每个Adobe Commerce版本行，升级实施日期的计算如下：

**升级实施日期** =正式发布日期+ 3年定期支持+最多1年延长支持

宣布对每个发行版行的定期支持即将结束，将提供扩展支持。

## 在版本升级实施日期将发生什么情况

在发布的升级实施日期，Adobe将停止对仍在运行受影响版本云环境上的所有Adobe Commerce的维护，并保留停用这些版本的权利。 您将在版本升级实施日期之前的关键里程碑收到高级通知。 Adobe将在环境停用之前提供一个数据导出窗口，以便您检索数据。

此策略下的第一个实施日期为&#x200B;**2027年6月1日**，对于在该日期之前达到扩展支持结束时间的发行行。 有关特定于版本的实施日期，请参阅[支持结束日期](lifecycle-policy.md#end-of-support-dates)表。
