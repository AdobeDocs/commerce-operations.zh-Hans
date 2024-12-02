---
title: MDVA-39923：在B2B快速订购功能中按SKU搜索区分大小写
description: MDVA-39923修补程序修复了以下问题：当客户在B2B快速订购功能中按SKU搜索订单（大小写与保存名称的大小写不同）时，会出现错误。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-39923。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: B2B, Catalog Management, Orders, Search
role: Admin
exl-id: 9bed5615-b398-42f5-8313-ae2acca59155
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39923：在B2B快速订购功能中按SKU搜索区分大小写

MDVA-39923修补程序修复了以下问题：当客户在B2B快速订购功能中按SKU搜索订单（大小写与保存名称的大小写不同）时，会出现错误。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-39923。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.1-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在B2B快速订购功能中通过SKU搜索是区分大小写的，当使用与保存SKU的大小写不同的大小写时，会显示错误。

<u>先决条件</u>：

已安装B2B模块。

<u>重现步骤</u>：

1. 登录到管理员并转到&#x200B;**商店** > **配置** > **B2B**。
1. 启用&#x200B;**共享目录**&#x200B;和&#x200B;**快速订购**。
1. 创建具有大写SKU的产品，例如TEST20-1234
1. 将创建的产品分配给&#x200B;**共享目录**。
1. 以客户身份登录，然后单击&#x200B;**快速订购**。
1. 以小写形式输入SKU，例如test20-1234。

<u>预期的结果</u>：

无论使用何种箱子，都应找到产品。

<u>实际结果</u>：

收到以下错误消息： *1个产品需要您注意*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
