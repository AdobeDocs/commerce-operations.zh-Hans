---
title: 分担责任
description: 了解Adobe Commerce中涉及的每个云基础架构项目的安全责任。
source-git-commit: d216418c69cb972e93c04b5d5cc0a8ab0495653d
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 0%

---


# 共享责任安全模型

云基础架构上的Adobe Commerce是一款依赖于共同责任安全模式的平台即服务(PaaS)产品。 Adobe、商家、云服务提供商和内容交付网络(CDN)提供商各自承担不同的责任，在云基础架构应用程序和特定于商家的代码和扩展上维护Adobe Commerce的安全性。

这种方法使商家能够设计和实施高度灵活、可定制和可扩展的解决方案，以最好地满足其业务需求，同时最大限度地降低运营责任和成本。

通常，Adobe负责开发和维护安全的核心应用程序代码，维护平台的安全性，确保平台的SOC 2和PCI合规性及其与PCI合规性技术组件（例如，PHP、Redis）的兼容性，并响应与核心平台相关的安全问题。 Adobe还负责与云服务提供商和CDN合作伙伴合作，以解决可能出现的问题。

商户负责维护安全的自定义代码以及与第三方应用程序的集成，确保安全应用程序开发，如果商户的支付处理器要求，则获得PCI认证，以及响应和响应安全事件。

## Adobe职责

Adobe负责云基础架构环境上的Adobe Commerce以及云基础架构解决方案代码上的核心Adobe Commerce的安全性和可用性。 此外，Adobe还负责必要的活动和机制来维护Adobe Commerce云基础架构解决方案的安全性，包括：

- 在云基础架构上为Adobe Commerce支持的应用程序（如云数据存储和搜索功能）应用服务器级安全性和修补程序
- 对云基础架构代码的核心Adobe Commerce进行渗透测试和扫描
- 对公共云服务提供商的身份和访问管理(IAM)解决方案和权限管理（PCI合规性要求）进行半年一次的审查/审核
- 对授权用户(包括Adobe员工和承包商)进行半年度审查/审计（PCI合规性要求）
- 对备份和恢复功能进行年度测试和文档记录
- 配置服务器和外围防火墙
- 在云基础架构存储库上连接和配置Adobe Commerce
- 为Adobe职责范围内的各个领域定义、测试、实施和记录灾难恢复(DR)计划
- 定义全球平台Web应用程序防火墙(WAF)规则
- 加强操作系统(OS)
- 在云基础架构上实施并维护内容分发网络(CDN)和应用程序性能管理(APM)解决方案与Adobe Commerce的集成
- 对云基础架构代码的核心Adobe Commerce发布定期安全更新和其他更新（应用修补程序是商家的责任）
- 管理商家支持和支持访问控制（例如Zendesk）
- 监控、记录和修复与云基础架构平台基础架构上的Adobe Commerce有关的安全事件
- 监控平台操作，并在云基础架构商户上为Adobe Commerce提供全天候支持
- 配置生产和暂存环境
- 评估对平台操作和基础架构的潜在安全威胁
- 根据与商户的服务级别协议(SLA)中的说明，扩展计算、存储、网格和其他资源
- 设置DNS(仅限云基础架构平台基础架构上的Adobe Commerce)
- 测试平台的安全漏洞

Adobe维护Adobe Commerce云基础架构解决方案运营中使用的基础架构和服务的PCI认证，而商家则负责自定义代码、系统和网络流程以及组织的合规性。

Adobe还可确保商户基础设施在适用的SLA中商定的可用性。

## 商户责任

该商家负责为其云基础架构解决方案上的特定Adobe Commerce自定义实例遵循以下安全最佳实践，并负责：

- 将云基础架构配置文件上必需的Adobe Commerce添加到存储库
- 在按Adobe发布安全修补程序和其他修补程序后，立即将其应用于云基础架构解决方案上的自定义Adobe Commerce
- 在供应商发布安全修补程序和其他修补程序后，立即将其应用于所有自定义扩展和代码
- 创建、部署和测试自定义清漆VCL文件
- 在云基础架构解决方案上设计、设置主题、安装、集成和保护自定义的Adobe Commerce，包括所有自定义扩展和代码
- 授予和撤销用户对商家Adobe Commerce实例的云基础架构配置、应用程序和平台的访问权限
- 处理与商户的内部网络、服务器、基础架构以及基于Adobe Commerce在云基础架构平台上构建的任何自定义应用程序相关的安全问题
- 在云基础架构上安装Adobe Commerce命令行集成(CLI)工具
- 按照PCI-DSS准则的定义，保持定制应用程序和其他内部过程所需的PCI合规性级别

  >[!NOTE]
  >
  >商家的PCI合规性建立在Adobe Commerce在云基础架构和云托管提供商上的PCI认证之上，以最大程度地减少必须审查的方面。

