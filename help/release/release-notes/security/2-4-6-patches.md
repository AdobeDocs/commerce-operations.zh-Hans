---
title: Adobe Commerce 2.4.6安全补丁发行说明
description: 了解Adobe Commerce版本2.4.6的安全修补程序版本中包含的安全错误修复、安全增强和其他安全相关更新。
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: 55bba84f05042667d0de3aa053e9a52119bd2599
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 0%

---


# Adobe Commerce 2.4.6安全修补程序的发行说明

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.6-p10

Adobe Commerce 2.4.6-p10安全版本为2.4.6早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-26](https://helpx.adobe.com/cn/security/products/magento/apsb25-26.html)。

{{b2b-patches}}

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.6-p9

Adobe Commerce 2.4.6-p9安全版本为2.4.6早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB25-08](https://helpx.adobe.com/cn/security/products/magento/apsb25-08.html)。

{{b2b-patches}}

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.6-p8

Adobe Commerce 2.4.6-p8安全版本为2.4.6早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-73](https://helpx.adobe.com/cn/security/products/magento/apsb24-73.html)。

{{b2b-patches}}

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### 此版本中包含的修补程序

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.6-p7

Adobe Commerce 2.4.6-p7安全版本为2.4.6早期版本中发现的漏洞修复了安全错误。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-61](https://helpx.adobe.com/cn/security/products/magento/apsb24-61.html)。

### 高亮

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### 此版本中包含的修补程序

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.6-p6

Adobe Commerce 2.4.6-p6安全版本为以前版本的2.4.6中发现的漏洞提供了安全错误修复。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-40](https://helpx.adobe.com/cn/security/products/magento/apsb24-40.html)。

为了与Commerce版本2.4.6-p6兼容，具有Adobe Commerce B2B扩展的商家必须升级到[B2B版本1.4.2-p1](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/b2b/release-notes#b2b-v142-p1)。

### 应用适用于CVE-2024-34102的修补程序

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

为了与Commerce版本2.4.6-p6兼容，具有Adobe Commerce B2B扩展的商家必须升级到[B2B版本1.4.2-p1](https://experienceleague.adobe.com/zh-hans/docs/commerce-admin/b2b/release-notes#b2b-v142-p1)。

### 高亮

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.6 - p5

Adobe Commerce 2.4.6-p5安全版本为以前版本的2.4.6中发现的漏洞提供了安全错误修复。

有关这些修复的最新信息，请参阅[Adobe安全公告APSB24-18](https://helpx.adobe.com/cn/security/products/magento/apsb24-18.html)。

## 2.4.6-p4

Adobe Commerce 2.4.6-p4安全版本为以前版本中发现的漏洞提供了安全错误修复。 此版本还包括可提高对最新安全最佳实践合规性的安全增强功能。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB24-03](https://helpx.adobe.com/cn/security/products/magento/apsb24-03.html)。

### 高亮

此版本引入了两项重要的安全增强功能：

* **更改未生成的缓存键的行为**：

   * 块的非生成缓存键现在包含与自动生成的键的前缀不同的前缀。 （未生成的缓存键是通过template指令语法或`setCacheKey`或`setData`方法设置的键。）
   * 块的非生成缓存键现在只能包含字母、数字、连字符(-)和下划线字符(_)。<!-- AC-9831 -->

* **自动生成的优惠券代码数量的限制**。 Commerce现在限制自动生成的优惠券代码数量。 默认最大值为250,000。 商家可以使用新的&#x200B;**[!UICONTROL Code Quantity Limit]**&#x200B;配置选项(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**)来控制此新限制。<!-- AC-8753 -->

## 2.4.6-p3

Adobe Commerce 2.4.6-p3安全版本为以前版本中发现的漏洞提供了安全错误修复。 此版本还包括安全增强功能，可提高对最新安全最佳实践的合规性。

有关安全修复的最新信息，请参阅[Adobe安全公告APSB23-50](https://helpx.adobe.com/cn/security/products/magento/apsb23-50.html)。

### 高亮

此版本引入了新的全页缓存配置设置，可帮助减轻与`{BASE-URL}/page_cache/block/esi HTTP`端点相关的风险。 此端点支持来自Commerce布局句柄和块结构的无限制、动态加载的内容片段。 新的&#x200B;**[!UICONTROL Handles Param]**&#x200B;配置设置设置此端点的`handles`参数的值，该值确定每个API允许的最大句柄数。 此属性的默认值为100。 商家可以从管理员(**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**&#x200B;更改此值。<!-- AC-9113 -->

### 此版本中包含的修补程序

Adobe Commerce 2.4.6-p3包含修补程序ACSD-51892修复的性能降级问题的解决方法。 此修补程序解决的问题不会影响商家，此问题在[ACSD-51892：配置文件加载多次的性能问题](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html?lang=zh-Hans)知识库文章中有所描述。

### 已知问题

**问题**： Adobe Commerce在Composer从`repo.magento.com`下载期间显示`wrong checksum`错误，包下载中断。 在下载预发行期间提供的发行包时可能会出现此问题，这是由于重新打包`magento/module-page-cache`包导致的。

**解决方法**：在下载过程中看到此错误的商家可以采取以下步骤：

1) 删除项目中的`/vendor`目录（如果存在）。
2) 运行`bin/magento composer update magento/module-page-cache`命令。 此命令仅更新`page cache`包。

如果校验和问题仍然存在，请先删除`composer.lock`文件，然后再重新运行`bin/magento composer update`命令以更新每个包。

## 2.4.6 - p2

Adobe Commerce 2.4.6-p2安全版本为以前版本中发现的漏洞提供了安全错误修复。 此版本还提供了安全增强功能，以改进对最新安全最佳实践的合规性。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB23-42](https://helpx.adobe.com/cn/security/products/magento/apsb23-42.html)。

### 应用适用于CVE-2022-31160的修补程序

`jQuery-UI`库版本1.13.1具有已知的安全漏洞(CVE-2022-31160)，该漏洞会影响Adobe Commerce和Magento Open Source的多个版本。 此库依赖于Adobe Commerce和Magento Open Source 2.4.4、2.4.5以及2.4.6。运行受影响部署的商户应应用针对2.4.4、2.4.5和2.4.6版本[&#128279;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=zh-Hans)知识库文章的jQuery UI安全漏洞CVE-2022-31160修复中指定的修补程序。

### 高亮

`nginx.sample`文件中的`fastcgi_pass`值已返回至其上一个（早于2.4.6-p1）值`fastcgi_backend`。 在Adobe Commerce 2.4.6-p1中，此值无意中更改为`php-fpm:9000`。

### 此版本中包含的修补程序

Adobe Commerce 2.4.6-p2包括对ACSD-51892补丁所解决的性能下降问题的解决方法。 此修补程序解决的问题不会影响商家，此问题在[ACSD-51892：配置文件加载多次的性能问题](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html?lang=zh-Hans)知识库文章中有所描述。

## 2.4.6-p1

Adobe Commerce 2.4.6-p1安全版本为以前版本中发现的漏洞提供了安全错误修复。 此版本还包括安全增强和平台升级，以改进对最新安全最佳实践的合规性。

有关安全错误修复的最新信息，请参阅[Adobe安全公告APSB23-35](https://helpx.adobe.com/cn/security/products/magento/apsb23-35.html)。

### 应用适用于CVE-2022-31160的修补程序

`jQuery-UI`库版本1.13.1具有已知的安全漏洞(CVE-2022-31160)，该漏洞会影响Adobe Commerce和Magento Open Source的多个版本。 此库依赖于Adobe Commerce和Magento Open Source 2.4.4、2.4.5以及2.4.6。运行受影响部署的商户应应用[查询UI安全漏洞CVE-2022-31160针对2.4.4、2.4.5和2.4.6版本](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=zh-Hans)知识库文章中指定的修补程序。

#### 突出显示

[`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL查询和([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) REST端点的默认行为已更改。 默认情况下，API现在始终返回`true`。 商家可以启用原始行为，如果数据库中不存在电子邮件，则返回`true`；如果存在，则返回`false`。<!-- AC-6695 -->

### 平台升级

此版本的平台升级可改善对最新安全最佳实践的合规性。

* **清漆缓存7.3支持**。 此版本与最新版本的Varnish Cache 7.3兼容。兼容性保持与6.0.x和7.2.x版本，但Adobe建议仅将Adobe Commerce 2.4.6-p1与Varnish Cache版本7.3或版本6.0 LTS一起使用。

* **RabbitMQ 3.11支持**。 此版本与最新版本的RabbitMQ 3.11兼容。兼容性仍与RabbitMQ 3.9兼容，该版本在2023年8月之前受支持，但Adobe建议仅将Adobe Commerce 2.4.6-p1与RabbitMQ 3.11一起使用。

* **JavaScript库**。 过时的JavaScript库已升级到最新的次要或修补程序版本，包括`moment.js`库(v2.29.4)、`jQuery UI`库(v1.13.2)和`jQuery`验证插件库(v1.19.5)。

### 已知问题

* `nginx.sample`文件无意中更新了更改，将`fastcgi_pass`的值从`fastcgi_backend`修改为`php-fpm:9000`。 可以安全地还原或忽略此更改。<!-- AC-8992 -->

* 在安装或将B2B扩展升级到1.4.0时，缺少B2B安全包的依赖项会导致以下安装错误。

  ```
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  通过为带有[稳定性标记](https://getcomposer.org/doc/04-schema.md#package-links)的B2B安全包添加手动依赖关系，可以解决此问题。 有关详细信息，请参阅[B2B发行说明](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html?lang=zh-Hans#known-issue)。
