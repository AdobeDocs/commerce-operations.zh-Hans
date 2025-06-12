---
title: MDVA-37984：应用暂存更新时，可视化促销程序无法正常工作
description: MDVA-37984修补程序解决了在应用暂存更新时，可视化促销器的“按规则匹配产品”功能无法正确筛选产品的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9后，即可使用此修补程序。 修补程序ID为MDVA-37984。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。
feature: Categories, Merchandising, Products, Staging
role: Admin
exl-id: 3aeb74a4-b6f7-453a-a8f6-45a345aaa74f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-37984：应用暂存更新时，可视化促销程序无法正常工作

MDVA-37984修补程序解决了在应用暂存更新时，可视化促销器的“按规则匹配产品”功能无法正确筛选产品的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9时，此修补程序可用。 修补程序ID为MDVA-37984。 请注意，该问题计划在Adobe Commerce 2.4.5中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

应用暂存更新时，可视促销器的“按规则匹配产品”功能无法正确筛选产品。

<u>重现步骤</u>：

1. 为任何现有产品创建计划更新。
   * 为`entity_id`和`row_id`设置不同的值。
1. 创建一个新的可配置产品，然后创建一个简单的产品（因此，新产品`entity_id`和`row_ids`也不同）。
   * 为了更便于复制问题，请为简单产品设置可区分的数量值，例如5000。
1. 转到类别> **类别**&#x200B;中的产品，并启用&#x200B;**按规则匹配产品**。
1. 现在，选择“数量”作为属性，“大于”作为运算符，“4500”作为值。
1. 单击&#x200B;**保存**。

<u>预期的结果</u>：

将列出新创建的可配置产品。

<u>实际结果</u>：

新创建的可配置产品未列出。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
