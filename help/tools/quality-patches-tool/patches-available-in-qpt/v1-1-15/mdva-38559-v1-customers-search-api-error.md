---
title: 'MDVA-38559： /V1/customers/search API返回错误'
description: MDVA-38559修补程序修复了“/V1/customers/search”API向具有多个订阅的客户返回错误的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15后，即可使用此修补程序。 修补程序ID为MDVA-38559。 请注意，Adobe Commerce 2.4.3中已修复此问题。
feature: REST, Search
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# MDVA-38559： /V1/customers/search API返回错误

MDVA-38559修补程序修复了`/V1/customers/search` API为具有多个订阅的客户返回错误的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15后，即可使用此修补程序。 修补程序ID为MDVA-38559。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.1-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

`/V1/customers/search` API为具有多个订阅的客户返回错误。

<u>先决条件</u>：

Adobe Commerce商店使用多个网站。

<u>重现步骤</u>：

1. 前往&#x200B;**商店** > **配置** > **客户** > **客户配置** > **帐户共享选项**，然后选择&#x200B;**全局**。
1. 转到&#x200B;**客户** > **所有客户**，选择任意客户的&#x200B;**编辑**，然后选择&#x200B;**新闻稿**。
1. 订阅多个网站的新闻稿并保存客户。
1. 发送以下请求：

```REST API
V1/customers/search?searchCriteria[filterGroups][0][filters][0][field]=email&searchCriteria[filterGroups][0][filters][0][value]=test@example.com&searchCriteria[filterGroups][0][filters][0][conditionType]=eq
```

<u>预期的结果</u>：

将显示客户的搜索结果。

<u>实际结果</u>：

以下错误记录到exception.log中： *具有相同ID“1”的项目(Magento\Customer\Model\Customer\Interceptor)已存在。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
