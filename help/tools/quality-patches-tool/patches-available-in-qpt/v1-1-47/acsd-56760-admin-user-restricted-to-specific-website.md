---
title: ACSD-56760：管理员用户仅限访问特定网站，无法排序或添加新产品
description: 应用ACSD-56760修补程序以修复Adobe Commerce问题：该问题导致管理员用户仅限于访问特定网站，如果网络商店拥有自己的根类别，则该用户无法对类别进行排序或添加新产品。
role: Admin
exl-id: 2d75164e-c463-4e1a-aa6f-f420dbe0aaeb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# ACSD-56760：管理员用户仅限访问特定网站，无法排序或添加新产品

ACSD-56760修补程序修复了以下问题：管理员用户被限制在特定网站，如果网络商店拥有自己的根类别，则无法在类别中排序或添加新产品。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.47时，此修补程序可用。 修补程序ID为ACSD-56760。 请注意，该问题计划在Adobe Commerce 2.4.8-beta1中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

仅限特定网站的管理员用户，如果网络商店拥有自己的根类别，该用户无法在类别中排序或添加新产品。

<u>重现步骤</u>：

1. 创建&#x200B;*2*&#x200B;网站。
1. 创建只能访问&#x200B;**[!UICONTROL restricted admin user]** 1 *网站的*。
1. 以&#x200B;**[!UICONTROL restricted admin user]**&#x200B;身份登录，并尝试更改类别中的产品职位。

*案例1*：

* *2*&#x200B;存储。
* *2*&#x200B;根类别，每个网站都分配给自己的类别根。

*案例2*：

* *2*&#x200B;存储。
* 仅将&#x200B;*1*&#x200B;根类别分配给这两个网站。

<u>预期的结果</u>：

* *用例1*：受限管理员应该能够对可用类别中的产品进行排序。
* *用例2*：受限管理员无法对可用类别中的产品进行排序，因为这样也会影响受限商店。

<u>实际结果</u>：

* *用例1*：受限管理员无法对可用类别中的产品进行排序。
* *案例2*：受限管理员可以对可用类别中的产品进行排序，从而影响受限商店。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
