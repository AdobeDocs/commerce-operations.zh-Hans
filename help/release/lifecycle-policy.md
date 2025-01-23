---
title: 软件生命周期政策
description: 了解 Adobe Commerce 版本的软件支持终止关键日期。
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: ce7c322c5cf979a992e6f929c3105daf86d4aa49
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 4%

---


# Adobe Commerce生命周期政策

对于Adobe Commerce 2.4.4及后续版本：

- 为了简化Adobe Commerce生命周期政策并支持客户的任务关键型需求，Adobe将支持时间从Adobe Commerce 2.4.4及更高版本的正式发布日期(GA)延长到了三年。 Adobe为2.4.4及更高版本提供了三年支持期的质量修复。 客户可以通过联系[Adobe Commerce支持](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)或自助服务[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)访问质量修复（如果其版本仍然符合质量支持条件）。 下表介绍了Adobe Commerce发行行的软件支持终止日期。

- Adobe通过安全补丁发行版提供三年支持期的安全修复。

- 对于严重的安全问题，例如零日漏洞，Adobe为使用受支持版本的所有客户提供了[修补程序](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-)，即使他们不在最新修补程序或安全修补程序版本中。 请注意，修补程序并不全面，也不能解决通过升级到最新版本可解决的所有安全问题。

- Adobe不提供对第三方服务和软件依赖项（例如PHP和MySQL）的安全性和质量修复，这些服务和软件依赖项在客户处于Adobe Commerce的三年支持期时可能会终止。 有关经过测试和受支持的第三方技术的完整列表，请参阅[系统要求](../installation/system-requirements.md)。

- Adobe提供了与第三方服务和软件依赖项的兼容性，而客户在仅限安全的修补程序版本中启用了Adobe Commerce的三年支持期，但前提是客户可以这样做而不会引入向后不兼容的更改。

## 扩展支持

Adobe鼓励客户尽快升级。 但是，为了提供更大的灵活性以符合升级计划和业务需求，Adobe为Adobe Commerce客户2.4.4和2.4.5版提供一年支持扩展，而无额外费用。支持扩展包括核心应用程序的质量和安全修补程序，有效期最长为一年。

>[!NOTE]
>
>扩展支持仅向Adobe Commerce客户提供。 它不适用于Magento Open Source代码库。

## 软件支持终止

| 版本 | 正式发布 | 结束常规支持<sup>1</sup> | 终止扩展支持 | 依赖的PHP版本 | 依赖的MariaDB版本 |
|----------------------|----------------------|------------------------------------|-------------------------|-----------------------|------------------------------|
| Adobe Commerce 2.4.7 | 2024年4月9日 | 2027年4月9日 | 不适用 | 8.2和8.3 | 10.6 |
| Adobe Commerce 2.4.6 | 2023年3月14日 | 2026年8月11日<sup>2</sup> | 不适用 | 8.1和8.2 | 10.6 |
| Adobe Commerce 2.4.5 | 2022年8月9日 | 2025年8月9日 | 2026年8月11日 | 8.1 | 10.6<sup>3</sup> |
| Adobe Commerce 2.4.4 | 2022年4月12日 | 2025年4月24日 | 2026年4月14日 | 8.1 | 10.6<sup>4</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup>软件支持终止包括质量修复终止和安全修复结束。
>- <sup>2</sup>已更新，以与2.4.5的扩展支持的结束时间保持一致。
>- <sup>3</sup>从2.4.5-p11安全修补程序开始。
>- <sup>4</sup>从2.4.4-p12安全修补程序开始。
>- 请参阅[软件生命周期策略](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)。

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
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
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
   <td style="background-color:#67ac68;"></td>
   <td>定期支持</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>扩展支持</td>
  </tr>
 </tbody>
</table>
