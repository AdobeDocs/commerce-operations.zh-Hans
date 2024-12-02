---
title: ACSD-51471：管理员用户无法保存捆绑产品的计划更新
description: 应用ACSD-51471修补程序以修复Adobe Commerce问题，该问题导致管理员用户无法为使用具有计划更新的简单产品的捆绑产品保存计划更新。
exl-id: d8134111-63f0-4476-a407-677bda52fa90
source-git-commit: f6abbbb28a3077f7bf26a393388c5059fcd8c599
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-51471：管理员用户无法保存捆绑产品的计划更新

ACSD-51471修补程序修复了以下问题：对于使用具有计划更新的简单产品的捆绑产品，管理员用户无法保存其计划更新。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33时，此修补程序可用。 修补程序ID为ACSD-51471。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

对于使用本身具有计划更新的简单产品的捆绑产品，管理员用户无法保存其计划更新。

<u>重现步骤</u>：

1. 创建一个简单的产品。
1. 为仅具有&#x200B;*开始日期*&#x200B;且没有&#x200B;*结束日期*&#x200B;的简单产品添加计划更新。
1. 应用更新后，更改产品的SKU。
1. 创建捆绑产品，并将步骤1中创建的简单产品添加为子产品。
1. 为捆绑产品创建计划更新以启用捆绑产品。 为计划更新提供&#x200B;*开始日期*&#x200B;和&#x200B;*结束日期*。
1. 保存计划的更新。

<u>预期的结果</u>：

已成功保存计划的更新。

<u>实际结果</u>：

保存计划更新时出现以下错误： *请求的产品不存在。 请验证产品并重试。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
