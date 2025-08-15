---
title: ACSD-63469：多个规则未正确应用固定金额购物车折扣
description: Adobe Commerce应用ACSD-63469修补程序以修复以下问题：当应用多个规则时，无法正确应用整个购物车的固定金额折扣。
feature: Price Rules
role: Admin, Developer
exl-id: fb6dee57-281e-4165-8b70-7ff5949eb677
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-63469：多个规则未正确应用固定金额购物车折扣

ACSD-63469修补程序修复了在应用多个规则时，整个购物车的固定金额折扣无法正确应用的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59时，此修补程序可用。 修补程序ID为ACSD-63469。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

当同时应用多个&#x200B;**[!UICONTROL Fixed amount discount for whole cart]**&#x200B;规则并且产品具有折扣或特殊价格时，折扣值的计算不正确。

<u>重现步骤</u>：

1. 创建两款定价分别为850美元和85美元的产品，并分别将其特价定为765美元和68美元。
1. 按如下方式创建两个&#x200B;**[!UICONTROL Cart Price Rules]**：
   * 规则1
      * **[!UICONTROL Conditions]**：对于$850产品，将&#x200B;*数量*&#x200B;设置为&#x200B;*等于或大于2*
      * **[!UICONTROL Actions]**：应用&#x200B;**[!UICONTROL Fixed amount discount for whole cart]**/*$153*
   * 规则2
      * **[!UICONTROL Conditions]**：对于$85产品，将&#x200B;*数量*&#x200B;设置为&#x200B;*等于或大于2*
      * **[!UICONTROL Actions]**：应用&#x200B;**[!UICONTROL Fixed amount discount for whole cart]**/*$14*
1. 将两个产品都添加到购物车，每个产品的数量为2。

<u>预期的结果</u>：

购物车中应用的折扣为167美元。

<u>实际结果</u>：

购物车中应用的折扣为$41。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 安装修补程序后所需的其他步骤

（本节为可选内容；在应用修补程序后，可能需要执行一些步骤来修复此问题。） 

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
