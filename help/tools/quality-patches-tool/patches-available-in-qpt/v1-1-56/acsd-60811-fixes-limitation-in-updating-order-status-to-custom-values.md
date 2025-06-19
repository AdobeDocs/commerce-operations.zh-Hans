---
title: ACSD-60811：修复了将订单状态更新为自定义值时的限制
description: 应用ACSD-60811修补程序以修复Adobe Commerce问题，该问题导致仅当当前状态为“正在处理”或“欺诈”时，才可能使用自定义值或注释更新订单状态。
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 6d5391b3-7014-4d0a-b4ab-799f0733bbca
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-60811：修复了将订单状态更新为自定义值时的限制

ACSD-60811修补程序修复了以下问题：使用自定义值或注释更新订单状态只有在当前状态为“[!UICONTROL Processing]”或“[!UICONTROL Suspected Fraud]”时才可行。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56时，此修补程序可用。 修补程序ID为ACSD-60811。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法）2.4.7。 2.4.7-p1、2.4.7-p2、2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

仅当当前状态为&#x200B;*正在处理*&#x200B;或&#x200B;*欺诈*&#x200B;时，才可以使用自定义值或注释更新订单状态。 选择并提交新状态时，订单状态保持不变。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Order Status]**&#x200B;以在管理面板中创建自定义订单状态。
1. 单击&#x200B;**[!UICONTROL Assign Status to State]**&#x200B;将自定义状态分配给订单状态。
1. 在管理面板的订单视图页面中更改订单状态。

<u>预期的结果</u>：

管理员用户应该能够在管理员面板中将订单状态更改为自定义订单状态。

<u>实际结果</u>：

选择并提交新订单状态时，订单状态将保持不变。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
