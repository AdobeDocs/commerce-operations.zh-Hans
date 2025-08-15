---
title: ACSD-65684：在B2B 1.5.2中升级Magento_Company缓慢，company_structure中的记录超过100,000条
description: 应用ACSD-65684修补程序以修复由于在company_structure表中处理大量记录（约100,000个以上）而导致B2B 1.5.2中的Magento_Company模块升级耗时过长的Adobe Commerce问题。
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: 1b45ebe4-4fb4-4fb5-b107-a2d44ec784e0
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-65684： `Magento_Company` 1.5.2中的[!DNL B2B]升级缓慢，`company_structure`中有超过100,000条记录

ACSD-65684修补程序修复了在处理`Magento_Company`表中的100,000多条记录时升级[!DNL B2B] 1.5.2中的`company_structure`模块耗时过长的性能问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64时，此修补程序可用。 修补程序ID为ACSD-65684。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce B2B（所有部署方法） 1.5.2

**与Adobe Commerce版本兼容：**

* Adobe Commerce B2B（所有部署方法） 1.5.2

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

处理`Magento_Company`表中的100,000多条记录时，在[!DNL B2B] 1.5.2中升级`company_structure`模块花费的时间过长，出现性能问题。

<u>重现步骤</u>：

1. 使用[!DNL B2B]安装Adobe Commerce 2.4.7-p4。
1. 将100,000条记录添加到`company_structure`表。
1. 升级到Adobe Commerce 2.4.7-p5和最新的[!DNL B2B]模块(1.5.2)。
1. 应用修补程序ACSD-65540。
1. 运行：

```
bin/magento setup:upgrade
```

<u>预期的结果</u>：

`setup:upgrade`在合理的时间内完成。

<u>实际结果</u>：

`setup:upgrade`需要很长时间才能完成。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
