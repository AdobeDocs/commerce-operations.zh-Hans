---
title: ACSD-59514：管理员中的Forms在浏览器控制台中出现 [!DNL Page Builder] throw错误
description: 应用ACSD-59514修补程序以修复Adobe Commerce问题：管理员中带有 [!DNL Page Builder] 抛出的表单错误“[!DNL Page Builder]”呈现5秒钟，并且未释放锁定。 在浏览器控制台中提交表单后，无法保存更改。
feature: Page Builder
role: Admin, Developer
exl-id: 3d1167d2-0a75-48ac-bc31-5bbd3c4a409e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-59514：管理员中的Forms在浏览器控制台中抛出[!DNL Page Builder]错误

ACSD-59514修补程序修复了Admin中具有[!DNL Page Builder]的表单抛出错误&#x200B;*[!DNL Page Builder]且呈现5秒而不释放锁定的问题。提交表单后，在浏览器控制台中显示*，无法保存更改。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50时，此修补程序可用。 修补程序ID为ACSD-59514。 请注意，该问题计划在Adobe Commerce 2.4.8中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p8

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

具有[!DNL Page Builder]的Admin中的Forms引发错误&#x200B;*[!DNL Page Builder]，该错误持续呈现5秒且未释放锁定。提交表单后，在浏览器控制台中显示*，无法保存更改。

<u>先决条件</u>：

已安装和启用Adobe Commerce [!DNL Page Builder]模块。

<u>重现步骤</u>：

1. 打开管理面板并单击[!UICONTROL Content]按钮。
1. 选择块并编辑块。
1. 更改内容并单击[!UICONTROL Save]。
1. 打开控制台并查看错误消息。

<u>预期的结果</u>：

已成功保存块。

<u>实际结果</u>：

加载器不会停止旋转，并且不会保存块。 浏览器控制台中会显示以下错误：
*[!DNL Page Builder]已呈现5秒钟，但未释放锁定。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
