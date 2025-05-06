---
title: MDVA-44660：不能将重音符号用于客户名称
description: The MDVA-44660 patch fixes the issue where the grave accent character cannot be used for a customer's name. This patch is available when the [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 is installed. The patch ID is MDVA-44660. Please note that the issue is scheduled to be fixed in Adobe Commerce 2.4.5.
feature: Variables
role: Admin
exl-id: 603161bf-fac3-4571-b872-d98de1bdf6b4
source-git-commit: 42e95722c59d29864bc631b5fadbe0bc520c8997
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# MDVA-44660: Grave accent character (&grave;) cannot be used for customer&#39;s name

The MDVA-44660 patch fixes the issue where the grave accent character (\`) cannot be used for a customer&#39;s name. This patch is available when the [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15 is installed. The patch ID is MDVA-44660. Please note that the issue is scheduled to be fixed in Adobe Commerce 2.4.5.

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce (all deployment methods) 2.4.2-p1 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

The grave accent character (\`) cannot be used for a customer&#39;s first and last name.

<u>重现步骤</u>：

通过管理员帐户创建新客户，或在店面中使用名字或姓氏中的重音符号进行注册，例如“L&#39;Epicerie”。

<u>预期的结果</u>：

可以创建名称中包含重音符号的新客户。

<u>实际结果</u>：

*名字无效！* Or *Last name is not valid* error is displayed.

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
