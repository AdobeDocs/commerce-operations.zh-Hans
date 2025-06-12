---
title: ACSD-47937：由于应用程序级别的缓存，未发送价格下降通知
description: 应用ACSD-47937修补程序以修复由于应用程序级别的缓存而无法始终发送降价通知的Adobe Commerce问题。
feature: Admin Workspace, Cache, Orders
role: Admin
exl-id: 91d8e677-c2bb-4230-bbe3-a2c5f9b82e16
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-47937：由于应用程序级别的缓存，未发送价格下降通知

ACSD-47937修补程序修复了由于应用程序级别的缓存而无法始终发送降价通知的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26时，此修补程序可用。 修补程序ID为ACSD-47937。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4和2.4.5-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4、2.4.5和2.4.5-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

客户不会收到后续产品价格更改的产品价格下降电子邮件。

<u>重现步骤</u>：

1. 在&#x200B;**[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**&#x200B;中为&#x200B;*[!UICONTROL Price Changes]*&#x200B;和&#x200B;*[!UICONTROL Back in Stock]*&#x200B;启用&#x200B;**[!UICONTROL Product Alert]**。
1. 启用&#x200B;**[!UICONTROL Display Out of Stock Products]**。
1. 创建数量= 0的简单产品(ABC)。
1. 从店面创建客户并订阅上述产品，获取产品降价提醒。
1. 启动客户产品警报。

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. 降低ABC产品的价格。
1. 触发产品警报cron。

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. 再次降低ABC产品的价格。
1. 触发产品警报cron。

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>如果您不熟悉[!DNL n98]工具，那么您可以像往常一样运行`bin/magento cron:run command`并监视`cron_schedule`表以确保`catalog_product_alert`作业获得成功状态。

<u>预期的结果</u>：

发送第二个降价电子邮件。

<u>实际结果</u>：

第二个降价电子邮件未发送。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)
* 云基础架构上的Adobe Commerce： Commerce on Cloud Infrastructure指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)

## 相关阅读

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题
* [在Commerce实施行动手册中修改数据库表的最佳实践](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
