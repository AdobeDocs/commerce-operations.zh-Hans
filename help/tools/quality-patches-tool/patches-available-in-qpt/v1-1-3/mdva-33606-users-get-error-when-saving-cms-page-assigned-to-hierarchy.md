---
title: MDVA-33606：保存分配给层次结构的CMS页面时，用户收到错误
description: MDVA-33606修补程序解决了在保存分配给层次结构树的CMS页面时，用户收到*发现唯一约束冲突*错误的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3后，即可使用此修补程序。 修补程序ID为MDVA-33606。 请注意，Adobe Commerce 2.4.3中已修复此问题。
feature: CMS
role: Admin
exl-id: 19aaa13f-7ee6-49bc-b1d9-c288dc93b951
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# MDVA-33606：保存分配给层次结构的CMS页面时，用户收到错误

MDVA-33606修补程序解决了在保存分配给层次结构树的CMS页面时，用户收到&#x200B;*发现的唯一约束冲突*&#x200B;错误的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3时，此修补程序可用。 修补程序ID为MDVA-33606。 请注意，Adobe Commerce 2.4.3中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1-2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在尝试保存分配给层次结构树的CMS页面时，用户收到以下错误消息： *发现唯一约束冲突*。

<u>重现步骤</u>：

1. 创建新的CMS页面。 将范围设置为“所有存储视图”。 这是您的CMS第1页。
1. 创建新的商店视图。 这是您的商店视图2。
1. 转到&#x200B;**Content** > **层次结构** >将CMS页面1添加到层次结构树。
1. 将范围更改为“存储视图2”。
   * 取消选中“使用父节点层次结构”。
   * 将CMS第1页添加到此范围并保存。
1. 现在将范围更改为默认存储视图。
   * 取消选中“使用父节点层次结构”。
   * 将CMS第1页添加到此范围并保存。
1. 转到&#x200B;**内容** > **页面** > **添加新页面**。
   * 将页面标题命名为“Page 2”。
   * 在“网站中的页面”部分中，分配给“所有商店视图”和两个商店视图（“默认商店视图”和“商店视图2”），然后单击“**保存页面**”。
1. 在CMS编辑页面中，打开层级选项卡。
   * 将页面2分配给“存储视图2”节点、“默认”节点和“所有网站”节点。

<u>预期的结果</u>：

您能够将CMS页面分配到所有三个节点，而不会出现任何错误。

<u>实际结果</u>：

您收到以下错误：发现&#x200B;*唯一约束冲突*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* [已发布质量修补程序工具：用于自助提供质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查是否有可用于Adobe Commerce问题的修补程序。

有关QPT中其他可用修补程序的信息，请参阅QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)中可用的修补程序部分。
