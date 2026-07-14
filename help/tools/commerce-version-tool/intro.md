---
title: '[!DNL Commerce Version Tool]'
description: 了解Adobe Commerce的 [!DNL Commerce Version Tool] 并使用供应商/bin/patch-status检查每月的安全修补程序状态。
TQID: 'https://experienceleague.adobe.com/9lDQtCrcCSIFjt3jUJkqCo-rMlIhhy3tPTtPyT4wt1Q'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: f42e0a1a-0d79-488d-a83f-f2c30672b137
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 586
ht-degree: 0%

---

# [!DNL Commerce Version Tool]

Adobe Commerce的每月安全修补程序是非累积性的，必须按顺序应用。 [!DNL Commerce Version Tool] ([!DNL CVT])通过报告每月安装了哪些安全修补程序、缺少哪些修补程序以及安装受到哪些CVE保护来帮助商家验证修补程序覆盖范围。

>[!IMPORTANT]
>
>[!DNL CVT]工具仅供参考。 它不会应用修补程序、还原修补程序或修改Adobe Commerce源文件。 它可以写入缓存文件、临时试运行文件和审核日志条目，以支持修补程序状态报告。

## 工具概述

[!DNL CVT]工具是一个独立的可执行文件，包含在每个每月的Adobe Commerce安全修补程序中。 将修补程序应用于Adobe Commerce安装后，该工具将安装在`vendor/bin/patch-status`。 它需要PHP 8.1或更高版本以及系统`patch`二进制文件。 它不需要编辑器包、非标准PHP扩展、Adobe Commerce引导或单独的安装步骤。

[!DNL CVT]工具可以帮助您：

- 为支持的Adobe Commerce安装检测已应用的安全修补程序。
- 识别每月隔离的安全修补程序序列中缺少的修补程序。
- 报告与修补程序相关的常见漏洞和暴露(CVE)记录的受保护、易受攻击或未知的安全状态。
- 生成机器可读的输出，如JSON或CSV，以用于扫描仪、功能板和合规性报告。
- 检测支持的平台和组件的修补程序状态。

## 可用性

当Adobe在修补程序注册表文件中为安装的版本提供修补程序元数据时，[!DNL CVT]工具支持以下平台和组件的修补程序状态报告。

| 平台或组件 | 可用性 |
| --- | --- |
| Adobe Commerce内部部署 | 支持 |
| [!DNL Magento Open Source] | 支持 |
| Adobe Commerce企业对企业(B2B) | 安装时支持 |
| Adobe Commerce Page Builder | 安装时支持 |
| Adobe Commerce清单 | 安装时支持 |
| 从`composer.lock`检测到其他组件 | 在修补程序注册表文件中表示时支持 |

{style="table-layout:auto"}

## 常见用例

当您需要以下任务时，请使用[!DNL CVT]工具：

- 检查Adobe Commerce安装是否包含所需的隔离安全修补程序。
- 确认跳过或不完整的修补程序集是否导致CVE覆盖不完整。
- 生成JSON或CSV输出以用于内部报告或自动扫描。
- 在打开支持请求或计划修正之前，提供修补程序状态信息。

## 使用结果的准则

将[!DNL CVT]工具输出视为支持修补程序规划和安全审查的检测数据。

请遵循以下准则：

- 针对稳定且受支持的Adobe Commerce安装运行[!DNL CVT]工具。
- 在发出安全状态声明之前，请查看丢失的修补程序和未知的修补程序。
- 保留JSON或CSV输出以提高可审核性和自动化程度。
- 将扫描输出视为与安全相关的操作数据。
- 仅共享支持或修正所需的详细信息。

## 补丁检测

[!DNL CVT]工具在两个固定步骤中运行检测。 在生成修补程序状态报告时，这两个步骤始终运行。

- **编辑器检测：**&#x200B;该工具读取`composer.lock`文件以确定[!DNL Adobe Commerce]基本版本和已安装的组件区域。 如果该工具无法检测到基本版本，则将退出并返回代码`1`。

- **模拟运行检测：**&#x200B;对于每个适用的修补程序，该工具将对修补程序更改进行模拟运行检查，以确定该修补程序是否已应用、未应用或修补程序状态是否未知。 该工具在此检查期间处理修补程序依赖关系，以便结果反映安装的组件版本。

该报告仅包含适用于检测到的安装和已安装的组件的修补程序。 如果该工具无法确认是否存在适用的修补程序，则会将该修补程序归类为未知修补程序。

## 开始使用[!DNL CVT]

使用下列主题可以生成、排除故障和跟踪修补程序状态报告：

- [生成修补程序状态报告](generate-report.md)以运行[!DNL CVT]工具、查看命令选项并解释报告结果。
- [[!DNL Commerce Version Tool] 疑难解答](troubleshooting.md)以解决意外结果或命令错误。
- [[!DNL Commerce Version Tool] 发行说明](release-notes.md)以查看发行更新。
