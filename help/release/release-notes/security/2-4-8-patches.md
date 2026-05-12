---
title: Adobe Commerce 2.4.8安全补丁发行说明
description: 了解Adobe Commerce版本2.4.8的安全修补程序版本中包含的安全错误修复、安全增强和其他安全相关更新。
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: a61409b02e612295fb03a42e22dcfdf5c3eb0e57
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---

# Adobe Commerce 2.4.8安全修补程序的发行说明

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p5

Adobe Commerce 2.4.8-p5安全版本为2.4.8以前版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB26-49](https://helpx.adobe.com/cn/security/products/magento/apsb26-49.html)。

{{b2b-patches}}

### 高亮

此版本包括以下功能亮点：

#### MariaDB 11.8兼容性

Adobe Commerce 2.4.8已经过与MariaDB 11.8的兼容性验证，同时保留对MariaDB 11.4的支持。 此更新解决MariaDB 11.8中引入的SQL行为更改、默认更新和弃用问题，以维护平台稳定性。

#### OpenSearch 3最新的次要版本支持

Adobe Commerce 2.4.8现在支持云基础架构、Cloud Native和内部部署上的Adobe Commerce上最新的OpenSearch 3次要版本。 保持与OpenSearch 2的兼容性。

#### Valkey 9.x LTS支持

Adobe Commerce 2.4.8现在与Valkey 9.x LTS兼容，提供了一个长期支持的缓存后端选项，该选项在Adobe Commerce on cloud infrastructure上受支持。

#### RabbitMQ 4.2支持

Adobe Commerce 2.4.8现在与RabbitMQ 4.2兼容，后者在RabbitMQ 4.1计划于2026年2月终止支持日期之前提供。 与Apache ActiveMQ Artemis的兼容性得以保留，并且ActiveMQ仍然是此仅安全版本行的默认消息队列服务。

#### USPS REST API支持

除了旧版Web Tools API之外，USPS配送集成现在还支持现代化的RESTful USPS API。 管理员可以从管理员配置中选择要使用的USPS集成API。 此更新为USPS Web Tools API弃用做准备。

#### Magento拥有的Laminas MVC分支

为解决Laminas MVC停用问题，Adobe Commerce现在使用Magento拥有的`laminas-mvc`分支（发布为`magento/magento-zf-mvc`）。 此分支代码确保持续修补并长期符合Adobe Commerce 2.4.8的安全要求。

## 2.4.8-p4

Adobe Commerce 2.4.8-p4安全版本为2.4.8以前版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB26-05](https://helpx.adobe.com/cn/security/products/magento/apsb26-05.html)。

{{b2b-patches}}

### 高亮

此版本包括以下功能亮点：

#### 对DHL配送集成的MyDHL REST API支持

除了现有的DHL Express XML集成之外，DHL传送集成现在还支持MyDHL REST API。 此更新与DHL的当前API栈栈保持一致，并为弃用旧版XML API做准备。

#### 添加与最新编辑器版本的兼容性

Adobe Commerce 2.4.8已更新，以支持编辑器2.9.x，同时保持与编辑器2.2 LTS兼容。

## 2.4.8-p3

Adobe Commerce 2.4.8-p3安全版本为2.4.8早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-94](https://helpx.adobe.com/cn/security/products/magento/apsb25-94.html)。

{{b2b-patches}}

### 高亮

此版本包括以下功能亮点：

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

* 对ACP2E-3874的修复：现在，订购了多个相同项目时，订单详细信息的REST API响应将包含`base_row_total`和`row_total`属性的正确值。

* 修复了AC-15446：修复了`Magento\Framework\Mail\EmailMessage`中的一个错误，其中`getBodyText()`尝试在`Symfony\Component\Mime\Message`上调用不存在的`getTextBody()`方法，从而确保与Magento 2.4.8-p2和`magento/framework` 103.0.8-p2兼容。

{{oct-2025-backports}}

### 已知问题

#### 签出页面无法加载static.min.js和mixins.min.js

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.8-p2

Adobe Commerce 2.4.8-p2安全版本为2.4.8早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-71](https://helpx.adobe.com/cn/security/products/magento/apsb25-71.html)。

{{b2b-patches}}

## 2.4.8-p1

Adobe Commerce 2.4.8-p1安全版本为2.4.8早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-50](https://helpx.adobe.com/cn/security/products/magento/apsb25-50.html)。

{{b2b-patches}}

### 高亮

此版本包括以下功能亮点：

* **API性能增强** — 解决在上一个安全修补程序之后引入的批量异步Web API端点中的性能降级。<!-- AC-14078 -->

* **CMS阻止访问修复** — 解决具有受限权限（例如仅限促销访问）的管理员用户无法查看[!UICONTROL CMS Blocks]列表页的问题。

  以前，这些用户在安装以前的安全修补程序后由于缺少配置参数而遇到错误。<!-- AC-14087 -->

* **Cookie限制兼容性** — 解决涉及框架中`MAX_NUM_COOKIES`常量的向后不兼容的更改。 此更新将恢复预期行为，并确保与Cookie限制交互的扩展或自定义设置的兼容性。<!-- AC-14475 -->

* **异步操作** — 用于覆盖先前客户订单的异步操作受限。<!-- AC-13917 -->

* **修复了CVE-2025-47110** — 解决了电子邮件模板漏洞。<!-- AC-14695 -->

* **修复VULN-31547** — 解决类别规范链接漏洞。<!-- AC-14713 -->

>[!BEGINSHADEBOX]

CVE-2025-47110和VULN-31547的修补程序也作为独立修补程序提供。 有关详细信息，请参阅[知识库文章](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50)。

>[!ENDSHADEBOX]

<!-- Last updated from includes: 2026-04-08 15:01:38 -->
