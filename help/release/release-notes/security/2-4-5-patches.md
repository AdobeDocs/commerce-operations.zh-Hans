---
title: Adobe Commerce 2.4.5安全修补程序发行说明
description: 了解Adobe Commerce版本2.4.5的安全修补程序版本中包含的安全错误修复、安全增强和其他安全相关更新。
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: 7705e750a466ab134ae2616a40a32880ee0c45de
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 0%

---


# Adobe Commerce 2.4.5安全修补程序的发行说明

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.5-p8

Adobe Commerce 2.4.5-p7安全版本为以前版本的2.4.5中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### 平台升级

* **MariaDB 10.5支持**. 此补丁发行版本引入了与MariaDB版本10.5的兼容性。Adobe Commerce仍与MariaDB版本10.4兼容，但Adobe建议仅在MariaDB版本10.5中使用Adobe Commerce 2.4.5-p8以及所有即将发布的仅支持2.4.5安全的修补程序版本，因为MariaDB 10.4的维护将于2024年6月18日结束。 <!--AC-11530-->

## Adobe Commerce 2.4.5-p7

Adobe Commerce 2.4.5-p7安全版本为以前版本中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.5-p6

Adobe Commerce 2.4.5-p6安全版本为以前版本中发现的漏洞提供了安全错误修复。 此版本还包括安全增强功能，可提高对最新安全最佳实践的合规性。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### 安全性亮点

此版本引入了两项重要的安全增强功能：

* **更改了未生成的缓存键的行为**：

   * 块的非生成缓存键现在包含与自动生成的键的前缀不同的前缀。 (未生成缓存键是通过template指令语法或 `setCacheKey` 或 `setData` 方法。)
   * 块的非生成缓存键现在只能包含字母、数字、连字符(-)和下划线字符(_)。  <!-- AC-9831 -->

* **对自动生成优惠券代码数量的限制**. Commerce现在限制自动生成的优惠券代码数量。 默认最大值为250,000。 商家可以使用新的 **[!UICONTROL Code Quantity Limit]** 配置选项(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)，以控制此新限制。 <!-- AC-8753 -->



## Adobe Commerce 2.4.5-p5

Adobe Commerce 2.4.5-p5安全版本为以前版本中发现的漏洞提供了安全错误修复。 此版本还包括安全增强功能，可提高对最新安全最佳实践的合规性。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### 安全性突出显示

此版本引入了新的全页缓存配置设置，可帮助降低与相关的风险。 `{BASE-URL}/page_cache/block/esi HTTP` 端点。 此端点支持来自Commerce布局句柄和块结构的无限制、动态加载的内容片段。 新 **[!UICONTROL Handles Param]** 配置设置设置此端点的值 `handles` 参数，用于确定每个API允许的最大句柄数。 此属性的默认值为100。 商家可以从管理员(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**)。 <!-- AC-9113 -->

### 已知问题

**问题**：Adobe Commerce显示 **校验和错误** 编辑器从下载时出错 `repo.magento.com`，并且包下载中断。 在下载预发行期间提供的发行版软件包时可能会出现此问题，此问题是由重新打包的 `magento/module-page-cache` 包。

**解决方法**：在下载过程中看到此错误的商家可以采取以下步骤：

1) 删除 `/vendor` 目录（如果存在）。
2) 运行 `bin/magento composer update magento/module-page-cache` 命令。 此命令仅更新 `page cache` 包。

如果校验和问题仍然存在，请删除 `composer.lock` 文件，然后再重新运行 `bin/magento composer update` 命令以更新每个包。

## Adobe Commerce 2.4.5-p4

Adobe Commerce 2.4.5-p4安全版本为以前版本中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### 应用补丁以解决jQuery-UI库中的安全漏洞CVE-2022-31160

`jQuery-UI` 库版本1.13.1具有已知的安全漏洞(CVE-2022-31160)，该漏洞会影响Adobe Commerce和Magento Open Source的多个版本。 此库依赖于Adobe Commerce和Magento Open Source2.4.4、2.4.5和2.4.6。运行受影响部署的商户应应用 [针对2.4.4、2.4.5和2.4.6版的jQuery UI安全漏洞CVE-2022-31160修复](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) 知识库文章。

## Adobe Commerce 2.4.5 - p3

Adobe Commerce 2.4.5-p3安全版本为以前版本中发现的漏洞提供了安全修复。 此版本还包括可提高对最新安全最佳实践合规性的安全增强功能。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### 应用补丁以解决jQuery-UI库中的安全漏洞CVE-2022-31160

`jQuery-UI` 库版本1.13.1具有已知的安全漏洞(CVE-2022-31160)，该漏洞会影响Adobe Commerce和Magento Open Source的多个版本。 此库依赖于Adobe Commerce和Magento Open Source2.4.4、2.4.5和2.4.6。运行受影响部署的商户应应用 [针对2.4.4、2.4.5和2.4.6版本的查询UI安全漏洞CVE-2022-31160修复](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) 知识库文章。

### 安全性突出显示

的默认行为 [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL查询和([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST端点已更改。 默认情况下，API现在始终返回 `true`. 商人们可以启用原始行为，即 `true` 如果电子邮件在数据库中不存在，并且 `false` 如果它存在。 <!-- AC-6695 -->

### 平台升级

此版本的平台升级可改善对最新安全最佳实践的合规性。

* **支持Varnish缓存7.3**. 此版本与最新版本的Varnish Cache 7.3兼容。与6.0.x和7.2.x版本的兼容性保持不变，但我们建议仅将Adobe Commerce 2.4.5-p3与Varnish Cache版本7.3或版本6.0 LTS一起使用。

* **RabbitMQ 3.11支持**. 此版本与最新版本的RabbitMQ 3.11兼容。兼容性保持与RabbitMQ 3.9的兼容，该版本在2023年8月之前受支持，但我们建议仅将Adobe Commerce 2.4.5-p3与RabbitMQ 3.11一起使用。

* **JavaScript库**. 过时的JavaScript库已升级到最新的次要版本或修补程序版本，包括 `moment.js` 库(v2.29.4)， `jQuery UI` 库(v1.13.2)，和 `jQuery` 验证插件库(v1.19.5)。

## Adobe Commerce 2.4.5-p2发行说明

Adobe Commerce 2.4.5-p2安全版本为以前版本中发现的漏洞提供了三个安全修复。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## Adobe Commerce 2.4.5-p1

Adobe Commerce 2.4.5-p1安全版本为先前版本(Adobe Commerce 2.4.5和Magento Open Source2.4.5)中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅 [Adobe安全公告APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

其中一项安全错误修复包括创建新的配置设置。 此 **电子邮件更改后需要电子邮件确认** 通过配置设置，管理员可在管理员用户更改其电子邮件地址时要求确认电子邮件。 <!-- AC-6292-->
