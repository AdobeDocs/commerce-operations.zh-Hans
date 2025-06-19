---
title: ACSD-62475：修复了购物车中的礼品卡合并问题
description: 应用ACSD-62475修补程序以修复包含不同详细信息的礼品卡产品被错误地合并到购物车中的单行项目中的Adobe Commerce问题。
feature: Shopping Cart, Quotes
role: Admin, Developer
exl-id: fc97c3c0-dc1b-4546-aad0-ef3b4b6a3415
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62475：修复了购物车中的礼品卡合并问题

ACSD-62475修补程序修复了包含不同详细信息的礼品卡产品被错误地合并到购物车中的单行项目中的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56时，此修补程序可用。 修补程序ID为ACSD-62475。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

添加到购物车且具有独特发件人或收件人详细信息的礼品卡产品会错误地合并到单个行项目中，从而导致数据不一致。

<u>重现步骤</u>：

1. 使用以下设置创建[!UICONTROL Gift Card]产品：
   * **[!UICONTROL Card Type]**： [!UICONTROL Virtual]
   * **[!UICONTROL Amount]**： 10

1. 在店面，创建新用户并登录。

1. 将礼品卡产品添加到购物车，详细信息如下：
   * **[!UICONTROL Sender Name]**：发件人1
   * **[!UICONTROL Sender Email**]： sender1@test.com
   * **[!UICONTROL Recipient Name**]：收件人1
   * **[!UICONTROL Recipient Email**]： recipient1@test.com


1. 注销

1. 将相同的礼品卡产品添加到购物车，详细信息如下：
   * **[!UICONTROL Sender Name]**：发件人2
   * **[!UICONTROL Sender Email**]： sender2@test.com
   * **[!UICONTROL Recipient Name**]：收件人2
   * **[!UICONTROL Recipient Email**]： recipient2@test.com

1. 重新登录并检查购物车。

<u>预期的结果</u>：

两张礼品卡应该显示为两个单独的行项目及其各自的详细信息。

<u>实际结果</u>：

礼品卡合并为一个数量为2的行项目，保留第一张礼品卡的详细信息。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
