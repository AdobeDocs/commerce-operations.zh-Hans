---
title: Adobe Commerce 2.4.4安全修补程序的发行说明
description: 了解Adobe Commerce版本2.4.4的安全修补程序版本中包含的安全错误修复、安全增强和其他安全相关更新。
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: 59a5306c8329ddc3ca2a2e086f5ebe81b49eab3a
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 0%

---


# Adobe Commerce 2.4.4安全修补程序的发行说明

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.4-p9

Adobe Commerce 2.4.4-p9安全版本为以前版本的2.4.4中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### 平台升级

* **MariaDB 10.5支持**. 此补丁发行版本引入了与MariaDB版本10.5的兼容性。Adobe Commerce仍与MariaDB版本10.4兼容，但Adobe建议仅在MariaDB版本10.5中使用Adobe Commerce 2.4.4-p9以及所有即将发布的仅支持2.4.4安全的修补程序版本，因为MariaDB 10.4的维护将于2024年6月18日结束。 <!--AC-11530-->

### 其他安全增强功能

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## 2.4.4-p8

Adobe Commerce 2.4.4-p8安全版本为Adobe Commerce 2.4.4部署提供了安全错误修复。 这些更新修复了以前版本中发现的漏洞。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.4-p7

Adobe Commerce 2.4.4-p7安全版本为以前版本中发现的漏洞提供了安全错误修复。 此版本还包括可提高对最新安全最佳实践合规性的安全增强功能。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### 安全性亮点

此版本引入了两项重要的安全增强功能：

* **更改了未生成的缓存键的行为**：

   * 块的非生成缓存键现在包含与自动生成的键的前缀不同的前缀。 (未生成缓存键是通过template指令语法或 `setCacheKey` 或 `setData` 方法。)
   * 块的非生成缓存键现在只能包含字母、数字、连字符(-)和下划线字符(_)。 <!-- AC-9831 -->

* **对自动生成优惠券代码数量的限制**. Commerce现在限制自动生成的优惠券代码数量。 默认最大值为250,000。 商家可以使用新的 **[!UICONTROL Code Quantity Limit]** 配置选项(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)，以控制此新限制。 <!-- AC-8753 -->

## 2.4.4-p6

Adobe Commerce 2.4.4-p6安全版本为以前版本中发现的漏洞提供了安全错误修复。 此版本还包括可提高对最新安全最佳实践合规性的安全增强功能。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

此版本还包括可提高对最新安全最佳实践合规性的安全增强功能。

### 安全性突出显示

此版本引入了新的全页缓存配置设置，可帮助降低与相关的风险。 `{BASE-URL}/page_cache/block/esi HTTP` 端点。 此端点支持来自Commerce布局句柄和块结构的无限制、动态加载的内容片段。 新 **[!UICONTROL Handles Param]** 配置设置设置此端点的值 `handles` 参数，用于确定每个API允许的最大句柄数。 此属性的默认值为100。 商家可以从管理员(**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**)。 <!-- AC-9113 -->

### 已知问题

**问题**：Adobe Commerce显示 **校验和错误** 编辑器从下载时出错 `repo.magento.com`，并且包下载中断。 在下载预发行期间提供的发行版软件包时可能会出现此问题，此问题是由重新打包的 `magento/module-page-cache` 包。

**解决方法**：在下载过程中看到此错误的商家可以采取以下步骤：

1) 删除 `/vendor` 目录（如果存在）。
2) 运行 `bin/magento composer update magento/module-page-cache` 命令。 此命令仅更新 `page cache` 包。

如果校验和问题仍然存在，请删除 `composer.lock` 文件，然后再重新运行 `bin/magento composer update` 命令以更新每个包。

## 2.4.4 - p5

Adobe Commerce 2.4.4-p5安全版本为以前版本中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### 应用补丁以解决jQuery-UI库中的安全漏洞CVE-2022-31160

`jQuery-UI` 库版本1.13.1具有已知的安全漏洞(CVE-2022-31160)，该漏洞会影响Adobe Commerce和Magento Open Source的多个版本。 此库依赖于Adobe Commerce和Magento Open Source2.4.4、2.4.5和2.4.6。运行受影响部署的商户应应用 [针对2.4.4、2.4.5和2.4.6版的jQuery UI安全漏洞CVE-2022-31160修复](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) 知识库文章。

## 2.4.4-p4

Adobe Commerce 2.4.4-p4安全版本为以前版本中发现的漏洞提供了安全错误修复。 此版本还包括安全增强和平台升级，以改进对最新安全最佳实践的合规性。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### 应用补丁以解决jQuery-UI库中的安全漏洞CVE-2022-31160

