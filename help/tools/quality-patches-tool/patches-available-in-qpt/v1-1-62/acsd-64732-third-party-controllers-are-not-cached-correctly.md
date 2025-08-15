---
title: ACSD-64732：第三方控制器未通过客户区段正确缓存
description: 应用ACSD-64732补丁以修复第三方控制器未正确通过客户区段缓存的Adobe Commerce问题。
feature: Cache
role: Admin, Developer
exl-id: 378e5a96-06dd-4796-9e45-a67cf539fcce
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# ACSD-64732：第三方控制器未通过客户区段正确缓存

ACSD-64732修补程序修复了第三方控制器无法通过客户区段正确缓存的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62时，此修补程序可用。 修补程序ID为ACSD-64732。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

第三方控制器未通过客户区段正确缓存。

<u>重现步骤</u>：

1. 转到自定义控制器(/catalog/category/vary)。
1. 转到&#x200B;**[!UICONTROL Network]**&#x200B;选项卡并检查&#x200B;**[!DNL X-Magento-Vary]**&#x200B;的值。

<u>预期的结果</u>：

自定义控制器上的&#x200B;**[!UICONTROL X-Magento-Vary]**&#x200B;值应该相同。

<u>实际结果</u>：

**[!UICONTROL X-Magento-Vary]**&#x200B;的值不同，这会导致缓存丢失。 这意味着访问自定义控制器时无法使用之前生成的缓存。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的升级和修补程序>应用修补程序。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
