---
title: Adobe Commerce生命周期政策
description: 了解Adobe Commerce支持期限、支持终止和云实施日期、过渡性规定以及支持版本的路径。
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 620523021580a9dba44e0e2041d8100761b8bce1
workflow-type: tm+mt
source-wordcount: '1526'
ht-degree: 0%

---


# Adobe Commerce生命周期政策

Adobe Commerce遵循定义的软件生命周期策略，以确保客户在安全、受支持的版本上运行。 如果您处于更旧的发行路线上，了解您在此生命周期中的位置并在实施截止日期之前采取行动，至关重要。 本主题涵盖支持层定义、支持终止和实施日期、临近生命周期结束的版本的过渡性规定，以及保留在受支持版本中的路径。

>[!IMPORTANT]
>
>Adobe为Adobe Commerce on Cloud (PaaS)引入了强制版本升级策略。 从&#x200B;**2027年6月1日**&#x200B;开始，Adobe将停止维护运行不支持的Commerce版本的Cloud环境，并保留停用这些版本的权利。 如果您在Cloud (PaaS)上运行，则必须在发布行的[终止扩展支持](lifecycle-policy.md#end-of-support-dates)日期之前，迁移到支持的Adobe Commerce版本或迁移到[!DNL Adobe Commerce as a Cloud Service]。 请参阅[云版本升级实施策略](version-upgrade-enforcement-policy.md)，了解实施日期、受影响的版本以及如果保留在不支持的版本上将会发生什么情况。

## 了解支持层

Adobe Commerce为版本行定义了三个支持层。 以下各节描述了每一层。

### 定期支持

从正式发布(GA)日期开始的标准三年支持期。 常规支持包括质量修复、安全补丁和全面的Adobe Commerce电话支持。

- **质量修复** — 客户可以通过联系[Adobe Commerce支持](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)或通过自助服务[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)访问质量修复。

