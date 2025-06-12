---
title: ACSD-51907：受限管理员用户无法创建离线退款的贷项通知单
description: 应用ACSD-51907补丁以修复Adobe Commerce问题，该问题导致受限管理员用户无法创建包含离线退款的贷项通知单。
exl-id: 1c44d99b-7633-4768-b7e7-332f3666a5d9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# ACSD-51907：受限管理员用户无法创建离线退款的贷项通知单

ACSD-51907修补程序修复了受限管理员用户无法创建具有离线退款的贷项通知单的性能问题。 安装[!DNL Quality Patches Tool (QPT)] 1.1.33时，此修补程序可用。 修补程序ID为ACSD-51907。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.2-p2

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

受限管理员用户无法创建具有离线退款的贷项通知单。

<u>重现步骤</u>：

1. 在默认网站上创建&#x200B;**客户**。
1. 使用相关的&#x200B;*商店*&#x200B;和&#x200B;*商店视图*&#x200B;创建&#x200B;**新网站**。
1. 将默认网站设置为新网站，清除缓存。
1. 更改客户配置： **管理员** > **商店** > **配置** > **客户** > **客户配置** > **共享客户帐户=全局**。
1. 在&#x200B;**管理员** > **系统** > **权限**&#x200B;中创建角色范围设置为新建网站&#x200B;*（仅访问销售数据）*&#x200B;的新管理员用户角色。
1. 使用此角色创建新的管理员帐户。
1. 使用在线付款方式&#x200B;*(如Auth.net或PayPal)*&#x200B;创建新订单。
1. 以受限管理员用户身份登录。
1. 前往&#x200B;**销售** > **订单** >然后&#x200B;**订单查看页面**。
1. 创建发票。
1. 定位至“发票”标签。
1. 单击&#x200B;**发票**。
1. 单击&#x200B;**[!UICONTROL Credit Memo]**。
1. 选中&#x200B;**[!UICONTROL Refund to Store Credit]**&#x200B;复选框，将其附近的文本字段设置为&#x200B;*1*&#x200B;值。
1. 单击&#x200B;**[!UICONTROL Refund Offline]**&#x200B;按钮。

<u>预期的结果</u>：

已创建贷项通知单，*$1*&#x200B;已退款到商店贷项。

<u>实际结果</u>：

显示错误消息&#x200B;*需要更多权限才能查看此项目*。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
