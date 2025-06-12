---
title: MDVA-37725：通过非默认站点发送的电子邮件包含默认站点的徽标URL
description: MDVA-37725修补程序修复了以下问题：通过包含默认网站的徽标URL的非默认网站发送异步订单电子邮件。
feature: Communications, Orders
role: Admin
exl-id: 6e72897c-7652-4b5a-8575-090e94188daf
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-37725：通过非默认站点发送的电子邮件包含默认站点的徽标URL

>[!WARNING]
>
> 已弃用MDVA-37725修补程序。

MDVA-37725修补程序修复了以下问题：通过包含默认网站的徽标URL的非默认网站发送异步订单电子邮件。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4时，此修补程序可用。 修补程序ID为MDVA-37725。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.0 - 2.4.3

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

异步订单电子邮件通过包含默认网站徽标URL的非默认网站发送。

<u>先决条件</u>：

1. 必须已创建第二个网站/商店/商店视图。
1. 必须从&#x200B;**商店** > **设置** > **配置** > **销售** > **销售电子邮件** > **常规设置**&#x200B;启用&#x200B;**异步发送**&#x200B;配置。
1. **已打开将商店代码添加到URL**&#x200B;配置，以便从&#x200B;**商店** > **设置** > **配置** > **URL选项**&#x200B;访问辅助网站。

<u>重现步骤</u>：

1. 从第一家和第二家商店下订单。
1. 运行cron以发送销售电子邮件。
1. 检查来自第二个网站的电子邮件。

<u>预期的结果</u>：

电子邮件的徽标URL包含第二个网站的URL。

<u>实际结果</u>：

电子邮件的徽标URL包含默认网站的URL。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅QPT[&#128279;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)中可用的修补程序部分。
