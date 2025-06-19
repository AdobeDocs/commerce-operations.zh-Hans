---
title: ACSD-63067：解决店面分组产品的数量验证问题
description: 应用ACSD-63067修补程序以修复Adobe Commerce问题：当只有一个产品的数量不正确时，分组产品中的所有产品数量会错误地高亮显示为无效。
feature: Storefront
role: Admin, Developer
exl-id: a497f2c4-8bf0-41da-955a-a58e79f09c08
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-63067：解决店面分组产品的数量验证问题

ACSD-63067修补程序修复了以下问题：当只有一个产品的数量不正确时，分组产品中的所有产品数量会错误地高亮显示为无效。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58时，此修补程序可用。 修补程序ID为ACSD-63067。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.7-p2

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在分组产品中，其中一个子产品中的无效数量会导致所有数量被错误地高亮显示为无效。 此外，对于所有产品，将出现验证消息，而不是只针对具有无效数量的产品。

<u>重现步骤</u>：

1. 创建至少有两个简单产品作为选项的新分组产品。
1. 打开店面上的产品。
1. 为其中一个选项输入无效数量（例如： -1），为其余选项输入有效数量（例如： 1）。
1. 单击&#x200B;**[!UICONTROL Add to Cart]**。

<u>预期的结果</u>：

只有具有无效数量的产品才会被高亮显示为无效。

<u>实际结果</u>：

所有产品数量都高亮显示为无效，并且消息&#x200B;*请指定产品数量。 将显示所有产品*。


## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
