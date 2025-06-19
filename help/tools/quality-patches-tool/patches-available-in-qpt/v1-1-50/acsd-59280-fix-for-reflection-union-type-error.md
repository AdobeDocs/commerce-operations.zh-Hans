---
title: ACSD-59280： 2.4.4-pX安装中出现“ReflectionUnionType：：getName()”错误
description: 应用ACSD-59280修补程序以修复Adobe Commerce问题，该问题导致在安装2.4.4-pX版本期间出现“调用未定义的方法ReflectionUnionType：：getName()”错误。
feature: Install, Upgrade
role: Admin, Developer
exl-id: 5a47dad4-4490-4e3d-93f2-9b176fb144d9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# ACSD-59280：在2.4.4-pX安装中出现`ReflectionUnionType::getName()`错误

ACSD-59280修补程序修复了在安装2.4.4-pX版本期间出现`call to undefined method ReflectionUnionType::getName()`错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50时，此修补程序可用。 修补程序ID为ACSD-59280。 请注意，Adobe Commerce 2.4.5中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

2.4.4-pX安装期间出现`ReflectionUnionType::getName()`错误。

<u>重现步骤</u>：

使用&#x200B;*[!UICONTROL Composer]*&#x200B;执行全新安装。

<u>预期的结果</u>：

安装过程完成，没有出现错误。

<u>实际结果</u>：

您在`setup:upgrade`过程中看到以下错误：

`Call to undefined method ReflectionUnionType::getName()`

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
