---
title: 保护您的Commerce站点和基础架构
description: 通过在设置、配置和更新Adobe Commerce安装时实施安全最佳实践来维护安全性。
feature: Best Practices
exl-id: 50d8a464-6496-4e9a-b642-0c6d0eb51ba0
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '2000'
ht-degree: 0%

---

# 保护您的Commerce站点和基础架构

为部署在云基础架构上的Adobe Commerce项目建立和维护安全的环境是Adobe Commerce客户、解决方案合作伙伴和Adobe共同承担的责任。 本指南旨在为方程式中的客户提供最佳实践。

虽然您无法消除所有安全风险，但应用这些最佳实践会强化Commerce安装的安全状况。 安全的站点和基础架构使恶意攻击成为不那么诱人的目标，确保了解决方案和客户敏感信息的安全，并有助于最大限度地减少可能导致站点中断和成本高昂的调查的安全相关事件。

>[!NOTE]
>
>有关在云基础架构上保护和维护Adobe Commerce项目的角色和责任的信息，请参阅[Adobe Commerce安全和合规性指南](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility#security-responsibilities-chart)中的&#x200B;_共享责任模型_。

[所有受支持的版本](../../../release/versions.md)，共：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 优先建议

Adobe认为以下建议对所有客户具有最高优先级。 在所有Commerce部署中实施以下关键安全最佳实践：

![核对清单](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **为您的管理员和所有SSH连接启用双重身份验证**

- [Commerce管理员的安全性](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication.html)

- [安全SSH连接](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/multi-factor-authentication.html) （云基础架构）

在项目上启用MFA后，具有SSH访问权限的云基础架构上的所有Adobe Commerce帐户都必须遵循身份验证工作流。 此工作流需要双重身份验证(2FA)代码，或者API令牌和SSH证书来访问环境。

![检查清单](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **保护管理员**

- [配置非默认管理员URL](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url)，而不是使用默认`admin`或常用术语，如`backend`。 此配置可减少尝试获得对网站的未经授权访问的脚本的风险。

- [配置高级安全设置](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html) — 向URL添加密钥，要求密码区分大小写，并限制管理员会话长度、密码生命周期间隔以及锁定管理员用户帐户之前允许的登录尝试次数。 为了提高安全性，请配置在当前会话过期之前键盘处于非活动状态的长度，并要求用户名和密码区分大小写。

- [启用ReCAPTCHA](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/captcha/security-google-recaptcha.html)以保护管理员免受自动暴力攻击。

- 在将[管理员权限](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions.html)分配给角色和角色分配给管理员用户帐户时，遵循最小权限原则。

![检查清单](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **升级到Adobe Commerce的最新版本**

通过[将您的Commerce项目升级到最新版本的](#upgrade-to-the-latest-release) Adobe Commerce、Commerce服务和扩展(包括Adobe提供的安全修补程序、修补程序和其他修补程序)来保持代码更新。

![清单](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **安全敏感配置值**

使用[配置管理](../../../configuration/cli/set-configuration-values.md)锁定关键配置值。

`lock config`和`lock env` CLI命令可配置环境变量，以防止从管理员更新它们。 该命令将该值写入`<Commerce base dir>/app/etc/env.php`文件。 (对于云基础架构项目上的Commerce，请参阅[存储配置管理](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html#sensitive-data)。)

![检查清单](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **运行安全扫描**

使用[Commerce安全扫描服务](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html)监视所有Adobe Commerce站点是否存在已知的安全风险和恶意软件，并注册以接收修补程序更新和安全通知。

## 确保扩展和自定义代码的安全性

当您通过从Adobe Commerce Marketplace添加第三方扩展来扩展Adobe Commerce，或添加自定义代码时，请应用以下最佳实践来确保这些自定义设置的安全：

![检查清单](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **选择精通安全问题的合作伙伴或解决方案集成商(SI)** — 通过选择遵循安全开发实践并具有防止和解决安全问题的可靠记录的组织，确保安全集成和安全交付自定义代码。

![检查清单](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **使用安全扩展** — 通过与解决方案集成商或开发人员咨询并遵循[Commerce扩展最佳实践](../planning/extensions.md)，确定Adobe部署的最合适且最安全的扩展。

- 仅限来自Adobe Commerce Marketplace或通过解决方案集成商的源扩展。 如果扩展是通过集成商提供的，请确保在集成商发生更改时，扩展许可证的所有权可转移。

- 通过限制扩展和供应商的数量来降低风险。

- 如果可能，在与Commerce应用程序集成之前，请查看扩展代码的安全性信息。

- 确保PHP扩展开发人员遵循Adobe Commerce开发准则、流程和安全最佳实践。 具体来说，开发人员必须避免使用PHP功能，因为这会导致远程代码执行或弱加密。 请参阅[扩展开发人员最佳实践指南](https://developer.adobe.com/commerce/php/best-practices/security/)中的&#x200B;*安全性*。

![检查清单](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **审核代码** — 检查服务器和源代码存储库中的开发剩余项。 确保没有可访问的日志文件、公开可见的.git目录、用于执行SQL语句的隧道、数据库转储、php信息文件或任何其他不需要的、可能在攻击中使用的不受保护的文件。

## 升级到最新版本

Adobe会不断发布更新的解决方案组件，以提高安全性并更好地保护客户免受可能的危害。 升级到最新版本的Adobe Commerce应用程序、已安装的服务和扩展并应用当前修补程序是抵御安全威胁的第一道也是最好的防线。

Commerce通常按季度发布安全更新，但保留根据优先级和其他因素发布主要安全威胁修补程序的权利。

有关可用的Adobe Commerce版本、发行周期以及升级和修补过程的信息，请参阅以下资源：

- [已发布版本](../../../release/versions.md)
- [产品可用性](../../../release/product-availability.md) (Adobe Commerce服务和Adobe创作的扩展)
- [Adobe Commerce生命周期政策](../../../release/lifecycle-policy.md)
- [升级指南](../../../upgrade/overview.md)
- [如何应用修补程序](../../../upgrade/patches/overview.md)

>[!TIP]
>
>通过订阅[Adobe安全通知服务](https://www.adobe.com/subscription/adbeSecurityNotifications.html)获取最新安全信息并缓解已知安全问题。

## 制定灾难恢复计划

如果您的Commerce站点受到危害，请通过制定和实施全面的灾难恢复计划，控制损坏并快速恢复正常业务运营。

如果客户由于灾难而需要恢复Commerce实例，Adobe可以为客户提供备份文件。 如果适用，客户和解决方案集成商可以执行恢复。

作为灾难恢复计划的一部分，Adobe强烈建议客户[导出其Adobe Commerce应用程序配置](../../../configuration/cli/export-configuration.md)，以便在业务连续性需要时轻松重新部署。 将配置导出到文件系统的主要原因是系统配置优先于数据库配置。 在只读文件系统中，必须重新部署应用程序以更改敏感的配置设置，从而提供额外的保护层。

### 其他信息

**Adobe Commerce已部署在云基础架构上**

- [备份和灾难恢复](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#backup-and-disaster-recovery)

- 在云基础架构上[存储Adobe Commerce的配置管理](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html)

**Adobe Commerce已部署在本地**

- [导出配置设置](../../../configuration/cli/export-configuration.md)

   - [导入配置设置](../../../configuration/cli/import-configuration.md)

   - [备份和回滚文件系统、介质和数据库](../../../installation/tutorials/backup.md)

## 维护安全的站点和基础架构

此部分总结了维护Adobe Commerce安装的站点和基础架构安全性的最佳实践。 其中许多最佳实践都侧重于保护计算机基础架构的总体安全，因此其中某些建议可能已经实施。

![检查清单](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **阻止未经授权的访问** — 与您的托管合作伙伴一起设置VPN通道以阻止对Commerce网站和客户数据的未经授权的访问。 设置SSH隧道以阻止对Commerce应用程序的未授权访问。

![检查清单](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **使用Web应用程序防火墙** — 分析通信并发现可疑模式，例如使用Web应用程序防火墙发送到未知IP地址的信用卡信息。

部署在云基础架构上的Adobe Commerce安装可以使用随[Fastly服务集成](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)提供的内置WAF服务

![核对清单](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **配置高级密码安全设置** — 按照PCI数据安全标准第8.2.4节中的建议，设置强密码并至少每90天更改一次。请参阅[配置管理员安全设置](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html)。

![检查清单](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **使用HTTPS** — 如果Commerce站点是新实施的，请使用HTTPS启动整个站点。 Google不仅使用HTTPS作为排名因素，而且许多用户甚至不考虑从网站购买，除非网站受HTTPS保护。

## 防范恶意软件

针对电子商务网站的恶意软件攻击非常普遍，威胁方不断开发从交易中获取信用卡和个人信息的新方法。

然而，Adobe发现，大多数网站上的妥协并非源自于一个创新的黑客。 相反，威胁行为人通常会利用文件系统中现有的未修补漏洞、较差的密码以及较弱的所有权和权限设置。

在最常见的攻击中，恶意代码会注入到客户存储的绝对页眉或绝对页脚中。 在那里，代码会收集客户在店面中输入的表单数据，包括客户登录凭据和结账表单数据。 然后，此数据会出于恶意目的发送到另一个位置，而不是发送到Commerce后端。 此外，恶意软件可能会危害管理员，使其以假形式执行替换原始支付表单的代码，从而覆盖支付提供商设置的任何保护。

客户端信用卡掠夺者是一种将代码嵌入商户网站内容的恶意软件，可在用户的浏览器中执行，如下图所示。

![针对电子商务网站的恶意软件攻击的数据流](../../../assets/playbooks/malware-data-flow.svg)

执行某些操作（如用户提交表单或修改字段值）后，撇取器会序列化数据并将其发送到第三方端点。 这些端点通常是其他受到危害的网站，它们充当中继将数据发送到其最终目的地。


>[!TIP]
>
>如果Commerce站点受到恶意软件攻击的影响，请按照Adobe Commerce最佳实践[响应安全事件](../maintenance/respond-to-security-incident.md)。

### 了解最常见的攻击

以下是Adobe建议所有Commerce客户注意并采取措施抵御的常见攻击类别列表：

- **站点损坏** — 攻击者通过更改站点的外观或添加自己的消息来破坏网站。 尽管对网站和用户帐户的访问受到威胁，但支付信息通常仍保持安全。

- **僵尸网络** — 客户的Commerce服务器成为发送垃圾邮件电子邮件的僵尸网络的一部分。 列入阻止列表虽然用户数据通常不会受到危害，但客户的域名可能会被垃圾邮件过滤器破坏，从而阻止从域投放任何电子邮件。 或者，客户站点成为僵尸网络的一部分，导致其他站点上的分布式拒绝服务(DDoS)攻击。僵尸网络可能会阻止到Commerce服务器的入站IP流量，从而阻止客户进行购物。

- **直接服务器攻击** — 数据被破坏，后门和恶意软件已安装，站点操作受到影响。 未存储在服务器上的付款信息不太可能通过这些攻击而受到危害。

- **无声卡捕获** — 在此最灾难性的攻击中，入侵者安装隐藏的恶意软件或卡捕获软件，或者更糟的是，修改签出过程以收集信用卡数据。 然后，数据被发送到另一个网站在黑暗网络上出售。 此类攻击可能会在较长的一段时间内不被发现，并可能导致客户帐户和财务信息严重受损。

- **静默密钥记录** — 威胁操作者在客户服务器上安装密钥记录代码以收集管理员用户凭据，以便他们能够登录并发起其他攻击，而不会被检测到。

### 防止密码猜测攻击

暴力密码猜测攻击可能导致未经授权的管理员访问。 通过以下最佳实践保护您的站点免受这些攻击：

- 识别和保护可以从外部访问Commerce安装的所有点。

  在配置Commerce项目时，您可以按照Adobe的[优先级建议](#priority-recommendations)，保护对管理员的访问，这通常需要最强的保护。

- 通过设置一个访问控制列表（仅允许来自指定IP地址或网络的用户访问），控制对Commerce站点的访问。

  您可以使用带有自定义VCL代码片段的Fastly Edge ACL来过滤传入的请求并允许按IP地址访问。 查看[自定义VCL以允许请求](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html)。


  >[!TIP]
  >
  >如果您雇用远程员工，请确保远程员工的IP地址包含在有权访问Commerce站点的地址列表中。

### 防止点击劫持攻击

Adobe通过提供可包含在店面请求中的`X-Frame-Options` HTTP请求标头，保护您的商店免受点击劫持攻击。 请参阅[Adobe Commerce配置指南](../../../configuration/security/xframe-options.md)中的&#x200B;*阻止点击劫持攻击*。
