---
title: ACSD-61366：“bin/magento setup:static-content:deploy —jobs 4”命令遇到多个作业失败并出现错误
description: 应用ACSD-61366修补程序以修复Adobe Commerce问题，该问题导致“bin/magento setup:static-content:deploy —jobs 4”命令遇到多个作业失败，并且必须在主机参数*错误中配置*Port，尽管为数据库连接指定了端口。
feature: SCD
role: Admin, Developer
exl-id: d71a4833-a236-429b-a4e5-7d7d51c2caeb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-61366： `bin/magento setup:static-content:deploy --jobs 4`命令遇到多个作业失败并出现错误

ACSD-61366修补程序修复了`bin/magento setup:static-content:deploy --jobs 4`命令遇到多个作业失败的问题，其中必须在主机参数&#x200B;*错误中配置*&#x200B;端口，尽管为数据库连接指定了端口。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52时，此修补程序可用。 修补程序ID为ACSD-61366。 请注意，此问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.7-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

`bin/magento setup:static-content:deploy --jobs 4`命令遇到多个作业失败，且必须在主机参数&#x200B;*错误中配置*&#x200B;端口，尽管为数据库连接指定了端口。

<u>重现步骤</u>：

1. 在`app/etc/env.php`中指定数据库连接中的端口。
1. 运行`bin/magento setup:static-content:deploy --jobs 4`命令。

<u>预期的结果</u>：

静态内容部署成功完成。

<u>实际结果</u>：

命令失败，因为&#x200B;*端口必须在主机参数*&#x200B;错误中配置。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的[!UICONTROL Quality Patches Tool]检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
