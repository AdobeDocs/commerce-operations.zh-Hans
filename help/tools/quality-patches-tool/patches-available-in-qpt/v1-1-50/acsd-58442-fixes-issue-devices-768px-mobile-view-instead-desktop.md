---
title: ACSD-58442：修复了宽度为768px的设备被视为移动设备的问题，该问题会导致菜单和标题在移动设备视图而非桌面中加载
description: 应用ACSD-58442修补程序以修复Adobe Commerce问题，该问题导致将宽度为768px的设备视为移动设备，从而导致在移动视图而非桌面中加载菜单和标头。
feature: Storefront
role: Admin, Developer
exl-id: 86ea64aa-10fc-4fa3-9902-918fb8983ca0
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-58442：修复了宽度为768px的设备被视为移动设备的问题，该问题会导致菜单和标题在移动设备视图而非桌面中加载

ACSD-58442修补程序修复了Adobe Commerce的问题：宽度为768px的设备被视为移动设备，导致菜单和标题加载到移动视图而不是桌面中。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50时，此修补程序可用。 修补程序ID为ACSD-58442。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

系统现在将宽度为768px的设备视为桌面，以确保菜单和标题正确加载。 以前，宽度为768像素的设备被视为移动设备，从而导致菜单和标题在移动视图中加载。

<u>重现步骤</u>：

1. 在iPad Mini上加载主页，或使用浏览器的检查工具将浏览器大小调整为宽度&#x200B;*768px*。
1. 打开主菜单。

<u>预期的结果</u>：

菜单和标题作为桌面视图加载。

<u>实际结果</u>：

菜单和标题将作为移动视图加载。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
