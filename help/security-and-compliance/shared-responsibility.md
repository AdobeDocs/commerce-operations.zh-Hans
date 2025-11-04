---
title: 分担责任的安全性和运营模式
description: 了解Adobe Commerce中涉及的每个云基础架构项目的安全责任。
exl-id: f3cc1685-e469-4e30-b18e-55ce10dd69ce
source-git-commit: aac78fc95b86951f352a636eef33e0b79b22a183
workflow-type: tm+mt
source-wordcount: '2939'
ht-degree: 0%

---

# 分担责任的安全性和运营模式

云基础架构上的Adobe Commerce是一项基于平台即服务(PaaS)的服务，它依赖于分担责任的安全性和运营模式。 这些责任在Adobe、商家、云服务提供商和内容交付网络(CDN)提供商之间分担。 各方对保护和运行Adobe Commerce应用程序以及部署在云基础架构上的特定于商家的代码和扩展承担不同的责任。

此共享模型使商家能够设计和实施高度灵活、可定制和可扩展的解决方案，以满足其业务需求，同时最大限度地降低运营责任和成本。

>[!VIDEO](https://video.tv.adobe.com/v/3458392/?learn=on&enablevpops)

通常，Adobe负责以下工作：

- 开发和维护安全的核心应用程序代码
- 维护平台的安全性
- 确保该平台符合SOC 2和PCI标准，并与PCI标准的技术组件（例如PHP、Redis）兼容
- 响应与核心平台有关的安全问题
- 与云服务提供商和CDN合作伙伴合作，解决出现的任何问题

商家负责以下事项：

- 维护自定义代码以及与第三方应用程序集成的安全性
- 确保安全的应用程序开发
- 如果商户的支付处理器要求，则获取PCI认证
- 响应和响应安全事件

## Adobe职责

Adobe负责云基础架构环境以及核心解决方案代码上的Adobe Commerce的安全性和可用性。 此外，Adobe还负责必要的活动和机制来维护Adobe Commerce在云基础架构解决方案中的安全性，包括：

- 在云基础架构上为Adobe Commerce支持的应用程序（如云数据存储和搜索功能）应用服务器级安全性和修补程序
- 对云基础架构代码的核心Adobe Commerce进行渗透测试和扫描
- 对公共云服务提供商的身份和访问管理(IAM)解决方案和权限管理（PCI合规性要求）进行半年一次的审查和审核
- 对授权用户(包括Adobe员工和承包商)进行半年一次的审查和审核（PCI合规性要求）
- 对备份和恢复功能进行年度测试和文档记录
- 配置服务器和外围防火墙
- 在云基础架构存储库上连接和配置Adobe Commerce
- 定义、测试、实施和记录Adobe职责范围内各领域的灾难恢复(DR)计划
- 定义全球平台Web应用程序防火墙(WAF)规则
- 加强操作系统(OS)
- 在云基础架构上实施并维护内容分发网络(CDN)和应用程序性能管理(APM)解决方案与Adobe Commerce的集成
- 对云基础架构代码的核心Adobe Commerce发布定期安全更新和其他更新（应用修补程序是商家的责任）
- 管理商家支持和支持访问控制（例如Zendesk）
- 监控、记录和修复与云基础架构平台基础架构上的Adobe Commerce有关的安全事件
- 监控平台操作，并在云基础架构商户上为Adobe Commerce提供全天候支持
- 配置生产和暂存环境
- 评估对平台操作和基础架构的潜在安全威胁
- 扩展计算、存储、网格和其他资源，如与商户的服务级别协议(SLA)中所述
- 设置DNS(仅限云基础架构平台基础架构上的Adobe Commerce)
- 测试平台的安全漏洞

Adobe维护用于Adobe Commerce解决方案的基础架构和服务的PCI认证。  商家负责遵守自定义代码、系统和网络流程以及组织。

Adobe还可确保在适用的SLA中商定的商家基础设施的可用性。

## 商户责任

该商家负责为其云基础架构解决方案上的Adobe Commerce的特定自定义实例遵循以下安全最佳实践：

- 将云基础架构配置文件上必需的Adobe Commerce添加到存储库
- 在Adobe发布其自定义云基础架构Adobe Commerce解决方案后，立即将其安全修补程序和其他修补程序应用到这些解决方案
- 在供应商发布安全修补程序和其他修补程序后，立即将其应用于所有自定义扩展和代码
- 创建、部署和测试自定义清漆VCL文件
- 在云基础架构解决方案上设计、设置主题、安装、集成和保护自定义的Adobe Commerce，包括所有自定义扩展和代码
- 授予和撤销用户对商家Adobe Commerce实例的云基础架构配置、应用程序和平台的访问权限
- 处理与商户的内部网络、服务器、基础架构以及基于Adobe Commerce在云基础架构平台上构建的任何自定义应用程序相关的安全问题
- 在云基础架构上安装Adobe Commerce命令行集成(CLI)工具
- 按照PCI-DSS准则的定义，保持定制应用程序和其他内部过程所需的PCI合规性级别

  >[!NOTE]
  >
  >为了最大程度地减少必须审查的方面，商家的PCI合规性建立在Adobe Commerce和云托管提供商的PCI认证之上。

- 在云基础架构代码和平台上的核心Adobe Commerce中运行PCI ASV扫描并修复问题
- 监控所有可能显示潜在安全威胁的应用程序活动，包括渗透测试、漏洞扫描和日志
- 在云基础架构解决方案和用户帐户上监控和响应安全事件，包括与商家Adobe Commerce相关的鉴证、补救和报告
- 获取DNS提供商并配置和维护任何特定于商家的DNS记录
- 在自定义应用程序上运行性能测试
- 保护对平台帐户的访问、实例访问和应用程序的安全
- 测试和QA自定义应用程序
- 维护商家连接到Adobe Commerce上的云基础架构应用程序上的任何系统或网络的安全

## Cloud Service提供商职责

Adobe依靠成熟的云服务提供商在云基础架构上托管Adobe Commerce的云服务器基础架构。 这些提供商负责网络安全，包括通过防火墙系统和入侵检测系统(IDS)的路由、交换和外围网络安全。 云服务提供商还负责在云基础架构解决方案上托管Adobe Commerce的数据中心的物理安全以及数据中心的环境安全。

云服务提供商还负责：

- 为其云服务维护PCI DSS、SOC 2和ISO 27001认证
- 保护虚拟机管理程序
- 保护数据中心（包括物理和网络访问）

## CDN提供商责任

Adobe Commerce on cloud infrastructure解决方案使用CDN提供商来加快页面加载时间、缓存内容并立即清除过时的内容。 这些提供商还负责与其CDN直接相关或影响其CDN的安全问题，以及定义和维护CDN WAF规则。

## 安全责任摘要

>[!BEGINSHADEBOX]

以下摘要表使用RACI模型来显示Adobe、商家和云服务提供商之间共享的安全责任：

**R** — 负责人
**A** — 责任人
**C** — 已咨询
**I** — 已通知

>[!ENDSHADEBOX]

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
    <td>正在将修补程序应用于支持服务<br>（例如，Nginx或MySQL。）</td>
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
    <td>部署platform WAF规则</td>
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
    <td>缩放（PaaS和网格）</td>
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
    <td>将存储库连接到云基础架构上的Adobe Commerce</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>正在配置源存储库<sup>1</sup></td>
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
    <td>配置New Relic APM和基础架构应用程序</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>安装New Relic APM和基础架构应用程序</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>支持New Relic APM和基础架构应用程序</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>正在配置Nginx<sup>3</sup></td>
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
    <td>正在云基础架构PCI扫描上修复Adobe Commerce<sup>4</sup></td>
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
    <td>Adobe灾难恢复计划以及备份和恢复的年度测试和文档记录</td>
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
      <p><sup><strong>1</strong></sup>仅当云基础架构存储库上的Adobe Commerce用作主存储库时。 使用其他外部存储库由商家全权负责。</p>
      <p><sup><strong>2</strong></sup> Adobe为CDN提供商的问题提供级别1支持。</p>
      <p><sup><strong>3</strong></sup>商家负责为其应用程序配置的任何Ngnix控件。</p>
      <p><sup><strong>4</strong></sup>对于PCI，渗透测试要求在Adobe和商家之间共享。</p>
    </td>
  </tr>
</tfoot>
</table>

## 运营责任摘要

>[!BEGINSHADEBOX]

以下汇总表阐明了Adobe和商家在云基础架构上开发、部署、维护和保护Adobe Commerce时的运营责任。

>[!ENDSHADEBOX]

### 编码与开发

#### 核心Adobe Commerce代码

|     | Adobe | 商家 |
| --- | --- | --- |
| 将更新和修补程序发布到Adobe Commerce核心 | R |     |
| 文件系统的可用性和修补 | R |  |
| 将更新和修补程序发布到ECE-Tools | R |     |
| 核心Adobe Commerce应用程序质量 | R |     |

{style="table-layout:auto"}

#### 代码存储库

|     | Adobe | 商家 |
| --- | --- | --- |
| repo.magento.com的可用性 | R |     |
| Adobe Commerce在Cloud Git服务器上的可用性 | R |     |
| 其他商家选择的代码存储库（GitHub、Bitbucket、托管的Git服务器） |     | R |

{style="table-layout:auto"}

#### Cloud Docker

|     | Adobe | 商家 |
| --- | --- | --- |
| 使Cloud Docker容器可供下载 | R |   |
| Cloud Docker的部署和设置（可选） |     | R |
| 任何其他本地开发设置 |     | R |

{style="table-layout:auto"}

#### COMMERCE CLOUD CLI

|     | Adobe | 商家 |
| --- | --- | --- |
| 欧洲经委会工具的持续质量和更新 | R |   |
| 安装最新的ECE工具版本 |     | R |

{style="table-layout:auto"}

#### 自定义

|  | Adobe | 商家 |
| --- | --- | --- |
| 自定义Adobe Commerce模块和代码 |     | R |
| 扩展 |     | R |
| 自定义集成 |     | R |

{style="table-layout:auto"}

#### 部署

|     | Adobe | 商家 |
| --- | --- | --- |
| 用于构建和部署代码的基础架构的可用性 | R |   |
| 持续高质量的基础架构构建和部署配置管道 | R |   |
| 构建和静态内容部署的配置 |     | R |
| 构建和执行部署治理流程：标准和更改管理 |     | R |
| 部署到暂存环境 |     | R |
| 部署到生产环境 |     | R |
| 生产回滚 |     | R |

{style="table-layout:auto"}

#### 同步环境

商家负责在环境之间同步数据。

#### 修补

|     | Adobe | 商家 |
| --- | --- | --- |
| 为ECE-Tools安装更新和修补程序 |     | R |
| 安装Adobe Commerce核心的更新和修补程序 |     | R |

#### 网站可用性

|  | Adobe | 商家 |
| --- | --- | --- |
| 自定义的Adobe Commerce应用程序和相关网站 |     | R |

#### 性能

|     | Adobe | 商家 |
| --- | --- | --- |
| 核心应用程序调整和优化 | R |   |
| 自定义代码调整和优化 |     | R |
| 自定义Adobe Commerce代码 |     | R |
| 加载测试 |     | R |
| 性能测试 |     | R |

{style="table-layout:auto"}


#### 日志和监控

|     | Adobe | 商家 |
| --- | --- | --- |
| 旋转日志 | R |   |
| 自定义Adobe Commerce应用程序 | | R |
| New Relic服务的可用性：<br>APM应用程序和代理集成、基础结构应用程序、<br>日志记录和集成 | R |   |
| 设置New Relic警报 |     | R |
| 在PaaS服务器上部署New Relic代理 | R |  |

{style="table-layout:auto"}

#### 调试和问题隔离

|     | Adobe | 商家 |
| --- | --- | --- |
| 调试和问题隔离 | R | R |
| 及时支持调试和问题隔离过程 |     | R |

{style="table-layout:auto"}

### 应用程序和服务配置

#### Commerce应用程序

|     | Adobe | 商家 |
| --- | --- | --- |
| 应用程序配置 |     | R |
| 向Adobe Commerce应用程序添加域（基本URL） |     | R |
| 将PaaS配置为使用所部署的Adobe Commerce版本<br><br>支持的服务版本。例如，不同的Commerce版本与特定版本的PHP、Redis等兼容。 |     | R |

{style="table-layout:auto"}

#### 使用cron作业进行任务计划

|     | Adobe | 商家 |
| --- | --- | --- |
| 默认cron作业的可用性 | R | |
| 自定义cron作业的持续质量 |  | R |

{style="table-layout:auto"}

#### 消息队列框架的消息代理

|     | Adobe | 商家 |
| --- | --- | --- |
| RabbitMQ服务的可用性 | R |   |
| 默认RabbitMQ设置的配置 | R |   |
| RabbitMQ的持续质量和修补 | R |   |
| 提交服务请求以安装与安装的Adobe Commerce版本兼容的RabbitMQ版本 |   | R |

{style="table-layout:auto"}

#### PHP服务

|     | Adobe | 商家 |
| --- | --- | --- |
| PHP的可用性 | R |   |
| 默认PHP设置的配置 | R |     |
| 自定义PHP设置的配置 |     | R |
| 配置YAML文件，以使PHP版本与已安装的Adobe Commerce版本兼容 |    | R |

{style="table-layout:auto"}

#### 数据库服务

|     | Adobe | 商家 |
| --- | --- | --- |
| Galera和MariaDB服务的可用性 | R | |
| 正在维护默认数据库设置<br><br>（索引和优化核心表，优化默认sys-admin设置） | R |   |
| 持续维护商家数据和修改的设置<br><br>（配置规范化表与平面表、索引和优化自定义表和第三方表、存档或删除数据、配置系统管理设置） |     | R |
| Galera和MySQL的配置 | R |   |
| Galera和MariaDB的持续质量和修补 | R |   |
| 持续的基础架构优化 | R |   |
| 识别和修复慢查询 |     | R |
| 提交服务请求以安装与安装的Adobe Commerce版本兼容的MariaDB版本 |     | R |
| 设置和维护特定于商家的数据保留策略(Adobe的数据保留策略在商家协议中定义) |     | R |

{style="table-layout:auto"}

#### CDN服务

|     | Adobe | 商家 |
| --- | --- | --- |
| CDN的可用性和质量 | R |   |
| Fastly服务配置（通过扩展/API） |     | R |
| Fastly扩展质量 | R |   |
| Fastly集成VCL片段（与Fastly扩展捆绑在一起）的质量 | R |   |
| 页面缓存优化 |     | R |
| 将域添加到服务、CDN和基础架构 | R |   |
| 自定义VCL代码片段 |     | R |
| WAF和WAF规则 | R |   |

{style="table-layout:auto"}

#### 缓存服务

|     | Adobe | 商家 |
| --- | --- | --- |
| Redis服务的可用性 | R |   |
| 默认Redis设置的配置 | R |   |
| Redis的持续质量和修补 | R |   |
| 提交服务请求以安装与已安装的Adobe Commerce版本兼容的Redis版本 |     | R |

{style="table-layout:auto"}

#### 搜索服务

|     | Adobe | 商家 |
| --- | --- | --- |
| Elasticsearch或OpenSearch的可用性 | R |   |
| 默认Elasticsearch或OpenSearch设置的配置 | R |   |
| 提交服务请求以安装与安装的Elasticsearch版本兼容的Adobe Commerce或OpenSearch版本 |  | R |

{style="table-layout:auto"}

#### 电子邮件服务

|     | Adobe | 商家 |
| --- | --- | --- |
| SendGrid电子邮件服务的可用性及其集成 | R |   |
| 根据限制监控商家的SendGrid使用情况 | R |   |
| 商家只负责将服务用于传出事务性电子邮件<br>该服务不支持发送营销电子邮件。 |     | R |
| 配置可选的第三方电子邮件服务 |     | R |

{style="table-layout:auto"}

#### 第三方服务

|     | Adobe | 商家 |
| --- | --- | --- |
| 第三方服务的可用性和质量 |     | R |

{style="table-layout:auto"}

### Commerce Services扩展

#### 高级报告服务

|     | Adobe | 商家 |
| --- | --- | --- |
| 高级报告服务的可用性 | R |   |
| 高级报告的配置符合高级报告条款和条件 |     | R |

{style="table-layout:auto"}

#### Commerce Intelligence

|     | Adobe | 商家 |
| --- | --- | --- |
| Adobe Commerce Business Intelligence服务的可用性 | R |   |
| MBI数据同步过程 | R |   |
| 检测MBI同步问题 | R |   |
| 配置MBI数据同步到Adobe Commerce Cloud Pro、Starter、内部部署或非Adobe Commerce<br>（API、数据质量和格式、商家网络、Adobe Commerce Cloud DB内部和外部的<br>数据库连接，超过数据阈值） |     | R |
| 配置MBI数据同步到Adobe Commerce Cloud Pro<br>（Adobe Commerce Cloud数据库配置） | R |   |

{style="table-layout:auto"}

>
>商家必须使用最新版本的Live Search、产品推荐和支付服务，以确保最高的稳定性、功能和最符合支持资格。
>Adobe不支持过时的版本，升级可确保您从最新的增强功能和错误修复中受益。
>有关受支持版本的详细信息，请参阅[Commerce服务的产品可用性矩阵](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability#commerce-services)。

#### 产品推荐

|     | Adobe | 商家 |
| --- | --- | --- |
| 产品推荐服务的可用性 | R |   |
| 升级“产品推荐”模块 |   | R |

{style="table-layout:auto"}

#### 实时搜索

|     | Adobe | 商家 |
| --- | --- | --- |
| 实时搜索服务的可用性 | R |   |
| 升级Live Search模块 |   | R |

{style="table-layout:auto"}

#### 店面活动（数据收集）的质量，可加强产品推荐和实时搜索输出

|     | Adobe | 商家 |
| --- | --- | --- |
| 核心主题(Luma) | R |   |
| 自定义主题 |  | R |
| 核心PWA实施 | R |   |
| 自定义PWA实施 |  | R |
| 核心AEM EDS实施(Commerce样板) | R |   |
| 自定义AEM EDS实施 |  | R |
| 任何其他自定义店面实施 |  | R |

{style="table-layout:auto"}

#### 支付服务

|     | Adobe | 商家 |
| --- | --- | --- |
| 支付服务的可用性 | R |   |
| 升级支付模块 |   | R |

{style="table-layout:auto"}

### 网络服务

#### 图像优化

|     | Adobe | 商家 |
| --- | --- | --- |
| 映像优化的可用性和质量 | R |  |
| 图像优化的配置 |     | R |

{style="table-layout:auto"}

#### SSL证书

|     | Adobe | 商家 |
| --- | --- | --- |
| SSL专用证书 — 到期 | R |  |
| 配置SSL证书 | R |  |
| 购买和维护特定于EV的SSL证书（提供的默认证书除外）并提供给Adobe |     | R |

{style="table-layout:auto"}

#### Web应用程序防火墙(WAF)

|     | Adobe | 商家 |
| --- | --- | --- |
| WAF的可用性和配置 | R |  |
| 解决WAF规则误报 | R | |
| 报告WAF规则误报 |     | R |
| WAF规则调整（不支持） |     |     |
| WAF/CDN日志 |     | R |

{style="table-layout:auto"}

#### DDOS

|     | Adobe | 商家 |
| --- | --- | --- |
| 主动IP阻止 |     | R |
| 机器人保护 |     | R |
| DDOS检测 — 第3-4层 | R |   |
| DDOS检测 — 第7层 |     | R |
| DDOS响应 | R |   |

{style="table-layout:auto"}

#### 专用链接

|     | Adobe | 商家 |
| --- | --- | --- |
| 使用Adobe拥有的VPC配置和维护PrivateLink连接（如果使用） | R |   |
| 使用商家拥有的VPC配置和维护PrivateLink连接（如果使用） |     | R |
| SSH（非专用链接）的可用性 | R |   |
| 配置入站到Adobe Commerce云服务端点的PrivateLink | R |   |
| 接受PrivateLink入站到Adobe Commerce云服务端点 |     | R |
| 入站到商家VPC服务端点的PrivateLink的配置 |     | R |
| 接受入站到商家VPC服务端点的PrivateLink | R |   |
| PrivateLink集成（端点到帐户）的配置 |     | R |
| 为PrivateLink端点<br><br>配置商家拥有的VPC（包括任何VPN连接） |     | R |

{style="table-layout:auto"}

### 系统和基础架构

#### 应用程序服务器

|     | Adobe | 商家 |
| --- | --- | --- |
| Nginx的可用性 | R |   |
| Nginx的配置 | R |   |
| Nginx的持续质量和修补 | R |   |

{style="table-layout:auto"}

#### 操作系统

|     | Adobe | 商家 |
| --- | --- | --- |
| 操作系统可用性 | R |   |
| 持续保持操作系统的质量和修补 | R |   |

{style="table-layout:auto"}

#### 备份、高可用性和故障切换

|     | Adobe | 商家 |
| --- | --- | --- |
| 快照和备份过程的可用性 | R |   |
| 为Cloud Pro暂存和生产环境计划备份 | R |   |
| 为Cloud Starter和专业集成环境计划备份 |     | R |
| 高可用性/故障切换 | R |   |

{style="table-layout:auto"}

#### 云服务器和扩展

|     | Adobe | 商家 |
| --- | --- | --- |
| CPU资源、数据中心和磁盘空间的可用性 | R |   |
| 快速部署容量或紧急规模调整的可用性和执行 | R |   |
| 请求快速部署容量 |     | R |
| 根据限制监控vCPU使用情况 | R |   |

{style="table-layout:auto"}
