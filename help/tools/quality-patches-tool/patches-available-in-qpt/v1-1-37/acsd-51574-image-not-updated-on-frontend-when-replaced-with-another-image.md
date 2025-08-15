---
title: ACSD-51574：用其他图像替换时，图像未在前端更新
description: 应用ACSD-51574补丁以修复Adobe Commerce问题，该问题导致在将图像替换为其他图像后，图像前端未更新。
feature: Configuration
role: Admin
exl-id: 199674fc-c3b3-4fee-9061-f0546833c1cd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-51574：用其他图像替换时，图像未在前端更新

ACSD-51574修补程序修复了将图像替换为其他图像后，未在前端更新图像的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.37时，此修补程序可用。 修补程序ID为ACSD-51574。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 - 2.4.7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

将图像替换为其他图像后，不会在前端更新图像。

<u>重现步骤</u>：

1. 创建带有几个图像的产品。
1. 编辑产品并上传具有已知名称的图像（示例： *image.jpg*）。
1. 保存产品。
1. 再次编辑产品并删除图像的旧版本，然后上传具有相同名称的新版本图像。 **确保新版本明显不同，以查看问题。**
1. 保存产品。 管理员和前端都会显示图像。
1. 再次编辑产品并重新上传相同的新图像（使用相同名称）。
1. 保存产品并在前端查看产品页面。

<u>预期的结果</u>：

第二次上传的图像应该是新图像，以及重命名的图像名称。

<u>实际结果</u>：

第二次上传的图像是之前已删除的旧版图像，而不是相同的新图像。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
