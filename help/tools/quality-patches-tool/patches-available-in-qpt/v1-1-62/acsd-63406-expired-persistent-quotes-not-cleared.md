---
title: ACSD-63406：运行persistent_clear_expired cron作业时未清除过期的持久引号
description: Adobe Commerce应用ACSD-63406修补程序以修复以下问题：当“persistent_clear_expired”cron作业运行时，任何cron作业都不会清除过期的永久性引号。
feature: Quotes, Shopping Cart
role: Admin, Developer
exl-id: 795d1ddf-0d5b-406c-870b-36cb92cf07fa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-63406：运行`persistent_clear_expired` cron作业时未清除过期的永久引号

ACSD-63406修补程序修复了`persistent_clear_expired` cron作业运行时任何cron作业都无法清除过期的永久引号的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62时，此修补程序可用。 修补程序ID为ACSD-63406。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.7-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4-p9 - 2.4.4-p12、2.4.5-p8 - 2.4.5-p11、2.4.6-p6 - 2.4.7-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

运行`persistent_clear_expired` cron作业时，任何cron作业都不会清除过期的持久引号。

<u>重现步骤</u>：

1. 创建类别和产品。
1. 转到&#x200B;**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]**。
   1. 将所有选项设置为&#x200B;*是*。
   1. 将&#x200B;**[!UICONTROL Persistence Lifetime (seconds)]**&#x200B;设置为&#x200B;*60*。
1. 在店面创建客户帐户并登录。
1. 将产品添加到购物车。
1. 注销，等待60秒，然后重新登录。

<u>预期的结果</u>：

`persistent_clear_expired` cron作业应根据配置中的持久性生命周期设置删除持久性引号。

<u>实际结果</u>：

客户报价的`is_persistent`值在报价表中仍为&#x200B;*1*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。


## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
