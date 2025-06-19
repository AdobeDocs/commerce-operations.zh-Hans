---
title: ACSD-51853：使用页面生成器未应用复制的文本样式
description: 应用ACSD-51853补丁可修复以下问题：使用Page Builder时未应用复制的文本样式。Adobe Commerce
feature: Page Builder
role: Admin
exl-id: fda5ba6e-4786-473c-a3a2-7356aa20f5ae
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-51853：使用页面生成器未应用复制的文本样式

ACSD-51853修补程序修复了在使用页面生成器时未应用复制的文本样式的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.34时，此修补程序可用。 修补程序ID为ACSD-51853。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用页面生成器时，不会应用复制的文本样式

<u>重现步骤</u>：

1. 登录管理员。
1. 前往> **内容** > **页面** > **打开任何页面** > **使用页面生成器编辑**。
1. 从&#x200B;**[!UICONTROL Elements]**&#x200B;拖动行和&#x200B;*文本*。
1. 复制&#x200B;**扩充的内容**，将该文本粘贴到&#x200B;**[!UICONTROL Page Builder]**&#x200B;中。

<u>预期的结果</u>

复制的文本将粘贴所有样式。

<u>实际结果</u>

复制的文本将粘贴为纯文本，并且所有样式都将丢失。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
