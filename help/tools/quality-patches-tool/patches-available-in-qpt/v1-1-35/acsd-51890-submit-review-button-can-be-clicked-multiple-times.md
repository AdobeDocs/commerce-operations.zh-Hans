---
title: ACSD-51890：可多次单击[!UICONTROL Submit review]按钮
description: 应用ACSD-51890修补程序以修复可多次单击[!UICONTROL Submit Review]按钮而无需 [!DNL Google reCAPTCHA v3] 验证的Adobe Commerce问题。
feature: Products
role: Admin
exl-id: db69ccdc-c66e-4bdb-9783-772f2af0d33f
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-51890：无需进行&#x200B;**[!DNL Google reCAPTCHA v3]**&#x200B;验证，即可多次单击&#x200B;**[!UICONTROL Submit Review]**&#x200B;按钮

>[!NOTE]
>
>此修补程序已被[ACSD-55112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55112-submit-review-button-can-be-clicked-multiple-times.md)替换。

ACSD-51890修补程序修复了在没有&#x200B;**[!DNL Google reCAPTCHA v3]**&#x200B;验证的情况下多次单击&#x200B;**[!UICONTROL Submit Review]**&#x200B;按钮的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.35时，此修补程序可用。 修补程序ID为ACSD-51890。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

无需进行&#x200B;**[!DNL Google reCAPTCHA v3]**&#x200B;验证，即可多次单击&#x200B;**[!UICONTROL Submit Review]**&#x200B;按钮。

<u>重现步骤</u>：

1. 启用&#x200B;**[!DNL Google reCAPTCHA v3]**&#x200B;以进行产品审查。
1. 打开产品页面并导航到&#x200B;**[!UICONTROL Review]**&#x200B;分区，并确保[!DNL reCAPTCHA]可见。
1. 填写审核表单，并尽快多次单击&#x200B;**[!UICONTROL Submit Review]**&#x200B;按钮。
1. 从管理员处打开&#x200B;**[!UICONTROL Review]**&#x200B;部分。

<u>预期的结果</u>

不会创建重复的审核。

<u>实际结果</u>

创建重复的审核。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>)。
