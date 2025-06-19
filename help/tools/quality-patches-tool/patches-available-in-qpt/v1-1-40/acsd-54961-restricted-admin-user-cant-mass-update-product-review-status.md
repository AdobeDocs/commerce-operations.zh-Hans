---
title: ACSD-54961：受限管理员用户无法批量更新[!UICONTROL Product Review status]
description: 应用ACSD-54961补丁以修复受限管理员用户无法批量更新产品审核状态的Adobe Commerce问题。
feature: Products
role: Admin, Developer
exl-id: d303365c-d7c7-4aca-9f33-75d67bcbe573
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-54961：受限管理员用户无法批量更新[!UICONTROL Product Review status]

ACSD-54961修补程序修复了受限管理员用户无法批量更新[!UICONTROL Product Review status]的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40时，此修补程序可用。 修补程序ID为ACSD-54961。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

受限管理员用户无法批量更新[!UICONTROL Product Review status]。

<u>重现步骤</u>：

1. 创建其他网站、商店和商店视图。
1. 将产品添加到第2个商店，然后添加评论。
1. 创建仅具有第2家商店访问权限的受限制管理员用户。
1. 以受限管理员用户身份登录，然后转到&#x200B;**[!UICONTROL  Marketings]** > **[!UICONTROL Reviews]** > **[!UICONTROL Mass Update]**，并将&#x200B;**状态**&#x200B;设置为&#x200B;*已批准*&#x200B;或&#x200B;*待处理*。

<u>预期的结果</u>：

受限管理员用户可以使用&#x200B;**[!UICONTROL Mass Update]**&#x200B;操作更新审阅。

<u>实际结果</u>：

使用&#x200B;**[!UICONTROL Mass Update]**&#x200B;操作更新审阅时出错。<br>
`var/log/exception.log`包含类似的错误：

```
report.CRITICAL: TypeError: array_intersect(): Argument #1 ($array) must be of type array, null given in app/code/Magento/AdminGws/Model/Models.php:439
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
