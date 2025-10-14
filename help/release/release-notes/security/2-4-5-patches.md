---
title: Adobe Commerce 2.4.5安全修补程序发行说明
description: 了解Adobe Commerce版本2.4.5的安全修补程序版本中包含的安全错误修复、安全增强和其他安全相关更新。
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: c73eafcf52cf2ba0ea539bf61191db5fff952d7a
workflow-type: tm+mt
source-wordcount: '1482'
ht-degree: 0%

---


# Adobe Commerce 2.4.5安全修补程序的发行说明

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.5-p15

Adobe Commerce 2.4.5-p15安全版本为2.4.5早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html)。

{{b2b-patches}}

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

>[!NOTE]
>
>2.4.5的扩展支持安全修补程序仅向Adobe Commerce客户提供。 这些修补程序不适用于Magento Open Source代码库。 请参阅[扩展支持](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/release/planning/lifecycle-policy#extended-support)。


## 2.4.5-p14

Adobe Commerce 2.4.5-p14安全版本为2.4.5早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-71](https://helpx.adobe.com/cn/security/products/magento/apsb25-71.html)。

{{b2b-patches}}

## 2.4.5-p13

Adobe Commerce 2.4.5-p13安全版本为2.4.5早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-50](https://helpx.adobe.com/cn/security/products/magento/apsb25-50.html)。

{{b2b-patches}}

### 高亮

此版本包括以下功能亮点：

* **API性能增强** — 解决在上一个安全修补程序之后引入的批量异步Web API端点中的性能降级。<!-- AC-14078 -->

* **CMS阻止访问修复** — 解决具有受限权限（例如仅限促销访问）的管理员用户无法查看[!UICONTROL CMS Blocks]列表页的问题。

  以前，这些用户在安装以前的安全修补程序后由于缺少配置参数而遇到错误。<!-- AC-14087 -->

* **Cookie限制兼容性** — 解决涉及框架中`MAX_NUM_COOKIES`常量的向后不兼容的更改。 此更新将恢复预期行为，并确保与Cookie限制交互的扩展或自定义设置的兼容性。<!-- AC-14475 -->

* **异步操作** — 用于覆盖先前客户订单的异步操作受限。<!-- AC-13917 -->

## 2.4.5-p12

Adobe Commerce 2.4.5-p12安全版本为2.4.5早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-26](https://helpx.adobe.com/cn/security/products/magento/apsb25-26.html)。

{{b2b-patches}}

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.5-p11

Adobe Commerce 2.4.5-p11安全版本为2.4.5早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-08](https://helpx.adobe.com/cn/security/products/magento/apsb25-08.html)。

{{b2b-patches}}

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.5-p10

Adobe Commerce 2.4.5-p10安全版本为2.4.5早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-73](https://helpx.adobe.com/cn/security/products/magento/apsb24-73.html)。

{{b2b-patches}}

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### 此版本中包含的修补程序

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.5-p9

Adobe Commerce 2.4.5-p9安全版本为2.4.5早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-61](https://helpx.adobe.com/cn/security/products/magento/apsb24-61.html)。

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### 此版本中包含的修补程序

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.5-p8

Adobe Commerce 2.4.5-p8安全版本为以前版本的2.4.5中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-40](https://helpx.adobe.com/cn/security/products/magento/apsb24-40.html)。

### 应用适用于CVE-2024-34102的修补程序

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### 平台升级

* **MariaDB 10.5支持**。 此补丁发行版本引入了与MariaDB版本10.5的兼容性。Adobe Commerce仍与MariaDB版本10.4兼容，但Adobe建议仅在MariaDB版本10.5中使用Adobe Commerce 2.4.5-p8以及所有即将发布的仅用于安全性的2.4.5修补程序版本，因为MariaDB 10.4维护将于2024年6月18日结束。<!--AC-11530-->

### 高亮

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.5-p7

Adobe Commerce 2.4.5-p7安全版本为以前版本的2.4.5中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-18](https://helpx.adobe.com/cn/security/products/magento/apsb24-18.html)。

## 2.4.5-p6

Adobe Commerce 2.4.5-p6安全版本为以前版本的2.4.5中发现的漏洞提供了安全错误修复。此版本还包括安全增强功能，可提高对最新安全最佳实践的合规性。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-03](https://helpx.adobe.com/cn/security/products/magento/apsb24-03.html)。

### 高亮

此版本引入了两项重要的安全增强功能：

* **更改未生成的缓存键的行为**：

   * 块的非生成缓存键现在包含与自动生成的键的前缀不同的前缀。 （未生成的缓存键是通过template指令语法或`setCacheKey`或`setData`方法设置的键。）
   * 块的非生成缓存键现在只能包含字母、数字、连字符(-)和下划线字符(_)。<!-- AC-9831 -->

* **自动生成的优惠券代码数量的限制**。 Commerce现在限制自动生成的优惠券代码数量。 默认最大值为250,000。 商家可以使用新的&#x200B;**[!UICONTROL Code Quantity Limit]**&#x200B;配置选项(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)来控制此新限制。<!-- AC-8753 -->

## 2.4.5-p5

Adobe Commerce 2.4.5-p5安全版本为以前版本的2.4.5中发现的漏洞提供了安全错误修复。此版本还包括安全增强功能，可提高对最新安全最佳实践的合规性。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB23-50](https://helpx.adobe.com/cn/security/products/magento/apsb23-50.html)。

### 高亮

此版本引入了新的全页缓存配置设置，可帮助减轻与`{BASE-URL}/page_cache/block/esi HTTP`端点相关的风险。 此端点支持来自Commerce布局句柄和块结构的无限制、动态加载的内容片段。 新的&#x200B;**[!UICONTROL Handles Param]**&#x200B;配置设置设置此端点的`handles`参数的值，该值确定每个API允许的最大句柄数。 此属性的默认值为100。 商家可以从管理员(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**)更改此值。<!-- AC-9113 -->

### 已知问题

**问题**： Adobe Commerce在Composer从&#x200B;**下载期间显示**&#x200B;错误校验和`repo.magento.com`错误，包下载被中断。 在下载预发行期间提供的发行版包时，可能会出现此问题，这是由于重新打包`magento/module-page-cache`包导致的。

**解决方法**：在下载过程中看到此错误的商家可以采取以下步骤：

1) 删除项目中的`/vendor`目录（如果存在）。
2) 运行`bin/magento composer update magento/module-page-cache`命令。 此命令仅更新`page cache`包。

