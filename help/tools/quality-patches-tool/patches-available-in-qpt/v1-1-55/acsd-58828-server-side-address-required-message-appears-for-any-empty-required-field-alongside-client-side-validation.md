---
title: ACSD-58828：服务器端*地址必填*消息会在客户端验证旁边显示任何空的必填字段
description: 应用ACSD-58828修补程序以修复Adobe Commerce问题：如果任何必填字段留空，则服务器端验证消息*地址为必填项*与客户端验证消息一起显示。
feature: Shipping/Delivery, Checkout
role: Admin, Developer
exl-id: 6c19773d-cb75-409f-bbd7-78d285a0252a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-58828：服务器端&#x200B;*地址为必填*&#x200B;消息将显示任何空的必填字段，以及客户端验证

ACSD-58828修补程序修复了以下问题：如果任何必填字段留空，则需要在客户端验证消息旁边显示服务器端验证消息&#x200B;*地址*。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55时，此修补程序可用。 修补程序ID为ACSD-58828。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**
* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**
* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果任何必填字段留空，则服务器端验证消息&#x200B;*地址为必填*&#x200B;与客户端验证消息一起出现。

重现问题的步骤：

1. 以客户身份登录。
1. 将产品添加到购物车。
1. 继续结帐。
1. 保持送货地址不变。
1. 选择&#x200B;**[!UICONTROL Flat rate]**&#x200B;并选择&#x200B;**[!UICONTROL Next]**。
1. 取消选中&#x200B;**[!UICONTROL My billing and shipping address are the same]**。
1. 从下拉列表中添加新地址。
1. 将任何必填字段留空并选择&#x200B;**[!UICONTROL Update]**。

预期结果：

错误消息描述缺少签出所需的信息或不正确的信息。

实际结果：

需要错误&#x200B;*地址。 请输入并重试。显示*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
