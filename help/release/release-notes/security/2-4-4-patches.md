---
title: Adobe Commerce 2.4.4安全修补程序发行说明
description: 了解Adobe Commerce版本2.4.4的安全修补程序版本中包含的安全错误修复、安全增强和其他安全相关更新。
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: 770986607b550d876a7afdf371a340ebae11eb99
workflow-type: tm+mt
source-wordcount: '1805'
ht-degree: 0%

---


# Adobe Commerce 2.4.4安全修补程序的发行说明

{{$include /help/_includes/release-notes/security-patch-intro.md}}

>[!NOTE]
>
>2.4.4的扩展支持安全修补程序仅向Adobe Commerce客户提供。 这些修补程序不适用于Magento Open Source代码库。 请参阅[扩展支持](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy#extended-support)。

## 2.4.4-p15

Adobe Commerce 2.4.4-p15是一个扩展支持安全版本，为以前版本的2.4.4中标识的漏洞提供了安全错误修复。它仅适用于Adobe Commerce客户。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html)。

{{b2b-patches}}

## 2.4.4-p14

Adobe Commerce 2.4.4-p14是一个扩展支持安全版本，为以前版本的2.4.4中标识的漏洞提供了安全错误修复。它仅适用于Adobe Commerce客户。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html)。

{{b2b-patches}}

### 高亮

此版本包括以下功能亮点：

* **API性能增强** — 解决在上一个安全修补程序之后引入的批量异步Web API端点中的性能降级。<!-- AC-14078 -->

* **CMS阻止访问修复** — 解决具有受限权限（例如仅限促销访问）的管理员用户无法查看[!UICONTROL CMS Blocks]列表页的问题。

  以前，这些用户在安装以前的安全修补程序后由于缺少配置参数而遇到错误。<!-- AC-14087 -->

* **Cookie限制兼容性** — 解决涉及框架中`MAX_NUM_COOKIES`常量的向后不兼容的更改。 此更新将恢复预期行为，并确保与Cookie限制交互的扩展或自定义设置的兼容性。<!-- AC-14475 -->

* **异步操作** — 用于覆盖先前客户订单的异步操作受限。<!-- AC-13917 -->

## 2.4.4-p13

Adobe Commerce 2.4.4-p13安全版本为2.4.4以前版本中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html)。

{{b2b-patches}}

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.4-p12

Adobe Commerce 2.4.4-p12安全版本为2.4.4以前版本中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html)。

{{b2b-patches}}

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.4-p11

Adobe Commerce 2.4.4-p11安全版本为2.4.4以前版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html)。

{{b2b-patches}}

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

## 2.4.4-p10

Adobe Commerce 2.4.4-p10安全版本为2.4.4以前版本中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html)。

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### 此版本中包含的修补程序

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.4 - p9

Adobe Commerce 2.4.4-p9安全版本为以前版本的2.4.4中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html)。

### 应用适用于CVE-2024-34102的修补程序

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### 平台升级

* **MariaDB 10.5支持**。 此补丁发行版本引入了与MariaDB版本10.5的兼容性。Adobe Commerce仍与MariaDB版本10.4兼容，但Adobe建议仅在MariaDB版本10.5中使用Adobe Commerce 2.4.4-p9以及所有即将发布的仅用于安全性的2.4.4修补程序版本，因为MariaDB 10.4的维护将于2024年6月18日结束。<!--AC-11530-->

### 高亮

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.4-p8

Adobe Commerce 2.4.4-p8安全版本为Adobe Commerce 2.4.4部署提供了安全错误修复。 这些更新修复了以前版本中发现的漏洞。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html)。

## 2.4.4-p7

Adobe Commerce 2.4.4-p7安全版本为以前版本中发现的漏洞提供了安全错误修复。 此版本还包括可提高对最新安全最佳实践合规性的安全增强功能。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html)。

### 高亮

此版本引入了两项重要的安全增强功能：

* **更改未生成的缓存键的行为**：

   * 块的非生成缓存键现在包含与自动生成的键的前缀不同的前缀。 （未生成的缓存键是通过template指令语法或`setCacheKey`或`setData`方法设置的键。）
   * 块的非生成缓存键现在只能包含字母、数字、连字符(-)和下划线字符(_)。<!-- AC-9831 -->

* **自动生成的优惠券代码数量的限制**。 Commerce现在限制自动生成的优惠券代码数量。 默认最大值为250,000。 商家可以使用新的&#x200B;**[!UICONTROL Code Quantity Limit]**&#x200B;配置选项(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)来控制此新限制。<!-- AC-8753 -->

## 2.4.4-p6

Adobe Commerce 2.4.4-p6安全版本为以前版本中发现的漏洞提供了安全错误修复。 此版本还包括可提高对最新安全最佳实践合规性的安全增强功能。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html)。

此版本还包括可提高对最新安全最佳实践合规性的安全增强功能。

### 高亮

此版本引入了新的全页缓存配置设置，可帮助减轻与`{BASE-URL}/page_cache/block/esi HTTP`端点相关的风险。 此端点支持来自Commerce布局句柄和块结构的无限制、动态加载的内容片段。 新的&#x200B;**[!UICONTROL Handles Param]**&#x200B;配置设置设置此端点的`handles`参数的值，该值确定每个API允许的最大句柄数。 此属性的默认值为100。 商家可以从管理员(**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**)更改此值。<!-- AC-9113 -->

### 已知问题

**问题**： Adobe Commerce在Composer从&#x200B;**下载期间显示**&#x200B;错误校验和`repo.magento.com`错误，包下载被中断。 在下载预发行期间提供的发行版包时，可能会出现此问题，这是由于重新打包`magento/module-page-cache`包导致的。

**解决方法**：在下载过程中看到此错误的商家可以采取以下步骤：

