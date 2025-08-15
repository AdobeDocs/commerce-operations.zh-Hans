---
title: MDVA-44940：从管理员保存类别时出现SQL错误
description: MDVA-44940修补程序修复了从管理员保存类别时发生SQL错误的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16后，即可使用此修补程序。 修补程序ID为MDVA-44940。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
feature: Admin Workspace, Categories, Sales Channels
role: Admin
exl-id: de4384f1-a75d-4726-810f-6560a7c57b82
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-44940：从管理员保存类别时出现SQL错误

MDVA-44940修补程序修复了从管理员保存类别时发生SQL错误的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16后，即可使用此修补程序。 修补程序ID为MDVA-44940。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

从管理员保存类别时发生SQL错误。

<u>重现步骤</u>：

1. 安装示例数据。
1. 创建第二个网站，并将商店组分配给默认类别。

   * 创建分配给新商店组的商店视图。

1. 创建库存和分配给此库存的附加源，以及分配给第二个网站的销售渠道。
1. 创建分配给第二个网站的测试产品。
1. 转到&#x200B;**管理员** > **目录** > **类别**，选择&#x200B;**范围** = **第二个网站**，然后转到&#x200B;**类别中的产品** > **自动排序** >将缺货产品移到底部，然后单击&#x200B;**保存**。

<u>预期的结果</u>：

将保存类别。

<u>实际结果</u>：

出现以下错误： *保存类别*&#x200B;时出错。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的Quality Patches Tool[!DNL Quality Patches Tool]，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