`jQuery-UI` 库版本1.13.1具有已知的安全漏洞(CVE-2022-31160)，该漏洞会影响Adobe Commerce和Magento Open Source的多个版本。 此库依赖于Adobe Commerce和Magento Open Source2.4.4、2.4.5和2.4.6。运行受影响部署的商户应应用 [针对2.4.4、2.4.5和2.4.6版的jQuery UI安全漏洞CVE-2022-31160修复](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) 知识库文章。

### 安全性突出显示

的默认行为 [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL查询和([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST端点已更改。 默认情况下，API现在始终返回 `true`. 商人们可以启用原始行为，即 `true` 如果电子邮件在数据库中不存在，并且 `false` 如果它存在。 <!-- AC-6695 -->

### 平台升级

此版本的平台升级可改善对最新安全最佳实践的合规性。

* **支持Varnish缓存7.3**. 此版本与最新版本的Varnish Cache 7.3兼容。与6.0.x和7u.2.x版本的兼容性保持不变，但Adobe建议仅将Adobe Commerce 2.4.4-p4与Varnish Cache版本7.3或版本6.0 LTS一起使用。

* **RabbitMQ 3.11支持**. 此版本与最新版本的RabbitMQ 3.11兼容。兼容性保持与RabbitMQ 3.9的兼容，该版本在2023年8月之前受支持，但Adobe建议仅将Adobe Commerce 2.4.4-p4与RabbitMQ 3.11一起使用。

* **JavaScript库**. 过时的JavaScript库已升级到最新的次要版本或修补程序版本，包括 `moment.js` 库(v2.29.4)， `jQuery UI` 库(v1.13.2)，和 `jQuery` 验证插件库(v1.19.5)。

## 2.4.4 - p3

Adobe Commerce 2.4.4-p3安全版本为以前版本中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## 2.4.4 - p2

Adobe Commerce 2.4.4-p2安全版本修复了以前版本中发现的漏洞。 一种修复包括创建新的配置设置。 此 **电子邮件更改后需要电子邮件确认** 配置设置允许管理员用户在更改其电子邮件地址时要求确认电子邮件。 <!-- AC-6292-->

有关安全错误修复的最新信息，请参阅 [Adobe安全公告APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

### 应用AC-3022.patch以继续将DHL作为运输运营商

DHL已引入架构版本6.2，并且将在不久的将来弃用架构版本6.0。 支持DHL集成的Adobe Commerce 2.4.4及更早版本仅支持版本6.0。部署这些版本的商家应适用 `AC-3022.patch` 尽早继续提供DHL作为航运公司。 请参阅 [应用修补程序以继续将DHL作为运输运营商](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481) 知识库文章，了解有关下载和安装修补程序的信息。

## 2.4.4-p1

Adobe Commerce 2.4.4-p1安全版本修复了以前版本中发现的漏洞。 此版本还包括安全增强功能，可提高对最新安全最佳实践的合规性。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告](https://helpx.adobe.com/security/products/magento/apsb22-38.html).t

### 应用 `AC-3022.patch` 继续提供DHL作为运输承运商

DHL已引入架构版本6.2，并且将在不久的将来弃用架构版本6.0。 支持DHL集成的Adobe Commerce 2.4.4及更早版本仅支持版本6.0。部署这些版本的商家应适用 `AC-3022.patch` 尽早继续提供DHL作为航运公司。 请参阅 [应用修补程序以继续将DHL作为运输运营商](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) 知识库文章，了解有关下载和安装修补程序的信息。

### 安全性亮点

此版本的安全改进改进了与最新安全最佳实践的符合性，包括：

* ACL资源已添加到清单。
* 增强了清单模板的安全性。

### 已知问题

**问题**：在2.4.4-p1包上运行时，Web API和集成测试会显示此错误： `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **解决方法**：通过运行 `require monolog/monolog:2.6.0` 命令。 <!-- AC-3651-->

**问题**：商家在从Adobe Commerce 2.4.4升级到Adobe Commerce 2.4.4-p1的过程中可能会注意到包版本降级通知。 可以忽略这些消息。 包版本中的差异是由于包生成期间出现异常造成的。 没有产品功能受到影响。 请参阅 [从2.4.4升级到2.4.4后，将包降级 — p1](https://support.magento.com/hc/en-us/articles/8214752983949) 知识库文章，用于讨论受影响的情景和解决方法。
