---
title: ACSD-55112：可多次单击[!UICONTROL Sumbit Review]按钮
description: 应用ACSD-55112修补程序以修复可多次单击[!UICONTROL Submit Review]按钮而无需 [!DNL Google reCAPTCHA v3] 验证的Adobe Commerce问题。
feature: Products
role: Admin, Developer
exl-id: 270c8adc-4f85-4643-8425-341ab0849d2b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# ACSD-55112：可多次单击[!UICONTROL Submit Review]按钮

>[!NOTE]
>
>此修补程序将替换[ACSD-51890](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-35/acsd-51890-submit-review-button-can-be-clicked-multiple-times.md)。

ACSD-55112修补程序修复了在没有[!UICONTROL Submit Review]验证的情况下多次单击[!DNL Google reCAPTCHA v3]按钮的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42时，此修补程序可用。 修补程序ID为ACSD-55112。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

获取以下错误：

```JS
_jquery.validate.js:799 Uncaught TypeError: Cannot read properties of undefined (reading 'call'). Exception occurred when checking element login-email, check the 'validate' method.
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)：搜索修补程序[!DNL Quality Patches Tool]。
