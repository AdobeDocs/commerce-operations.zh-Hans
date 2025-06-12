---
title: ACSD-45849：暂存更新后视频元数据丢失
description: ACSD-45849修补程序修复了在应用暂存更新后视频元数据丢失的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18后，即可使用此修补程序。 修补程序ID为ACSD-45849。 请注意，Adobe Commerce 2.4.4中已修复此问题。
feature: Staging, Page Content
role: Admin
exl-id: cbab0120-585a-47ef-8ed9-abb2da1ec3d6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-45849：暂存更新后视频元数据丢失

ACSD-45849修补程序修复了在应用暂存更新后视频元数据丢失的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18时，此修补程序可用。 修补程序ID为ACSD-45849。 请注意，Adobe Commerce 2.4.4中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

应用暂存更新后，视频元数据将丢失。

<u>重现步骤</u>：

1. 在&#x200B;**管理员** > **商店** > **配置** > **目录** > **产品视频**&#x200B;中设置YouTube API密钥。
1. 用YouTube视频创建产品。 请注意，已填写URL、标题和描述。
1. 使用任何参数为产品创建新的计划更新，而不更改&#x200B;*图像和视频*&#x200B;部分。
1. 单击计划更改中的&#x200B;**查看/编辑**。
1. 转到&#x200B;**图像和视频**&#x200B;并单击视频。

<u>预期的结果</u>：

URL、标题和描述包含相应的数据。

<u>实际结果</u>：

URL、标题和描述字段为空。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
