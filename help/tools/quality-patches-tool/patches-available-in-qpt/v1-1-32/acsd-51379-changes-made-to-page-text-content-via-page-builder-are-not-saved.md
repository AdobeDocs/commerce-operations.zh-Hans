---
title: ACSD-51379：未保存通过 [!DNL Page Builder] 对页面文本内容所做的更改
description: 应用ACSD-51379修补程序以修复通过 [!DNL Page Builder] 对页面文本内容所做的更改未保存的Adobe Commerce问题。
feature: Page Builder, Page Content
role: Admin
exl-id: 03fc2865-04b6-4330-b80c-8d694baa8c88
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51379：未保存通过[!DNL Page Builder]对页面文本内容所做的更改

ACSD-51379修补程序修复了通过[!DNL Page Builder]对页面文本内容所做的更改未保存的问题。 安装[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32时，此修补程序可用。 修补程序ID为ACSD-51379。 请注意，该问题计划在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

未保存通过[!DNL Page Builder]对页面文本内容所做的更改。

<u>重现步骤</u>：

1. 登录到Admin。
1. 转到&#x200B;**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]**。
1. 在&#x200B;**[!UICONTROL Content]**&#x200B;选项卡上创建一个具有一个行和一个文本元素的测试页面。
1. 保存页面并返回&#x200B;**[!UICONTROL Content]**&#x200B;选项卡。
1. 通过选择并更改文本来编辑文本。

   **注意：**&#x200B;仅当选择并更改文本而未激活编辑器时，此问题才可复制。

1. 单击测试页面上的&#x200B;**[!UICONTROL Save and Close]**&#x200B;按钮。
1. 再次打开测试页面并检查&#x200B;**[!UICONTROL Content]**&#x200B;选项卡。

<u>预期的结果</u>：

为原始文本元素和复制的文本元素成功保存了新文本。

<u>实际结果</u>：

文本元素已成功复制，但未保存新文本。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool] 已发布：支持知识库中用于自助提供高质量修补程序的新工具](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [使用[!UICONTROL Quality Patches Tool]指南中的 [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)检查修补程序是否可用于您的Adobe Commerce问题。


有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
