---
title: ACP2E-3767：保存捆绑产品后，将重新显示最后一个捆绑选项
description: 应用ACP2E-3767修补程序以修复无法删除捆绑产品中的最后一个捆绑包选项的Adobe Commerce问题。
feature: Products, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f39442925d9cc82087af9e84d91137a0fcd0ec14
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# ACP2E-3767：保存捆绑产品后，将重新显示最后一个捆绑选项

ACP2E-3767修补程序修复了在保存捆绑产品后重新显示最后一个捆绑选项的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69时，此修补程序可用。 修补程序ID为ACP2E-3767。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

无法删除捆绑产品中的最后一个捆绑选项。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**。
1. 从下拉列表中选择&#x200B;**[!UICONTROL Simple Product]**。
1. 输入所需数据并保存。
1. 转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**。
1. 从下拉列表中选择&#x200B;**[!UICONTROL Bundle Product]**。
1. 输入所需数据。
1. 在捆绑包项目中，单击&#x200B;**[!UICONTROL Add Option]**。
1. 向新选项添加标题，然后单击&#x200B;**[!UICONTROL Add Products to Option]**。
1. 选择之前创建的简单产品，然后选择&#x200B;**[!UICONTROL Add Selected Products]**。
1. 保存捆绑包产品。
1. 删除捆绑包选项并保存。

<u>预期的结果</u>：

1. 已成功删除捆绑包选项。
1. 如果不允许删除，则会显示一条消息。

<u>实际结果</u>：

1. 束选项保持活动状态。
1. 未显示错误或通知。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