如果校验和问题仍然存在，请先删除`composer.lock`文件，然后再重新运行`bin/magento composer update`命令以更新每个包。

## 2.4.5-p4

Adobe Commerce 2.4.5-p4安全版本为以前版本的2.4.5中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB23-42](https://helpx.adobe.com/cn/security/products/magento/apsb23-42.html)。

### 应用适用于CVE-2022-31160的修补程序

`jQuery-UI`库版本1.13.1具有已知的安全漏洞(CVE-2022-31160)，该漏洞会影响Adobe Commerce和Magento Open Source的多个版本。 此库依赖于Adobe Commerce和Magento Open Source 2.4.4、2.4.5以及2.4.6。运行受影响部署的商户应应用针对2.4.4、2.4.5和2.4.6版本[知识库文章的](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2-4-4-2-4-5-2-4-6)jQuery UI安全漏洞CVE-2022-31160修复中指定的修补程序。

## 2.4.5-p3

Adobe Commerce 2.4.5-p3安全版本为以前版本的2.4.5中发现的漏洞提供了安全修复。此版本还包括可提高对最新安全最佳实践合规性的安全增强功能。

有关安全错误修复的最新信息，请参阅[Adobe安全公告](https://helpx.adobe.com/cn/security/products/magento/apsb23-35.html)。

### 应用适用于CVE-2022-31160的修补程序

`jQuery-UI`库版本1.13.1具有已知的安全漏洞(CVE-2022-31160)，该漏洞会影响Adobe Commerce和Magento Open Source的多个版本。 此库依赖于Adobe Commerce和Magento Open Source 2.4.4、2.4.5以及2.4.6。运行受影响部署的商户应应用[查询UI安全漏洞CVE-2022-31160针对2.4.4、2.4.5和2.4.6版本](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2-4-4-2-4-5-2-4-6)知识库文章中指定的修补程序。

### 高亮

[`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL查询和([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST端点的默认行为已更改。 默认情况下，API现在始终返回`true`。 商家可以启用原始行为，如果数据库中不存在电子邮件，则返回`true`；如果存在，则返回`false`。<!-- AC-6695 -->

### 平台升级

此版本的平台升级可改善对最新安全最佳实践的合规性。

* **清漆缓存7.3支持**。 此版本与最新版本的Varnish Cache 7.3兼容。与6.0.x和7.2.x版本的兼容性保持不变，但我们建议仅将Adobe Commerce 2.4.5-p3与Varnish Cache版本7.3或版本6.0 LTS一起使用。

* **RabbitMQ 3.11支持**。 此版本与最新版本的RabbitMQ 3.11兼容。与RabbitMQ 3.9的兼容性仍然存在，该版本在2023年8月之前受支持，但我们建议仅将Adobe Commerce 2.4.5-p3与RabbitMQ 3.11一起使用。

* **JavaScript库**。 过时的JavaScript库已升级到最新的次要或修补程序版本，包括`moment.js`库(v2.29.4)、`jQuery UI`库(v1.13.2)和`jQuery`验证插件库(v1.19.5)。

## 2.4.5 - p2

Adobe Commerce 2.4.5-p2安全版本为以前版本的2.4.5中发现的漏洞提供了三个安全修复。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB23-17](https://helpx.adobe.com/cn/security/products/magento/apsb23-17.html)。

## 2.4.5-p1

Adobe Commerce 2.4.5-p1安全版本为以前版本的2.4.5中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB22-48](https://helpx.adobe.com/cn/security/products/magento/apsb22-48.html)。

其中一项安全错误修复包括创建新的配置设置。 如果电子邮件已更改，[!UICONTROL **需要电子邮件确认**]&#x200B;配置设置允许管理员用户在更改其电子邮件地址时要求电子邮件确认。<!-- AC-6292-->

<!-- Last updated from includes: 2025-10-06 13:12:34 -->