1) 删除项目中的`/vendor`目录（如果存在）。
2) 运行`bin/magento composer update magento/module-page-cache`命令。 此命令仅更新`page cache`包。

如果校验和问题仍然存在，请先删除`composer.lock`文件，然后再重新运行`bin/magento composer update`命令以更新每个包。

## 2.4.4 - p5

Adobe Commerce 2.4.4-p5安全版本为以前版本中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html)。

### 应用适用于CVE-2022-31160的修补程序

`jQuery-UI`库版本1.13.1具有已知的安全漏洞(CVE-2022-31160)，该漏洞会影响Adobe Commerce和Magento Open Source的多个版本。 此库依赖于Adobe Commerce和Magento Open Source 2.4.4、2.4.5以及2.4.6。运行受影响部署的商户应应用针对2.4.4、2.4.5和2.4.6版本[知识库文章的](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html)jQuery UI安全漏洞CVE-2022-31160修复中指定的修补程序。

## 2.4.4-p4

Adobe Commerce 2.4.4-p4安全版本为以前版本中发现的漏洞提供了安全错误修复。 此版本还包括安全增强和平台升级，以改进对最新安全最佳实践的合规性。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html)。

### 应用适用于CVE-2022-31160的修补程序

`jQuery-UI`库版本1.13.1具有已知的安全漏洞(CVE-2022-31160)，该漏洞会影响Adobe Commerce和Magento Open Source的多个版本。 此库依赖于Adobe Commerce和Magento Open Source 2.4.4、2.4.5以及2.4.6。运行受影响部署的商户应应用针对2.4.4、2.4.5和2.4.6版本[知识库文章的](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html)jQuery UI安全漏洞CVE-2022-31160修复中指定的修补程序。

### 高亮

[`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL查询和([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST端点的默认行为已更改。 默认情况下，API现在始终返回`true`。 商家可以启用原始行为，如果数据库中不存在电子邮件，则返回`true`；如果存在，则返回`false`。<!-- AC-6695 -->

### 平台升级

此版本的平台升级可改善对最新安全最佳实践的合规性。

* **清漆缓存7.3支持**。 此版本与最新版本的Varnish Cache 7.3兼容。兼容性保持与6.0.x和7u.2.x版本，但Adobe建议仅将Adobe Commerce 2.4.4-p4与Varnish Cache版本7.3或版本6.0 LTS一起使用。

* **RabbitMQ 3.11支持**。 此版本与最新版本的RabbitMQ 3.11兼容。与RabbitMQ 3.9的兼容性仍然存在，该版本在2023年8月之前受支持，但Adobe建议仅将Adobe Commerce 2.4.4-p4与RabbitMQ 3.11一起使用。

* **JavaScript库**。 过时的JavaScript库已升级到最新的次要或修补程序版本，包括`moment.js`库(v2.29.4)、`jQuery UI`库(v1.13.2)和`jQuery`验证插件库(v1.19.5)。

## 2.4.4 - p3

Adobe Commerce 2.4.4-p3安全版本为以前版本中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html)。

## 2.4.4 - p2

Adobe Commerce 2.4.4-p2安全版本修复了以前版本中发现的漏洞。 一种修复包括创建新的配置设置。 如果电子邮件已更改，[!UICONTROL **需要电子邮件确认**]&#x200B;配置设置允许管理员用户在更改其电子邮件地址时要求电子邮件确认。<!-- AC-6292-->

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html)。

### 应用AC-3022.patch以继续将DHL作为运输运营商

DHL已引入架构版本6.2，并且将在不久的将来弃用架构版本6.0。 支持DHL集成的Adobe Commerce 2.4.4及更早版本仅支持版本6.0。部署这些版本的商家应尽早应用`AC-3022.patch`，以继续将DHL作为装运承运人提供。 有关下载和安装修补程序的信息，请参阅[应用修补程序以继续将DHL作为发运运营商提供](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481)知识库文章。

## 2.4.4-p1

Adobe Commerce 2.4.4-p1安全版本修复了以前版本中发现的漏洞。 此版本还包括安全增强功能，可提高对最新安全最佳实践的合规性。

有关安全错误修复的最新信息，请参阅[Adobe安全公告](https://helpx.adobe.com/security/products/magento/apsb22-38.html)。t

### 应用`AC-3022.patch`以继续将DHL作为装运承运人提供

DHL已引入架构版本6.2，并且将在不久的将来弃用架构版本6.0。 支持DHL集成的Adobe Commerce 2.4.4及更早版本仅支持版本6.0。部署这些版本的商家应尽早应用`AC-3022.patch`，以继续将DHL作为装运承运人提供。 有关下载和安装修补程序的信息，请参阅[应用修补程序以继续将DHL作为发运运营商提供](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier)知识库文章。

### 高亮

此版本的安全改进改进了与最新安全最佳实践的符合性，包括：

* ACL资源已添加到清单。
* 增强了清单模板的安全性。

### 已知问题

**问题**：在2.4.4-p1包上运行时，Web API和集成测试显示此错误： `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`。 **解决方法**：通过运行`require monolog/monolog:2.6.0`命令安装早期版本的Monolog。<!-- AC-3651-->

**问题**：商家在从Adobe Commerce 2.4.4升级到Adobe Commerce 2.4.4-p1的过程中可能会注意到包版本降级通知。 可以忽略这些消息。 包版本中的差异是由于包生成期间出现异常造成的。 没有产品功能受到影响。 有关受影响的方案和变通方法的讨论，请参阅从2.4.4升级到2.4.4-p1[知识库文章后降级的](https://support.magento.com/hc/en-us/articles/8214752983949)包。

<!-- Last updated from includes: 2025-07-24 10:48:00 -->
