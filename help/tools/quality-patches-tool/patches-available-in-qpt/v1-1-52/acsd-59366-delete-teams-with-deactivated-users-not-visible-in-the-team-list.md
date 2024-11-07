---
title: “ACSD-59366：删除其已停用用户的团队在团队列表中不可见”
description: Adobe Commerce应用ACSD-59366修补程序以修复以下问题：当您尝试删除团队时，如果团队包含未在团队列表中显示的已停用用户，则会出现错误。
feature: GraphQL, Companies
role: Admin, Developer
source-git-commit: 8037db7a89cd850385dc88750e881f68ae62172f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-59366：删除其已停用用户的团队在团队列表中不可见

ACSD-59366修补程序修复了在尝试删除团队时出现错误的问题，该团队包含未在团队列表中显示的已停用用户。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52时，此修补程序可用。 修补程序ID为ACSD-59366。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.6

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当您删除团队时，该团队包含未在团队列表中显示的已停用用户。

<u>先决条件</u>：

已安装Adobe Commerce B2B模块，并启用公司。

<u>重现步骤</u>：

1. 创建公司用户并使用其登录。
1. 在公司结构下，创建一个新团队。
1. 在新团队下，创建新用户。
1. 编辑新用户并取消激活。
1. 选择团队并删除。

<u>预期的结果</u>：

团队有一个或多个非活动用户。 删除团队将取消分配这些用户。 您可以在[!UICONTROL Company Users]部分中找到不活动的用户。

<u>实际结果</u>：

当您尝试删除具有已停用用户的团队时，会发生错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。

