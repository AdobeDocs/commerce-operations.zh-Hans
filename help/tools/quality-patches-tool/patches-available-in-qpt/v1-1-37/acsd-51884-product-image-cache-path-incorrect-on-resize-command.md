---
title: ACSD-51884：调整大小命令上的产品图像缓存路径不正确
description: 应用ACSD-51884补丁以修复Adobe Commerce问题，该问题导致在运行resize命令后产品图像缓存路径不正确。
feature: Products
role: Admin
exl-id: a3779e4b-2749-460e-a0a8-656b26bb06fa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-51884：调整大小命令上的产品图像缓存路径不正确

ACSD-51884修补程序修复了运行resize命令后，产品图像缓存路径不正确的内部错误问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.37时，此修补程序可用。 修补程序ID为ACSD-51884。 请注意，Adobe Commerce 2.4.7中已修复此问题。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

调整大小命令上的产品图像缓存路径不正确。

<u>重现步骤</u>：

1. 创建新网站/商店/商店。
1. 创建产品并将其分配给两个网站并上传产品图像。
1. 创建新主题(请参阅附加的Adobe.zip)。
1. 在`app/design/Adobe/theme/etc/view.xml`更改中：

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">1</var>
</vars>
```

到

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">0</var>
</vars>
```

1. 将主题应用于之前创建的商店评论。
1. 查看第二个网站上的产品页面。 产品图像可正确显示。
1. 使用刷新缓存：
   `bin/magento cache:flush`
1. 查看第二个网站上的产品页面。

<u>预期的结果</u>：

产品图像可正确显示。

<u>实际结果</u>：

产品图像不存在。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
