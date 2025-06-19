---
title: ACSD-42807：店面未显示自定义货币符号
description: ACSD-42807修补程序修复了自定义货币符号未显示在店面中的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17后，即可使用此修补程序。 修补程序ID为ACSD-42807。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。
feature: Storefront
role: Developer
exl-id: 9aa3dd73-fab8-4a5b-b177-5226a37ee3c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-42807：店面未显示自定义货币符号

ACSD-42807修补程序修复了自定义货币符号未显示在店面中的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17时，此修补程序可用。 修补程序ID为ACSD-42807。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.0 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

店面不显示自定义货币符号。

<u>重现步骤</u>：

1. 转到&#x200B;**商店** > **设置** > **配置** > **常规** > **货币设置**&#x200B;并选择任意自定义货币。 例如，**墨西哥比索**。
1. 转到&#x200B;**存储** > **设置** > **配置** > **常规** > **区域设置选项**，然后选择&#x200B;**西班牙语（墨西哥）**。
1. 转到&#x200B;**存储** > **货币符号**&#x200B;并将货币符号配置为&#x200B;**MX$**。
1. 检查前端的货币符号。

<u>预期的结果</u>：

默认的货币符号为“MX$”，货币设置为“墨西哥比索”，区域设置设置为“西班牙语（墨西哥）”。

<u>实际结果</u>：

默认货币符号显示“$”。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
