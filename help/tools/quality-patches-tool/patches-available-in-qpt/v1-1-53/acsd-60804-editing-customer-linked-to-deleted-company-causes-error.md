---
title: “ACSD-60804：编辑与已删除公司关联的客户会导致错误”
description: 应用ACSD-60804修补程序以修复Adobe Commerce问题，该问题导致编辑与已删除公司关联的客户时出现错误*在null*上调用成员函数getSuperUserId() 。
feature: Companies, Customers, B2B
role: Admin, Developer
source-git-commit: 1231dac065565ff636424673a15ae4148a5f84dd
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-60804：编辑与已删除公司关联的客户会导致错误

ACSD-60804修补程序修复了以下问题：编辑与已删除公司关联的客户会导致在null *上发生错误*&#x200B;调用成员函数getSuperUserId()。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53时，此修补程序可用。 修补程序ID为ACSD-60804。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

编辑与已删除公司关联的客户会导致在null *上调用成员函数getSuperUserId()时出现错误*。

<u>先决条件：</u>：

安装和启用Adobe Commerce B2B模块。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Settings]** > **[!UICONTROL B2B]** > **[!UICONTROL Enable Company]**。
1. 转到&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL Company]** > **[!UICONTROL Create New Company]**。
1. 登录实例的`mysql`。
1. 删除`entity_id` = *1*&#x200B;的公司。
1. 转到&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL All Customers]**。
1. 编辑在创建公司时自动创建的客户。

<u>预期的结果</u>：

编辑客户时未引发异常错误。

<u>实际结果</u>：

发生错误：如果没有公司与客户关联，则在null *上调用成员函数getSuperUserId()。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
