---
title: ACSD-53998：注销后，基于客户区段的动态块无法正常工作
description: 应用ACSD-53998修补程序以修复Adobe Commerce问题：从客户帐户注销后，基于客户区段的动态块无法正常工作。
feature: Customers, Page Builder, Personalization
role: Admin, Developer
exl-id: aa7001c7-bb35-4e5c-8ac9-3ed84b75d7cd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-53998：注销后，基于客户区段的动态块无法正常工作

ACSD-53998修补程序修复了从客户帐户注销后，基于客户区段的动态块无法正常工作的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.39时，此修补程序可用。 修补程序ID为ACSD-53998。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4-p2 - 2.4.4-p6、2.4.5-p1 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

从客户帐户注销后，基于客户区段的动态块无法正常工作。

<u>先决条件</u>：

安装并启用[!DNL Page Builder]模块。

<u>重现步骤</u>：

1. 无条件创建两个客户区段。
1. 为每个区段创建两个动态块。
1. 将包含两个动态块的块创建为[!DNL Page Builder]个动态块。
1. 创建包含上述块的构件，并使该块在所有页面的页脚部分下可见。
1. 清除缓存。
1. 打开主页。
1. 以客户身份登录。
1. 注销。

<u>预期的结果</u>：

为已登录客户创建的横幅不会显示给访客用户。

<u>实际结果</u>：

即使从客户帐户注销，也会显示为已登录客户区段创建的横幅。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