- 在云基础架构代码和平台上的核心Adobe Commerce中运行PCI ASV扫描并修复问题
- 监控所有可能显示潜在安全威胁的应用程序活动，包括渗透测试、漏洞扫描和日志
- 在云基础架构解决方案和用户帐户上监控和响应安全事件，包括与商家Adobe Commerce相关的鉴证、补救和报告
- 获取DNS提供商并配置和维护任何特定于商家的DNS记录
- 在自定义应用程序上运行性能测试
- 保护对平台帐户的访问、实例访问和应用程序的安全
- 测试和QA自定义应用程序
- 维护商家连接到Adobe Commerce上的云基础架构应用程序上的任何系统或网络的安全

## 云服务提供商责任

Adobe依靠成熟的云服务提供商在云基础架构上托管Adobe Commerce的云服务器基础架构。 这些提供商负责网络安全，包括通过防火墙系统和入侵检测系统(IDS)的路由、交换和外围网络安全。 云服务提供商还负责在云基础架构解决方案上托管Adobe Commerce的数据中心的物理安全以及数据中心的环境安全。

云服务提供商还负责：

- 为其云服务维护PCI DSS、SOC 2和ISO 27001认证
- 保护虚拟机管理程序
- 保护数据中心（包括物理和网络访问）

## CDN提供商责任

Adobe Commerce on cloud infrastructure解决方案使用CDN提供商来加快页面加载时间、缓存内容并立即清除过时的内容。 这些提供商还负责与其CDN直接相关或影响其CDN的安全问题，以及定义和维护CDN WAF规则。

## 安全责任图

下图使用RACI模型（R — 负责，A — 负责，C — 咨询，I — 信息）以视觉方式描绘生态系统关于Adobe Commerce云基础架构共享责任模型的安全责任中的每一方：

<table>
<thead>
  <tr>
    <th>任务</th>
    <th>Adobe</th>
    <th>商家</th>
    <th>云服务提供商</th>
    <th>CDN提供商</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>在云基础架构上应用Adobe Commerce修补程序</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>将修补程序应用到支持服务<br>（例如，Nginx、MySQL）</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>定义原始WAF规则</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>定义CDN WAF规则</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>部署平台WAF规则</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>部署CDN WAF规则</td>
    <td>A</td>
    <td>I</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>修复了Adobe Commerce中有关云基础架构代码的核心错误</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在云基础架构修补程序上发布Adobe Commerce</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>扩展（计算和存储）</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>缩放（PaaS/网格）</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>确保访问源代码，包括repo.magento.com</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在云基础架构CLI工具上安装Adobe Commerce</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>将Adobe Commerce on cloud基础架构配置文件添加到存储库</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>为商家创建项目（入门UI）</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在云基础架构上将存储库连接到Adobe Commerce</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>配置源存储库<sup>1</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>为版本管理器创建用户（入门UI）</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>将代码部署到生产环境中</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>将代码部署到暂存环境</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>集成外部应用程序和扩展</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>安装扩展</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在云基础架构上自定义Adobe Commerce</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在云基础架构上测试自定义Adobe Commerce的性能</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>测试自定义应用程序</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>自定义应用程序的主题和设计</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
    <tr>
    <td>创建、部署和测试自定义清漆VCL</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>配置DNS（仅限平台基础架构）</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>开发CDN扩展并修复错误</td>
    <td>A</td>
    <td>C</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>载入CDN</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>支持CDN<sup>2</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>配置New Relic APM/基础架构</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>安装New Relic APM/基础架构</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>支持New Relic APM/基础架构</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>配置Nginx<sup>3</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>获取DNS提供商（仅限Pro）</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>强化操作系统</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>配置生产和暂存环境</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在云基础架构上访问Zendesk for Adobe Commerce</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>解决商家安全问题</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>解决Adobe Commerce中的云基础架构安全问题</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>解决CDN安全问题</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>解决APM安全问题</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>协助Adobe进行安全研究（软件）</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>协助Adobe进行安全研究（扫描/审核）</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>执行PCI ASV扫描</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在云基础架构PCI扫描上修复Adobe Commerce<sup>4</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>正在修复PaaS PCI扫描</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>管理操作系统和平台密钥</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在云基础架构加密密钥上管理Adobe Commerce</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在云基础架构实例上扫描自定义的Adobe Commerce</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>监控安全日志</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>在云基础架构上管理Adobe Commerce的IAMand权限</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>管理支持访问控制（远程端口）</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>控制商户支持和访问</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>对Adobe灾难恢复计划以及备份和恢复进行年度测试和记录</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>灾难恢复计划的年度测试和文档记录</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
<tfoot>
  <tr>
    <td colspan="5">
      <p><sup><strong>1</strong></sup> 仅当使用Adobe Commerce on cloud infrastructure存储库作为主存储库时。 使用其他外部存储库由商家全权负责。</p>
      <p><sup><strong>2</strong></sup> Adobe为CDN提供商的问题提供级别1支持。</p>
      <p><sup><strong>3</strong></sup> 某些Ngnix控件由商家为其应用程序配置，并由他们负责。</p>
      <p><sup><strong>4</strong></sup> 对于PCI，渗透测试要求在Adobe和商家之间共享。</p>
    </td>
  </tr>
</tfoot>
</table>
