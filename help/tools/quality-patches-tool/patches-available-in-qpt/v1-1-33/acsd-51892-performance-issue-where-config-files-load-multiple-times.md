---
title: 'ACSD-51892：配置文件加载多次出现的性能问题'
description: 应用ACSD-51892修补程序以修复在部署期间多次加载配置文件的Adobe Commerce性能问题。
feature: Observability
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-51892：配置文件加载多次出现的性能问题

ACSD-51892修补程序修复了每次在单个请求中访问部署配置值时加载`app/etc/env.php`和`app/etc/config.php`文件所引起的性能问题。 文件读取过多给系统带来压力，导致整体性能下降。 安装[!DNL Quality Patches Tool (QPT)] 1.1.33时，此修补程序可用。 修补程序ID为ACSD-51892。 请注意，Adobe Commerce 2.4.6-p2中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

存在配置文件加载多次的性能问题。

<u>重现步骤</u>：

1. 执行部署或升级到Adobe Commerce 2.4.6或更高版本。
1. 在部署运行时检查文件系统日志以访问`app/etc/env.php`和`app/etc/config.php`文件。

<u>预期的结果</u>：

在常规时间范围内部署成功。

<u>实际结果</u>：

* 服务器正在努力响应您输入的任何命令。 访问网站时导致&#x200B;*错误503第一字节超时*。
* 日志文件中有多个条目可访问`app/etc/env.php`和`app/etc/config.php`文件。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
