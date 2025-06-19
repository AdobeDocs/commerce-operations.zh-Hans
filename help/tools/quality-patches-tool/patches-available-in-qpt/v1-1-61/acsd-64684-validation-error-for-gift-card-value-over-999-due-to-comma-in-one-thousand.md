---
title: ACSD-64684：保存值超过999的礼品卡时出现验证错误，因为逗号以1000为单位(1,000)
description: 应用ACSD-64684修补程序以修复在保存值超过999的礼品卡时出现验证错误的Adobe Commerce问题，该错误是由于逗号“1,000”(1,000)导致的。
feature: Catalog Management
role: Admin, Developer
exl-id: 327c5d28-b52c-4da9-a905-8a3deb755241
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-64684：保存值超过999的礼品卡时出现验证错误，因为逗号以1000为单位(1,000)

ACSD-64684修补程序修复了在保存值超过999的礼品卡时，由于逗号“one 000”(1,000)而产生验证错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61时，此修补程序可用。 修补程序ID为ACSD-64684。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

编辑和保存值大于999的礼品卡时，由于数字中存在逗号（千位分隔符），例如“1,000”(1,000)，发生验证错误。

<u>重现步骤</u>：

1. 创建礼品卡产品。
   1. 输入1,000作为[!UICONTROL Amount]。
   1. 单击&#x200B;**[!UICONTROL Save]**。

<u>预期的结果</u>：

* 节省了1,000的新礼品卡。

<u>实际结果</u>：

* 当礼品卡金额大于999时发生验证错误。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
