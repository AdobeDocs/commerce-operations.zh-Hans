---
title: Adobe Commerce 2.4.3安全修补程序的发行说明
description: 了解Adobe Commerce版本2.4.3的安全修补程序版本中包含的安全错误修复、安全增强和其他安全相关更新。
exl-id: 72d343cd-83d7-48ce-976a-e26ba1b8db27
source-git-commit: 46816b42ea30cb6c5f5ce59752cc00c38d221610
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---


# Adobe Commerce 2.4.3安全修补程序的发行说明

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.3-p3

Adobe Commerce 2.4.3-p3安全版本为以前版本的2.4.3中发现的漏洞提供了安全修复。此版本还包括可提高对最新安全最佳实践合规性的安全增强功能。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB22-38](https://helpx.adobe.com/cn/security/products/magento/apsb22-38.html)。

### 应用`AC-3022.patch`以继续将DHL作为装运承运人提供

DHL已引入架构版本6.2，并且将在不久的将来弃用架构版本6.0。 支持DHL集成的Adobe Commerce 2.4.4及更早版本仅支持版本6.0。部署这些版本的商家应尽早应用`AC-3022.patch`，以继续将DHL作为装运承运人提供。 有关下载和安装修补程序的信息，请参阅[应用修补程序以继续将DHL作为发运运营商提供](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier)知识库文章。

### 安全性亮点

* ACL资源已添加到清单。
* 增强了清单模板的安全性。



## Adobe Commerce 2.4.3-p2

Adobe Commerce 2.4.3-p2安全版本为以前版本中发现的漏洞提供了安全错误修复。 此版本还包括可提高对最新安全最佳实践合规性的安全增强功能。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB22-13](https://helpx.adobe.com/cn/security/products/magento/apsb22-13.html)。  修补程序版本还解决了由`MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch.zip`、`MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch.zip`、`MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch`和`MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch`解决的漏洞。


### 应用`AC-3022.patch`以继续将DHL作为装运承运人提供

DHL已引入架构版本6.2，并且将在不久的将来弃用架构版本6.0。 支持DHL集成的Adobe Commerce 2.4.4及更早版本仅支持版本6.0。部署这些版本的商家应尽早应用`AC-3022.patch`，以继续将DHL作为装运承运人提供。 有关下载和安装修补程序的信息，请参阅[应用修补程序以继续将DHL作为发运运营商提供](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier)知识库文章。

### 安全性亮点

* 在2.3.4中，作为降低安全风险的一部分，为了支持更严格的变量语法，已弃用电子邮件变量用法。 此版本中完全删除了此旧版行为，以继续降低安全风险。

  因此，在早期版本中有效的电子邮件或新闻稿模板在升级到Adobe Commerce 2.4.3-p2后可能无法正常工作。 受影响的模板包括自定义模块或第三方扩展中的管理员覆盖、主题、子主题和模板。 即使在使用[升级兼容性工具](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html?lang=zh-Hans)修复已弃用的使用之后，您的部署仍可能会受到影响。 请参阅[迁移自定义电子邮件模板](https://developer.adobe.com/commerce/frontend-core/guide/templates/email-migration/)，以了解有关迁移受影响模板的潜在影响和准则的信息。

* 现在，将OAuth访问令牌和密码重置令牌存储在数据库中时会进行加密。<!-- AC-520 1323-->

* 已加强验证，以防止上载非字母数字文件扩展名。<!-- AC-479-->

* 当Adobe Commerce处于生产模式时，Swagger现在默认处于禁用状态。<!-- AC-1450-->

* 开发人员现在可以按端点配置Adobe Commerce RESTful端点接受的阵列大小限制。 查看[API安全性](https://developer.adobe.com/commerce/webapi/get-started/api-security/)。<!-- AC-465-->

* 添加了以下机制：限制用户可在系统范围内通过Web API请求的资源大小和数量，以及覆盖单个模块的默认值。 此增强功能解决了`MC-43048__set_rate_limits__2.4.3.patch`解决的问题。 查看[API安全性](https://developer.adobe.com/commerce/webapi/get-started/api-security/)。<!-- AC-1120-->


## 2.4.3-p1

Adobe Commerce 2.4.3-p1安全版本为先前版本(Adobe Commerce 2.4.3和Magento Open Source 2.4.3)中发现的漏洞修复了安全错误。 此版本还包括可提高对最新安全最佳实践合规性的安全增强功能。


有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB21-86](https://helpx.adobe.com/cn/security/products/magento/apsb21-86.html)。 此补丁发行版本还为[Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/braintree.html?lang=zh-Hans)、[Klarna](https://marketplace.magento.com/klarna-m2-klarna.html)和[Vertex](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)供应商开发的扩展提供了错误修复。

### 应用`AC-3022.patch`以继续将DHL作为装运承运人提供

DHL已引入架构版本6.2，并且将在不久的将来弃用架构版本6.0。 支持DHL集成的Adobe Commerce 2.4.4及更早版本仅支持版本6.0。部署这些版本的商家应尽早应用`AC-3022.patch`，以继续将DHL作为装运承运人提供。 有关下载和安装修补程序的信息，请参阅[应用修补程序以继续将DHL作为发运运营商提供](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier)知识库文章。

### 修补程序

此版本包含以下修补程序，以及针对之前的修补程序版本发布的所有修补程序。

* 修补程序`AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch to address PHP fatal error on upgrade`。 有关修补程序和问题的信息，请参阅[Adobe Commerce升级2.4.3、2.3.7-p1 PHP致命错误修补程序](https://support.magento.com/hc/en-us/articles/4408021533069-Adobe-Commerce-upgrade-2-4-3-2-3-7-p1-PHP-Fatal-error-Hotfix)知识库文章。

### 安全性亮点

**会话ID已从数据库**&#x200B;中删除。 如果商家具有使用存储在数据库中的原始会话ID的自定义设置或安装的扩展，则此代码更改可能会导致重大更改。<!-- MC-40976-->

**限制管理员访问媒体集文件夹**。 默认媒体集权限现在只允许配置明确允许的目录操作（查看、上传、删除和创建）。 管理员用户无法再通过在`catalog/category`或`wysiwyg`目录之外上传的媒体集访问媒体资产。 管理员如果想要访问介质资源，必须将其移至明确允许的文件夹或调整其配置设置。 请参阅[修改媒体库文件夹权限](https://developer.adobe.com/commerce/php/tutorials/backend/modify-image-library-permissions/)。<!-- B2B-1897-->

**降低了对GraphQL查询复杂性的限制**。 GraphQL允许的最大查询复杂性已降低，以防止拒绝服务(DOS)攻击。 查看[GraphQL安全配置](https://developer.adobe.com/commerce/webapi/graphql/usage/security-configuration/)。<!-- PWA-1700-->

已在此版本中修复了&#x200B;**最近的渗透测试漏洞**。<!-- MC-42431-->

已从内容安全策略`unsafe-inline`指令中删除不受支持的源表达式`frame-ancestors`。 [GitHub-33101](https://github.com/magento/magento2/issues/33101)<!-- MC-42632-->

<!-- Last updated from includes: 2025-05-28 17:01:56 -->
