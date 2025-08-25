---
title: ACSD-66506：删除并重新分配共享目录产品后发生后端错误
description: 应用ACSD-66506修补程序以修复后端引发错误*所请求的产品不存在的Adobe Commerce问题。 验证产品，并在删除以前分配的产品并将新产品分配给共享目录后重试*。
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8f77101832ccfb415d040c202f0fc7221f97419a
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# ACSD-66506：删除并重新分配共享目录产品后发生后端错误

ACSD-66506修补程序修复了后端引发错误&#x200B;*所请求的产品不存在的问题。 请验证产品，并在删除以前分配的产品并将新产品分配给共享目录后重试*。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68时，此修补程序可用。 修补程序ID为ACSD-66506。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

删除以前分配的产品并将新产品分配到&#x200B;**[!UICONTROL Shared Catalog]**&#x200B;后，后端返回以下错误： *请求的产品不存在。 请验证产品并重试*

<u>重现步骤</u>：

1. 使用性能工具包创建一些产品： `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`
1. 转到&#x200B;**[!UICONTROL [!DNL B2B] Features]**&#x200B;配置并将&#x200B;**[!UICONTROL Enable Company]**&#x200B;和&#x200B;**[!UICONTROL Enable Shared Catalog]**&#x200B;设置为`Yes`。
1. 创建新的共享目录。
1. 将所有生成的产品分配给新创建的共享目录。
1. 使用&#x200B;**[!UICONTROL Product Import]**&#x200B;删除分配给共享目录的产品。
   1. 导出按SKU过滤的产品。
   1. 选择&#x200B;**[!UICONTROL Import Behavior: Delete]**，然后导入相同的文件。
1. 打开&#x200B;**[!UICONTROL Shared Catalog]**&#x200B;并配置定价和结构。
   1. 选择&#x200B;**[!UICONTROL Set Pricing and Structure]**。
   1. 单击&#x200B;**[!UICONTROL Next]**，然后单击&#x200B;**[!UICONTROL Generate Catalog]**。
   1. 单击&#x200B;**[!UICONTROL Save]**。

<u>预期的结果</u>：

不会发生任何错误，即使发生错误，产品仍保留在共享目录中。

<u>实际结果</u>：

发生错误： *请求的产品不存在。 验证产品并重试*，所有产品都将从共享目录中删除。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
