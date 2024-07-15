---
title: 软件生命周期政策
description: 了解 Adobe Commerce 版本的软件支持终止关键日期。
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 7df5edf2acba706fb01f58cc3749c4a2bf136fc5
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 5%

---


# Adobe Commerce生命周期政策

对于Adobe Commerce 2.4.4及后续版本：

- 为了简化Adobe Commerce生命周期政策并支持客户的任务关键型需求，Adobe将支持时间从Adobe Commerce 2.4.4及更高版本的正式发布日期(GA)延长到了三年。 Adobe为2.4.4及更高版本提供了三年支持期的质量修复。 客户可以通过联系[Adobe Commerce支持](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html)或自助服务[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)访问质量修复（如果其版本仍然符合质量支持条件）。 有关Adobe Commerce版本行的软件支持终止日期，请参阅下表。

- Adobe通过安全补丁发行版提供三年支持期的安全修复。

- 对于严重的安全问题，例如零日漏洞，Adobe为使用受支持版本的所有客户提供了[修补程序](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)，即使他们不在最新修补程序或安全修补程序版本中。 请务必注意，修补程序并不是一个通用修补程序，它不能解决所有可以通过升级到最新版本来修复的安全问题。

- Adobe不提供对第三方服务和软件依赖项（例如PHP和MySQL）的安全性和质量修复，这些服务和软件依赖项在客户处于Adobe Commerce的三年支持期时可能会终止。 有关经过测试和受支持的第三方技术的完整列表，请参阅[系统要求](../installation/system-requirements.md)。

- Adobe提供了与第三方服务和软件依赖项的兼容性，而客户在仅限安全的修补程序版本中启用了Adobe Commerce的三年支持期，但前提是客户可以这样做而不会引入向后不兼容的更改。

## 软件支持终止

| 版本 | 正式发布 | 软件支持终止<sup>1</sup> | 依赖的PHP版本 | 依赖的MariaDB版本 |
|----------------------|----------------------|-------------------------------------|-----------------------|------------------------------|
| Adobe Commerce 2.4.7 | 2024年4月9日 | 2027年4月9日 | 8.2和8.3 | 10.6 |
| Adobe Commerce 2.4.6 | 2023年3月14日 | 2026年3月14日 | 8.1和8.2 | 10.6 |
| Adobe Commerce 2.4.5 | 2022年8月9日 | 2025年8月9日 | 8.1 | 10.5<sup>2</sup> |
| Adobe Commerce 2.4.4 | 2022年4月12日 | 2025年4月24日 | 8.1 | 10.5<sup>3</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup>软件支持终止包括质量修复终止和安全修复结束。
>- <sup>2</sup>从2.4.5-p8安全修补程序开始。
>- <sup>3</sup>从2.4.4-p9安全修补程序开始。
>- 请参阅[软件生命周期策略](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)。

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
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
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="8"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**键**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">支持</td>
   <td>Adobe Commerce的安全性和质量修补程序</td>
  </tr>
  <!-- <tr>
   <td style="background-color:#cd3c3c;">End of software support</td>
   <td>Version that has reached end of software support.</td>
  </tr>
 </tbody> -->
</table>