- **安全修复** - Adobe通过累积的安全修补程序和非累积的[隔离的安全修补程序文件](versioning-policy.md#isolated-security-patch-file)提供三年支持期的安全修复。

- **修补程序** — 对于严重的安全问题，例如零日漏洞，Adobe为使用受支持版本的所有客户提供了[修补程序](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)，即使他们不在最新修补程序或安全修补程序版本上。 请注意，修补程序并不全面，也不能解决通过升级到最新版本可解决的所有安全问题。

### 扩展支持

除常规支持外，还可为特定版本系列提供一年的支持延期。 包括质量和安全性修补程序。 仅适用于Adobe Commerce客户 — 不适用于Magento Open Source。

### 仅限安全的过渡期

2025年或2026年终止延长支持的特定版本有时间限制的一次性过渡期。 仅安全过渡期仅提供有限的隔离安全修复。 不包括Adobe Commerce电话支持。 此期限不等于常规支持或延长支持，并且不会进一步延长。 将其视为迁移阶段，而不是长期支持层。 请参阅[仅安全过渡规定](#security-only-transitional-provisions)。

## 支持结束日期

下表显示了每个Adobe Commerce版本的完整生命周期，包括Adobe Commerce on Cloud (PaaS)环境的新版本升级实施日期。

| 版本 | 正式发布 | 停止定期支持 | 终止扩展支持 | 仅安全期限结束 | [版本升级实施日期（仅限云）](version-upgrade-enforcement-policy.md) |
|---------|----------------------|------------------------|-------------------------|-----------------------------|-----------------------------------------------|
| Adobe Commerce 2.4.9 | 2026年5月12日 | 2029年5月31日 | 待定 | 不适用 | 待定 |
| Adobe Commerce 2.4.8 | 2025年4月8日 | 2028年5月31日 | 待定 | 不适用 | 待定 |
| Adobe Commerce 2.4.7 | 2024年4月9日 | 2027年5月31日 | 2028年5月31日 | 不适用 | 2028年6月1日 |
| Adobe Commerce 2.4.6 | 2023年3月14日 | 2026年8月11日 | 2027年8月30日 | 2028年5月31日 | 2028年6月1日 |
| Adobe Commerce 2.4.5 | 2022年8月9日 | 2025年8月12日 | 2026年8月12日 | 2027年5月31日 | 2027年6月1日 |
| Adobe Commerce 2.4.4 | 2022年4月12日 | 2025年4月12日 | 2026年4月14日 | 2027年5月31日 | 2027年6月1日 |

{style="table-layout:auto"}

如果您的版本行接近或超过这些日期，请参阅[升级和迁移选项](#upgrade-and-migration-options)。 有关云强制详细信息，请参阅[云版本升级强制策略](version-upgrade-enforcement-policy.md)。

### 按季度支持时间表

使用此图表可以查看跨发行行的重叠支持窗口。 有关确切的结束日期，请参阅上表。 对2.4.8和2.4.9的扩展支持待定，未显示。

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
    <th colspan="4">2029</th>
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
    <td colspan="4" style="background-color:#FFBF00;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="3" style="background-color:#FFBF00;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="3" style="background-color:#FFBF00;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.8</td>
    <td colspan="13"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.9</td>
    <td colspan="17"></td>
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
   <td>定期支持</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>扩展支持</td>
  </tr>
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>仅限安全的过渡期</td>
  </tr>
 </tbody>
</table>

## 仅限安全的过渡性规定 {#security-only-transitional-provisions}

作为对2.4.4、2.4.5和2.4.6版本的一次性措施，Adobe在2025年和2026年结束时提供了扩展支持，提供了以下过渡条款，让您有更多时间规划和执行迁移或升级。 这些设置不会取代PaaS环境的[云版本升级实施](version-upgrade-enforcement-policy.md)。 您仍然必须在发布的实施日期之前升级或迁移。

| 版本 | 过渡性规定 | 期间 | 包含的内容 | 未包含的内容 |
|---------|------------------------|--------|------------------|----------------------|
| 2.4.4和2.4.5 | 仅限安全的过渡期 | 至2027年5月31日 | 逐案进行有限的隔离安全修复 | Adobe Commerce电话支持、质量修复、平台依赖关系更新 |
| 2.4.6 | 延长支持时间+仅限安全的过渡期 | 支持延长至2027年8月30日。 仅限安保至2028年5月31日。 | 延长支持期：质量和安全性修补程序。 仅限安全保护期：有限的隔离安全修复。 | 在仅限安全设置期间：Adobe Commerce电话支持、质量修复、平台依赖关系更新 |

{style="table-layout:auto"}

>[!IMPORTANT]
>
>仅限安全的过渡期是一次性例外。 它不会在发布日期之后扩展。 将仅限安全的时间段视为迁移时间，而不是长期支持层。

## 平台依赖项

停留在支持的Commerce版本上还需要受支持的平台依赖关系。 Adobe不提供对第三方服务和软件依赖项（例如PHP、MariaDB、OpenSearch、Redis、Valkey、RabbitMQ等）的安全性和质量修复，这些服务和软件依赖项可能会在您处于Adobe Commerce的三年支持期或延长支持期时终止使用。

您负责维护主动支持版本上的所有第三方依赖项和平台服务。 有关已测试和受支持的第三方技术的完整列表，请参阅[系统要求](../installation/system-requirements.md)。

Adobe不为运行不支持的依赖项版本的部署提供安全支持或帮助。 有关详细信息，请参阅[共享责任安全和操作模型](../security-and-compliance/shared-responsibility.md)。

>[!IMPORTANT]
>
>运行不支持的依赖项版本可能会导致您的Cloud实例上出现Adobe无法解决的安全漏洞。 在这种情况下，Adobe保留强制升级受影响的软件依赖项的权利，或在无法升级时停用服务的权利，而不管您的Adobe Commerce版本支持状态如何。

## PHP生命周期结束和PCI法规遵从性

您负责监视环境中使用的PHP版本的支持状态。

旧版Commerce发行版线使用的以下PHP版本已到期或即将到期，这对PCI合规性有直接影响。

| PHP版本 | 生命周期结束日期 | 受影响的Commerce版本 | PCI合规性影响 |
|-------------|------------------|----------------------------|------------------------|
| PHP 8.1 | 2025年12月31日 | 2.4.4、2.4.5和2.4.6（其中使用PHP 8.1） | PCI合规性面临风险 — 运行PHP 8.1已超过其生命周期结束日期，这意味着PHP中的安全漏洞可能无法得到修复，从而使PCI合规性面临风险。 评估合规性状态并排定升级优先级。 |
| PHP 8.2 | 2026年12月31日 | 2.4.6（其中使用PHP 8.2） | 从2026年底开始，PCI合规性面临风险 — 在2026年底之前规划升级或迁移，以保持PCI合规性。 |

{style="table-layout:auto"}

### PCI合规性声明

PCI合规性是商家进行评估的责任。 Adobe强烈建议受影响版本的商家咨询其符合条件的安全评估员，并优先尽快迁移到支持的Commerce版本和受支持的PHP版本。 有关PHP支持时间表，请参阅[PHP支持的版本](https://www.php.net/supported-versions.php)和[PHP生命周期结束](https://www.php.net/eol.php)。

## 升级和迁移选项

如果您使用的版本接近或超过其支持结束日期，请立即采取行动。 如果保留在不支持的版本，则您的存储将面临安全漏洞、合规问题和失去支持的风险。 Adobe提供了以下路径来迁移至支持的版本。

### 推荐路径：迁移到Adobe Commerce as a Cloud Service (ACCS)

[!DNL Adobe Commerce as a Cloud Service]是Adobe的新一代托管商务平台，也是Adobe推荐的适用于Adobe Commerce上所有Cloud客户的长期目标。

- Adobe会自动管理所有基础架构、修补和升级。
- 您始终处于受支持、合规的基础架构上 — 不会再次出现生命周期结束的情况。
- 您可以访问Adobe的最新功能：AI支持的促销、可组合的店面架构和本机Adobe Experience Cloud集成。
- 您可以消除循环升级周期。

请联系您的Adobe客户团队以开始迁移评估。 有关产品概述，请参阅[Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview)。

### 替代路径：升级到支持的Adobe Commerce云版或内部部署版

如果您无法立即迁移到[!DNL Adobe Commerce as a Cloud Service]，则可以升级到当前支持的最新本地Adobe Commerce或云版本。 这会将您移至完全支持的现代化基础架构栈栈，同时保留您现有的PaaS部署模型。

请注意，此路径不会消除未来的升级义务。 随着版本行达到其版本升级实施日期，PaaS上的客户必须继续升级。
