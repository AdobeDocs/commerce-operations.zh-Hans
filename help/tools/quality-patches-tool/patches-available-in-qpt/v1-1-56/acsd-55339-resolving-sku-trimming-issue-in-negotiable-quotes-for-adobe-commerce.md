---
title: ACSD-55339：解决Adobe Commerce的可协商报价中的SKU裁切问题
description: 应用ACSD-55339修补程序以修复Adobe Commerce问题，该问题导致前导为零的产品SKU被裁剪，从而导致协商错误。
feature: B2B, Quotes
role: Admin, Developer
exl-id: 7a9f92df-fb3e-4723-b731-155c6c4fc431
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-55339：解决Adobe Commerce的可协商报价中的SKU裁切问题

ACSD-55339修补程序修复了前导为0的产品SKU被裁剪而导致协商过程中出现错误的问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.56时，此修补程序可用。 修补程序ID为ACSD-55339。 请注意，该问题计划在Adobe Commerce B2B 1.5.0中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在可转让报价中使用前导为零的数值产品SKU时，会进行修剪，从而导致无法更新数量或设置价格的错误。

<u>重现步骤</u>：

1. 导航到管理面板中的产品创建部分。
1. 将产品的[!UICONTROL SKU]设置为01910。
1. 登录到店面并执行以下操作：
   1. 将产品添加到购物车。
   1. 查看和编辑购物车。
   1. 请求报价。
1. 转到[!UICONTROL admin] > [!UICONTROL Quote] > [!UICONTROL View]和[!UICONTROL Add Products by SKU] - 01910。

**注意：** SKU显示为&#x200B;*1910*，而不是&#x200B;*01910*。 这种差异会阻止用户更新数量或设置价格，因为目录中不存在带有SKU 1910的产品。

<u>预期的结果</u>：

可转让报价单应成功更新且无任何错误。

<u>实际结果</u>：

将显示一条警告消息，指示该产品不存在。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
