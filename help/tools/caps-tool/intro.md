---
title: '[!DNL Adobe Commerce Patching Automation]'
description: 了解 [!DNL Adobe Commerce Patching Automation]、其用途、如何访问它以及自动修补的最佳实践
hide: true
source-git-commit: f70924d6f0d1777104c59f3f9e776360308abceb
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# [!DNL Adobe Commerce Patching Automation]

[!DNL Adobe Commerce Patching Automation]是一个工具，可自动在Cloud环境中应用和还原Adobe Commerce的修补程序。 它为Commerce项目管理员提供了一个简化的工作流程，以便应用和还原修补程序。 内置的验证和运行状况检查有助于确保云环境保持稳定和安全。

本指南面向希望简化修补流程、降低修补程序相关问题风险、提高环境的安全性和稳定性并自动化例行修补程序操作的Adobe Commerce Cloud商家和合作伙伴。

## [!DNL Patching Automation]主题

* **[如何访问](access.md)**
* **[工作流概述](workflow.md)**
* **[GitHub集成](github-integration.md)**
* **[最佳实践](best-practices.md)**
* **[疑难解答](troubleshooting.md)**

## 工具概述

* **UI界面**
  * 实时显示特定项目和环境组合的修补程序可用性和状态
  * 显示进度、错误和任何其他相关消息的综合修补程序状态信息
  * [!UICONTROL Patch Management Dashboard]用于：
    * 查看可用的修补程序
    * 通过一键操作应用修补程序
    * 还原以前应用的修补程序
    * 监视修补程序操作状态和结果

* **使用结构化工作流自动修补服务**
  * **初步检查** — 验证修补程序兼容性和环境就绪性
  * **修补** — 在集成环境中自动应用或还原修补程序
  * **验证** — 执行运行状况检查，以确认应用程序已启动并且其数据库和缓存连接可访问

* **安全功能**
  * 在应用程序之前验证修补程序兼容性
  * 在合并到目标环境之前，先在临时集成环境中应用修补程序（确认它成功部署并通过运行状况检查），然后在部署后立即执行最终的运行状况检查
  * 将修补程序应用到`m2-hotfixes`文件夹，并在还原期间自动删除

## 与Adobe Commerce Cloud集成

[!DNL Patching Automation]与Adobe Commerce Cloud基础架构完全集成，可与您现有的云环境无缝配合工作。 它利用云原生功能以获得最佳性能，提供详细的日志记录和监控，并与Adobe Commerce云支持工具集成。

## 视频教程

了解[!DNL Adobe Commerce Patching Automation]以及此工具如何帮助用户快速查找和应用安全修补程序。 以下视频介绍如何通过站点范围分析工具(SWAT)仪表板访问它，选择您的项目和环境，以及单击一下即可应用修补程序。

>[!VIDEO](https://video.tv.adobe.com/v/3476247/?learn=on&enablevpops)

## 常见用例

* **安全修补程序** — 快速应用关键安全更新
* **修补程序回滚** — 安全还原通过服务应用的问题修补程序
* **安全合规性** — 通过自动修补维护安全标准
* **操作稳定性** — 确认应用程序在每次修补程序操作后启动并通过运行状况检查
