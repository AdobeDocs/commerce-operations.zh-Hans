---
title: ACSD-63182：在复制捆绑产品后保存产品时出错
description: 应用ACSD-63182修补程序以修复在启用MSI的情况下复制捆绑产品后保存产品时出现错误的Adobe Commerce问题。
feature: Inventory, Catalog Management
Role: Admin, Developer
exl-id: 2c664c89-e00e-40a8-9127-8c3f36c5bab9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-63182：在复制捆绑产品后保存产品时出错

ACSD-63182修补程序修复了在复制捆绑产品后无法保存用作捆绑选项的简单产品的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58时，此修补程序可用。 修补程序ID为ACSD-63182。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在复制捆绑产品后保存用作捆绑选项的简单产品时出错。

<u>重现步骤</u>：

1. 创建新的MSI源和库存。
1. 创建两个简单的产品： **p1**&#x200B;和&#x200B;**p2**。
1. 创建捆绑产品&#x200B;**b1**，并将&#x200B;**p1**&#x200B;和&#x200B;**p2**&#x200B;作为捆绑选项。
1. 编辑&#x200B;**捆绑产品b1**&#x200B;并单击&#x200B;***[!UICONTROL Save and Duplicate]***。
1. 编辑&#x200B;**简单产品p1**&#x200B;并单击&#x200B;**[!UICONTROL Save]**。

<u>预期的结果</u>：

保存产品时不会出错。

<u>实际结果</u>：

将显示以下错误：
*异常：已存在具有相同ID“XXX”的项目(Magento\Catalog\Model\Product\Interceptor)。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
