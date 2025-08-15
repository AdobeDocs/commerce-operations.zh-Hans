---
title: ACSD-63974：通过分页修复了[!UICONTROL Requisition List]加载时间缓慢的问题
description: 应用ACSD-63974修补程序以修复项目过多时[!UICONTROL Requisition List]页面加载时间较长的问题。
feature: B2B
role: Admin, Developer
exl-id: 1798baa3-da2f-44eb-8312-1f1b3f75b24d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-63974：通过分页修复了[!UICONTROL Requisition List]加载时间缓慢的问题

ACSD-63974修补程序修复了在项目过多时&#x200B;**[!UICONTROL Requisition List]**&#x200B;页面加载时间较长的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61时，此修补程序可用。 修补程序ID为ACSD-63974。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当存在许多项目(2000+)时，**[!UICONTROL Requisition List]**&#x200B;页面需要很长时间才能加载。 这是由于缺少分页，导致所有项目同时加载。

<u>重现步骤</u>：

1. 转到&#x200B;**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > *[!UICONTROL General]* > **[!UICONTROL B2B features]**。
1. 将&#x200B;**[!UICONTROL Enable Requisition List]**&#x200B;设置为&#x200B;*是*。
1. 通过编辑`simple_products`中的`setup/performance-toolkit/profiles/ce/small.xml`节点生成2000多种产品。
1. 运行以下命令：

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. 创建客户并登录。
1. 将所有产品添加到&#x200B;**[!UICONTROL Requisition List]**。
1. 在店面查看&#x200B;**[!UICONTROL Requisition List]**。


<u>预期的结果</u>：

页面应在合理的时间内加载。


<u>实际结果</u>：

页面加载时间会随着项目数量增加而增加，因为所有项目都会因为缺少分页而一次性加载。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的升级和修补程序>应用修补程序。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
