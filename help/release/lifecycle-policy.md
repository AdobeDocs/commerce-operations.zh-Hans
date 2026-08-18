---
title: 软件生命周期政策
description: 了解 Adobe Commerce 版本的软件支持终止关键日期。
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
nudge: true
last-update: 2026-08-17T00:00:00Z
source-git-commit: 7ba189685721799de047bc8d0e7108fa512f7120
workflow-type: tm+mt
source-wordcount: '1350'
ht-degree: 1%

---


# Adobe Commerce生命周期政策

为了简化Adobe Commerce生命周期政策并支持客户的关键需求，Adobe从正式发布(GA)之日起为每个版本提供三年标准支持期，并在此期间发布质量修复。 有关每个版本的软件支持终止的日期和详细信息，请参阅[支持终止日期](#end-of-support-dates)表。

Adobe不提供对第三方服务和软件依赖项（例如PHP和MySQL）的安全性和质量修复，这些服务和软件依赖项可能会在客户处于Adobe Commerce的三年支持期或延长支持期时终止。 有关经过测试和受支持的第三方技术的完整列表，请参阅[系统要求](../installation/system-requirements.md)。

## 标准支持

从正式发布(GA)日期开始的标准三年支持期。 标准支持包括质量修复、安全补丁和完整的Adobe Commerce电话支持。

- **质量修复** — 客户可以通过联系[Adobe Commerce支持](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)或通过自助服务[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)访问质量修复。

- **安全修复** - Adobe通过累积的安全修补程序和非累积的[隔离的安全修补程序文件](versioning-policy.md#isolated-security-patch-file)提供三年支持期的安全修复。

- **修补程序** — 对于严重的安全问题，例如零日漏洞，Adobe为使用受支持版本的所有客户提供了[修补程序](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)，即使他们不在最新修补程序或安全修补程序版本上。 请注意，修补程序并不全面，也不能解决通过升级到最新版本可解决的所有安全问题。

## 扩展支持

Adobe鼓励客户尽快升级。 但是，为了提供更大的灵活性以符合升级计划和业务需求，Adobe在版本2.4.6和2.4.7上为Adobe Commerce客户提供一年的额外支持，而不产生额外费用。 支持扩展包括核心应用程序的质量和安全修补程序。 对Adobe Commerce 2.4.4和2.4.5版本的扩展支持按计划于2026年4月和8月结束。

>[!NOTE]
>
>Adobe为Adobe Commerce on Cloud引入强制版本升级策略，以帮助每位客户停留在一个安全、受支持的平台上。 自2027年6月1日&#x200B;**起**，Adobe将不再维护运行不支持的Commerce版本的Cloud环境，并将被迫采取适当措施保障Adobe Commerce平台及其客户的安全。 这包括暂停到受影响的基础架构的流量。 因此，您的电子商务店面将脱机。 如果您在Cloud上运行，则必须移至支持的Adobe Commerce版本，或在发布行的[终止扩展支持](lifecycle-policy.md#end-of-support-dates)日期之前迁移到[!DNL Adobe Commerce as a Cloud Service]。 如果您使用的是版本2.4.4到2.4.9，请参阅[安全和合规性声明](security-enforcement-policy.md)，以了解适用于您的环境的特定操作和截止日期。

## 仅限安全的过渡期

一次性有限过渡期仅适用于2.4.4、2.4.5和2.4.6版，其长期支持于2025年或2026年结束。 仅安全过渡期仅提供有限的隔离安全修复（无质量修复）。

>[!IMPORTANT]
>
>仅限安全的过渡期是一次性例外。 它不会在发布日期之后扩展。 将仅限安全的时间段视为迁移时间，而不是长期支持层。 如果您希望帮助制定迁移计划，请与您的客户团队联系。

## 支持结束日期

下表显示了每个Adobe Commerce版本的完整生命周期，包括Adobe Commerce on Cloud环境的新版本升级实施日期。

{{$include /help/_includes/templated/release/end-of-support-dates.md}}

## 支持时间表

支持时间表按季度映射每个Adobe Commerce版本行的支持时段。 使用本主题前面提供的表获取确切的结束日期。

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="1"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
    <th colspan="4">2028</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Commerce</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="5" style="background-color:#FFBF00"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="4" style="background-color:#FFBF00"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="2"></td>
  </tr>
  <tr>
    <td>2.4.8</td>
    <td colspan="13"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**键**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;"></td>
   <td>标准支持</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>扩展支持</td>
  </tr>
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>扩展的安全修复</td>
  </tr>
 </tbody>
</table>

## 平台依赖项

停留在支持的Commerce版本上还需要受支持的平台依赖关系。 Adobe不提供对第三方服务和软件依赖项（例如MariaDB、OpenSearch、Redis、Valkey、RabbitMQ等）的安全性和质量修复，这些服务和软件依赖项可能会在您处于Adobe Commerce的三年支持期或延长支持期时终止生命周期。 有关详细信息，请参阅[共享责任安全和操作模型](../security-and-compliance/shared-responsibility.md)。

您负责维护主动支持版本上的所有第三方依赖项和平台服务。 有关已测试和受支持的第三方技术的完整列表，请参阅[系统要求](../installation/system-requirements.md)。

>[!IMPORTANT]
>
>运行不支持的依赖项版本可能会导致您的Cloud实例上出现Adobe无法解决的安全漏洞。 在这种情况下，Adobe将被迫采取适当行动维护Adobe Commerce平台及其客户的安全。 这包括暂停到受影响的基础架构的流量。 因此，您的电子商务店面将脱机。
>
>如果环境在流量暂停后继续保持不合规状态，Adobe可以终止云服务，启动停用过程。 由于停用，托管电子商务环境中的所有数据和资产（包括所有实例、环境和分支）将被永久删除且无法恢复。 请参阅[保护Commerce环境所需的操作和截止日期](security-enforcement-policy.md)，了解这些升级的计划方式以及在整个过程中可供您使用的支持。

## PHP生命周期结束和PCI法规遵从性

您负责监视环境中使用的PHP版本的支持状态。

旧版Commerce发行版线使用的以下PHP版本已到期或即将到期，这对PCI合规性有直接影响。

| PHP版本 | 生命周期结束日期 | 受影响的Commerce版本 | PCI合规性影响 |
| ------------- | ------------------ | ---------------------------- | ------------------------ |
| PHP 8.1 | 2025年12月31日 | 2.4.4、2.4.5和2.4.6（其中使用PHP 8.1） | PCI合规性面临风险 — 运行PHP 8.1已超过其生命周期结束日期，这意味着PHP中的安全漏洞可能无法得到修复，从而使PCI合规性面临风险。 评估合规性状态并排定升级优先级。 |
| PHP 8.2 | 2026年12月31日 | 2.4.6（其中使用PHP 8.2） | 从2026年底开始，PCI合规性面临风险 — 在2026年底之前规划升级或迁移，以保持PCI合规性。 |

{style="table-layout:auto"}

>[!IMPORTANT]
>
>**PCI合规性通知：** PCI合规性是商家进行评估的责任。 Adobe强烈建议受影响版本的商家咨询其符合条件的安全评估员，并优先尽快迁移到支持的Commerce版本和受支持的PHP版本。 有关PHP支持时间表，请参阅[PHP支持的版本](https://www.php.net/supported-versions.php)和[PHP生命周期结束](https://www.php.net/eol.php)。

## 升级和迁移选项

如果您使用的版本接近或超过其支持结束日期，请立即采取行动。 如果保留在不支持的版本，则您的存储将面临安全漏洞、合规问题和失去支持的风险。 Adobe提供了以下路径来迁移至支持的版本。

### 推荐路径：迁移到Adobe Commerce as a Cloud Service

[!DNL Adobe Commerce as a Cloud Service]是Adobe的新一代托管商务平台，也是Adobe推荐的适用于Adobe Commerce上所有Cloud客户的长期目标。

- Adobe会自动管理所有基础架构、修补和升级。
- 您始终处于受支持、合规的基础架构上 — 不会再次出现生命周期结束的情况。
- 您可以访问Adobe的最新功能：AI支持的促销、可组合的店面架构和本机Adobe Experience Cloud集成。
- 您可以消除循环升级周期。

请联系您的Adobe客户团队以开始迁移评估。 有关产品概述，请参阅[Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/zh-hans/docs/commerce/cloud-service/overview)。

### 替代路径：升级到支持的Adobe Commerce云版或内部部署版

如果您无法立即迁移到[!DNL Adobe Commerce as a Cloud Service]，则可以升级到当前支持的Adobe Commerce云版本的最新版本。 这会将您转移到完全支持的现代化基础架构栈栈，同时保留云上现有的Commerce部署模型。

请注意，此路径不会消除未来的升级义务。 在版本行到达版本升级实施日期时，具有Adobe Commerce on Cloud部署的客户必须继续升级。
