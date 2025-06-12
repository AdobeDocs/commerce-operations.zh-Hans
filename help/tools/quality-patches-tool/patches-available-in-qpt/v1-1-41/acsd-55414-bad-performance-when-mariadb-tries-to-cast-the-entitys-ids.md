---
title: ACSD-55414：当MariaDB尝试强制转换entitys_ids时，性能不佳
description: 应用ACSD-55414修补程序以修复Adobe Commerce问题。当MariaDB尝试将“entitys_ids”从字符串转换为整数时，它会妨碍重新索引的性能。
feature: Attributes
role: Admin, Developer
exl-id: 76309cef-559e-4a55-a27b-7d807ef9f74e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-55414：当MariaDB尝试转换`entitys_ids`时，性能不佳

ACSD-55414修补程序修复了MariaDB尝试将`entitys_ids`从字符串转换为整数时，重新索引的性能受到影响的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.41时，此修补程序可用。 修补程序ID为ACSD-55414。 请注意，Adobe Commerce 2.4.6中已修复该问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当MariaDB尝试将`entitys_ids`从字符串转换为整数时，重新索引的性能会受到影响。

<u>重现步骤</u>：

1. 通过设置&#x200B;*50000*&#x200B;简单产品来更新`setup/performance-toolkit/profiles/ce/small.xml`。
1. 通过执行命令生成此配置文件： `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`。
1. 运行重新索引： `bin/magento indexer:reindex catalog_product_attribute`。

<u>预期的结果</u>：

重新索引需要合理的时间才能完成。

<u>实际结果</u>：

重新索引需要花费太多时间才能完成。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
