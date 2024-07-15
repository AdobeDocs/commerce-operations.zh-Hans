---
title: 发布计划
description: 了解 Adobe 打算何时发布 Adobe Commerce 的新功能。
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: e9ef167f5425407f6b1850f0dd913d5d3e2bd628
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 2%

---

# 发布计划

Adobe不断努力在使产品升级变得简单且可预测，同时更快地向早期采用者提供改进和新功能之间找到合适的平衡（请参阅[版本控制策略](versioning-policy.md)）。 此时间表的目的是提供Adobe计划宣布推出重要新功能的日期。 这些功能在一年中可能会有所不同。 但是，在本页指定的日期之间，Adobe会定期并持续发布对扩展性工具、基础架构和SaaS产品（服务）的改进。

对于核心Adobe Commerce PHP应用程序的每个受支持的发行行，Adobe将发布[修补程序](versioning-policy.md#patch-release)。 修补程序版本提供了升级核心代码库的机会，可确保您的平台安全、可靠且高性能。 功能独立于核心代码库，可通过[外部模块、扩展、工具或Web服务](versioning-policy.md#extensibility-infrastructure-and-services-release)使用。

>[!NOTE]
>
>从2024年开始，Adobe不再提供对修补程序的“预发布”访问。 相反，对于2.4.7及更高版本，Adobe Commerce客户可以使用[测试版](beta.md)来访问用于测试和开发用途的正式发布之前的可用性代码。

下表提供了计划发放的日期（日期可能会更改）：

<table>
<thead>
  <tr>
    <th>正式发布</th>
    <th>功能</th>
    <th>PHP核心</th>
  </tr>
</thead>
<tfoot>
   <tr>
      <td colspan="3"><strong>图例</strong>
         <ul>
           <li><strong><img alt="B2B功能图标" src="../assets/icons/enterprise.svg"></img> B2B</strong> - Adobe Commerce的B2B扩展的新增功能、增强功能和错误修复。 有关B2B扩展版本的详细信息，请参阅<a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">B2B发行说明</a>。</li>
            <li><strong><img alt="“可扩展性功能”图标" src="../assets/icons/brackets.svg"></img>可扩展性</strong> — 新的开发人员工具和服务实现了进程外可扩展性，这些工具和服务独立于修补程序版本提供。 例如，管理员UI SDK、Commerce的Adobe I/O事件和API Mesh。</li>
            <li><strong><img alt="基础架构功能图标" src="../assets/icons/servers.svg"></img>基础架构</strong> — 云基础架构上的Adobe Commerce和适用于Commerce包的Cloud Tools Suite的新增功能和增强功能，这些功能旨在部署和管理Cloud平台上的Adobe Commerce安装和升级。</li>
            <li><strong><img alt="“补丁版本”图标" src="../assets/icons/file-code.svg"></img>修补程序</strong> — 更新了核心Adobe Commerce PHP应用程序，其中包括安全性、合规性、性能和高优先级质量修复。</li>
            <li><strong><img alt="“服务”功能图标" src="../assets/icons/feature.svg"></img>服务</strong> — 独立于修补程序版本提供的新SaaS功能。 例如，目录服务、实时搜索和产品Recommendations。</li>
         </ul>
      </td>
   </tr>
</tfoot>
<tbody>
  <tr>
    <td>2024年2月13日</td>
    <td><img alt="“可扩展性功能”图标" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">可扩展性</a><br><img alt="基础架构功能图标" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">基础架构</a><br><img alt="“服务”功能图标" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">服务</a></td>
    <td><img alt="“补丁版本”图标" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">安全修补程序</a>：2.4.6-p4、2.4.5-p6、2.4.4-p7</td>
  </tr>
  <tr>
    <td>2024年3月12日</td>
    <td>—</td>
    <td><img alt="“补丁版本”图标" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">Beta修补程序</a>： 2.4.7-beta3</td>
  </tr>
  <tr>
    <td>2024年4月9日</td>
    <td><img alt="“可扩展性功能”图标" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">可扩展性</a><br><img alt="基础架构功能图标" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">基础架构</a><br><img alt="“服务”功能图标" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">服务</a></td>
    <td><img alt="“补丁版本”图标" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md"><strong>Adobe Commerce 2.4.7</a></strong>：<ul><li>性能改进</li><li>质量增强</li><li>安全性增强</li><li>第三方依赖项更新</li></ul><img alt="“补丁版本”图标" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">安全修补程序</a>：2.4.6-p5、2.4.5-p7、2.4.4-p8</td>
  </tr>
  <tr>
    <td>2024年6月11日</td>
    <td><img alt="“可扩展性功能”图标" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">可扩展性</a><br><img alt="基础架构功能图标" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">基础架构</a><br><img alt="“服务”功能图标" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">服务</a></td>
    <td><img alt="“补丁版本”图标" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">安全修补程序</a>：2.4.7-p1、2.4.6-p6、2.4.5-p8、2.4.4-p9</td>
  </tr>
  <tr>
    <td>2024年8月13日</td>
    <td><img alt="“可扩展性功能”图标" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">可扩展性</a><br><img alt="基础架构功能图标" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">基础架构</a><br><img alt="“服务”功能图标" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">服务</a></td>
    <td><img alt="“补丁版本”图标" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">安全修补程序</a>：2.4.7-p2、2.4.6-p7、2.4.5-p9、2.4.4-p10</td>
  </tr>
  <tr>
    <td>2024年10月8</td>
    <td><img alt="“可扩展性功能”图标" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">可扩展性</a><br><img alt="基础架构功能图标" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">基础架构</a><br><img alt="“服务”功能图标" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">服务</a></td>
    <td><img alt="“补丁版本”图标" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">Beta修补程序</a>： 2.4.8-beta1<br><img alt="“补丁版本”图标" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">安全修补程序</a>： 2.4.7-p3、2.4.6-p8、2.4.5-p10、2.4.4-p11</td>
  </tr>
</tbody>
</table>
