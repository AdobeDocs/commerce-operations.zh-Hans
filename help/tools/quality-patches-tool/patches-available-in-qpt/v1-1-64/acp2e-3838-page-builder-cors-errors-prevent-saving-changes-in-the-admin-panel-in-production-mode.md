---
title: ACP2E-3838： [!DNL Page Builder] CORS错误导致无法在生产模式的管理面板中保存更改
description: 应用ACP2E-3838修补程序以修复Adobe Commerce问题，该问题导致 [!DNL Page Builder] CORS错误导致无法在生产模式的管理面板中保存更改。
feature: Page Builder, Page Content, Admin Workspace
role: Admin, Developer
exl-id: 0d590c0e-e21c-4553-a0a3-9332e22796f3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACP2E-3838： [!DNL Page Builder] CORS错误导致无法在生产模式的管理面板中保存更改

ACP2E-3838修补程序修复了[!DNL Page Builder] CORS错误导致无法在生产模式的管理面板中保存更改的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64时，此修补程序可用。 修补程序ID为ACP2E-3838。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4-p9 - 2.4.4-p12、2.4.5-p8 - 2.4.5-p11、2.4.6-p6 - 2.4.6-p9、2.4.7 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

[!DNL Page Builder] CORS错误导致无法在生产模式的管理面板中保存更改。

<u>重现步骤</u>：

1. 登录到管理面板。
1. 转到&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Pages]**。
1. 单击&#x200B;**[!UICONTROL Add New Page]**，或选择现有的CMS页面并单击&#x200B;**[!UICONTROL Edit]**。
1. 单击&#x200B;**[!UICONTROL Edit with Page Builder]**&#x200B;以添加新内容块或编辑现有块。
1. 对内容进行任何更改，例如添加文本、图像或其他元素。
1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;按钮。

<u>预期的结果</u>：

页面内容应可在没有任何错误的情况下成功保存。

<u>实际结果</u>：

1. 无法保存[!DNL Page Builder]更改。
1. 浏览器控制台将记录与CORS相关的错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
