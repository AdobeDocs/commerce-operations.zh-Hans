---
title: 软件生命周期政策
description: 了解 Adobe Commerce 版本的软件支持终止关键日期。
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 3e7cef954a2be506c6f72e704710d16ed1d9b7a3
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 2%

---


# Adobe Commerce生命周期政策

为了简化Adobe Commerce生命周期政策并支持客户的任务关键型需求，Adobe从正式发布之日起，为每一个版本提供为期三年的支持期，并在此期间发布质量修复。 有关每个版本的软件支持终止的日期和详细信息，请参阅[软件支持终止](#end-of-software-support)表。

在三年的支持期内，客户可以访问：

- **质量修复** — 客户可以通过联系[Adobe Commerce支持](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)或通过自助服务[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)访问质量修复。 下表介绍了Adobe Commerce发行行的软件支持终止日期。

- **安全修复**-Adobe通过累积的安全修补程序和非累积的[隔离的安全修补程序文件](versioning-policy.md#isolated-security-fixes)提供三年支持期的安全修复。

- **修补程序** — 对于严重的安全问题，例如零日漏洞，Adobe为使用受支持版本的所有客户提供了[修补程序](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)，即使他们不在最新修补程序或安全修补程序版本中。 请注意，修补程序并不全面，也不能解决通过升级到最新版本可解决的所有安全问题。

Adobe不提供对第三方服务和软件依赖项（例如PHP和MySQL）的安全性和质量修复，这些服务和软件依赖项可能会在客户处于Adobe Commerce的三年支持期或延长支持期时终止。 有关经过测试和受支持的第三方技术的完整列表，请参阅[系统要求](../installation/system-requirements.md)。

## 扩展支持

Adobe鼓励客户尽快升级。 但是，为了提供更大的灵活性以符合升级计划和业务需求，Adobe为Adobe Commerce客户2.4.6版提供一年支持扩展，而无额外费用。支持扩展包括核心应用程序的质量和安全修补程序，有效期最长为一年。 对Adobe Commerce 2.4.4和2.4.5版本的扩展支持按计划于2026年4月和8月结束。

>[!NOTE]
>
>扩展支持仅向Adobe Commerce客户提供。 它不适用于Magento Open Source代码库。

## 软件支持终止

| 版本 | 正式发布 | 结束常规支持<sup>1</sup> | 终止扩展支持 |
|----------------------|----------------------|------------------------------------|-------------------------|
| Adobe Commerce 2.4.8 | 2025年4月8日 | 2028年5月31日 | 待定 |
| Adobe Commerce 2.4.7 | 2024年4月9日 | 2027年5月31日 | 待定 |
| Adobe Commerce 2.4.6 | 2023年3月14日 | 2026年8月11日 | 2027年8月30日 |
| Adobe Commerce 2.4.5 | 2022年8月9日 | 2025年8月12日 | 2026年8月11日 |
| Adobe Commerce 2.4.4 | 2022年4月12日 | 2025年4月12日 | 2026年4月14日 |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup>如果您是Adobe Commerce客户，则可以在延长的支持期内继续接收额外一年的安全和质量修复。
>- 请参阅[软件生命周期策略](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)。

## Adobe Commerce 2.4.4和2.4.5的其他安全修复程序配置

作为一次性例外，Adobe为Adobe Commerce版本2.4.4和2.4.5提供了更长的安全修复配置期限，以便客户有更多时间迁移到Adobe Commerce as a Cloud Service或升级到支持的发行行。

在此安全修复置备期间，请注意以下事项：

- **仅隔离的安全修补程序文件** — 将按照发布计划为这些版本发布隔离的安全修补程序文件。 在此期间不提供任何安全修补程序版本（无新的 — p版本）。

  要应用独立的安全修补程序文件，客户必须在其受支持的版本行上使用最新的仅安全修补程序发行版（最新的 — p版本），因为独立的安全修补程序将专门针对该版本进行测试。

- **在此期间不为2.4.4或2.4.5版提供质量修复或工程帮助** — 不提供错误修复、质量更新（[质量修补程序工具](../tools/quality-patches-tool/usage.md)）或工程帮助（[Adobe Commerce支持](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)）。

- **不保证PCI合规性：** — 由于2.4.4和2.4.5使用生命周期已结束的PHP版本，因此无法保证这些版本上的商家符合PCI合规性。 继续运行这些版本可能会使您的PCI合规性面临风险。

为了保持完整的安全保护范围并确保PCI合规性，客户必须尽快升级到当前支持的Adobe Commerce版本，或迁移到[Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview)。

| 版本 | 正式发布 | 终止扩展支持 | 安全修复程序配置终止 |
|----------------------|----------------------|-------------------------|------------------------------------|
| Adobe Commerce 2.4.5 | 2022年8月9日 | 2026年8月11日 | 2027年5月 |
| Adobe Commerce 2.4.4 | 2022年4月12日 | 2026年4月14日 | 2027年5月 |

{style="table-layout:auto"}

>[!NOTE]
>
>其他安全修复仅适用于Adobe Commerce客户，不适用于Magento Open Source代码库。


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
    <td colspan="6"></td>
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
   <td>定期支持</td>
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
