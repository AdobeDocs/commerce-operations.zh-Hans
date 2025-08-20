---
title: ACSD-65983：在Admin中重新配置捆绑的产品报价时出错
description: Adobe Commerce应用ACSD-65983修补程序以修复以下问题：尝试在后端的[!UICONTROL Sales] > [!UICONTROL Quotes] > [!UICONTROL Edit]屏幕中配置捆绑产品时出现错误。
feature: B2B, Quotes
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8a8f2b273bcbcf135677ad7ca289398bf660e02e
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---


# ACSD-65983：在Admin中重新配置捆绑的产品报价时出错

ACSD-65983修补程序修复了在Admin后端重新配置捆绑的产品报价时返回错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69时，此修补程序可用。 修补程序ID为ACSD-65983。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

在管理员后端重新配置捆绑的产品报价时返回错误。

<u>重现步骤</u>：

1. 转到“管理”面板并启用&#x200B;**[!UICONTROL B2B Feature]**： **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Feature]**。
1. 创建固定数量的捆绑产品（例如： *$10*），并在&#x200B;*选项1*&#x200B;中添加&#x200B;*2*&#x200B;个数量为&#x200B;**0**&#x200B;的简单产品，在&#x200B;*选项2*&#x200B;中添加&#x200B;**other**&#x200B;个数量为2的简单产品。
1. 从前端创建公司帐户。
1. 转到&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]**，将创建的公司和产品分配给新/自定义共享目录。
1. 在前端以&#x200B;**公司用户**&#x200B;身份登录，并从捆绑包中添加一个简单的产品到购物车。
1. 打开购物车页面并作为&#x200B;**请求报价**&#x200B;提交。
1. 转到后端并编辑已创建的报价。
1. 在&#x200B;**报价单项目**&#x200B;部分中，单击&#x200B;**配置**&#x200B;按钮。
1. 从&#x200B;**选项2**&#x200B;中选择另一个简单产品。
1. 现在单击&#x200B;**确定**&#x200B;按钮并查看错误消息。

<u>预期的结果</u>：

您可以正常从管理员处成功配置所请求的报价项目，而不会显示任何错误消息。

<u>实际结果</u>：

您会看到以下错误消息：

*服务器出现技术问题并生成错误。 重试以继续您正在执行的操作。 如果问题仍然存在，请稍后再试。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]
* 云基础架构上的Adobe Commerce： Commerce on Cloud Infrastructure指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： Tools指南中用于优质修补程序的Self-service工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
