---
title: 软件生命周期策略
description: 了解 Adobe Commerce 版本的软件支持终止关键日期。
source-git-commit: ffa8b957828833d2c3f9bc79c31dc3fa2c6035a5
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 8%

---


# Adobe Commerce生命周期策略

对于Adobe Commerce 2.4及后续版本：

- 为了更好地简化生命周期策略，Adobe为2.4版本提供了质量修复，直到其所基于的PHP版本的支持日期结束。 客户可以通过联系 [Adobe Commerce支持](https://developer.adobe.com/commerce/contributor/community/support/) 或通过自助服务 [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}（如果其版本仍符合质量支持条件）。 请参阅下表，了解Adobe Commerce发行版的软件支持终止日期。

- Adobe仅通过最新补丁或安全补丁版本提供安全修复，即使客户的版本仍符合质量支持的条件。 与质量修复不同，安全修复不能移植到以前的次要版本，也不能移植到支持的次要版本中的先前修补程序版本。

- 对于诸如零日漏洞等关键安全问题，Adobe提供 [修补程序](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) 适用于所有受支持版本的客户，即使他们不在最新的修补程序或安全修补程序版本中。 请务必注意，修补程序不是一个通用的修补程序，并且不会解决通过升级到最新版本将要修复的所有安全问题。

## 软件支持终止

| 版本 | 发行日期 | 软件支持终止<sup>1</sup> | 从属PHP版本 |
| -------------------------------- | ----------------- | ----------------------------------- | --------------------------- |
| Adobe Commerce 2.3 | 2018年11月28日 | 2022年9月8日<sup>2</sup> | 7.3和7.4菲律宾比索<sup>3</sup> |
| Adobe Commerce 2.4.0-2.4.3 | 2020年7月28日 | 2022年11月28日 | 七点四菲律宾比索 |
| Adobe Commerce 2.4.4-2.4.6 | 2022年4月12日 | 2024年11月25日 | 8.1菲律宾比索 |

<sup>1终止软件支持包括终止质量修复和安全修复。</sup><br>
<sup>2软件支持2.3的结束日期已延长到2022年9月8日，以便客户有更多时间升级到2.4.4版，该版本将于2022年3月8日正式发布。</sup><br>
<sup>3 2.3.0-2.3.6依赖于PHP 7.3;2.3.7取决于菲律宾比索7.4。</sup>

>[!NOTE]
>
>请参阅 [软件生命周期策略](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table>
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>商务</td>
    <td>PHP</td>
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
    <td>2.4.0 - 2.4.3</td>
    <td style="text-align:center">7.4</td>
    <td colspan="3" style="background-color:#67ac68;"></td>
    <td style="background-color:#cd3c3c;">11月</td>
    <td colspan="8" ></td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td rowspan="2" style="text-align:center">8.1</td>
    <td></td>
    <td colspan="10" style="background-color:#67ac68;">3月</td>
    <td rowspan="2" style="background-color:#cd3c3c;">11月</td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="9" style="background-color:#67ac68;">8月</td>
  </tr>
</tbody>
</table>

## 键

<table>
  <thead>
   <tr>
    <th></th>
    <th></th>
   </tr>
  </thead>
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">支持</td>
   <td>已通过Adobe完全测试且受支持的版本。</td>
  </tr>
  <tr>
   <td style="background-color:#cd3c3c;">软件支持终止</td>
   <td>软件支持终止的版本。</td>
  </tr>
 </tbody>
</table>
