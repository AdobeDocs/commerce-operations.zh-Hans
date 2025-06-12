---
title: ACSD-47666：在[!UICONTROL User Roles]中搜索不起作用
description: 应用ACSD-47666修补程序以修复Adobe Commerce问题，该问题导致[!UICONTROL User Roles]上的筛选函数无法按预期工作。
feature: Roles/Permissions, Search
role: Admin
exl-id: fb66f114-b95c-402e-a35a-e552f264966c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-47666：在&#x200B;**[!UICONTROL User Roles]**&#x200B;中搜索不起作用

ACSD-47666修补程序解决了&#x200B;**[!UICONTROL User Roles]**&#x200B;中的搜索不起作用的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23时，此修补程序可用。 修补程序ID为ACSD-47666。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

**[!UICONTROL User Roles]**&#x200B;上的筛选器函数无法按预期工作。

<u>重现步骤</u>：

1. 登录到Adobe Commerce管理员> **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**。
1. 从列表中打开任何现有的角色。
1. 打开&#x200B;**[!UICONTROL Role Users]**&#x200B;选项卡。
1. 在列中键入任意查询。
1. 按Enter。

<u>预期的结果</u>：

**[!UICONTROL User Roles]**&#x200B;筛选器函数应根据查询筛选结果。

<u>实际结果</u>：

无限加载，出现控制台错误&#x200B;_（索引）：9未捕获的TypeError：无法读取null的属性（正在读取&#39;down&#39;）_。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。 

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
