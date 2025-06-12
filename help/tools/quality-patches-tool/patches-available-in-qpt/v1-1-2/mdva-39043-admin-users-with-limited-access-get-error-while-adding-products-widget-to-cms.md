---
title: MDVA-39043：管理员用户将小组件添加到CMS页面时遇到错误
description: MDVA-39043修补程序修复了具有有限访问权限的管理员用户在将“产品”构件添加到CMS页面时收到错误的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-39043。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: Admin Workspace, CMS, Products
role: Admin
exl-id: 82488249-cca3-4a28-bdc1-fa93a4c9dc2f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# MDVA-39043：管理员用户将小组件添加到CMS页面时遇到错误

MDVA-39043修补程序修复了具有有限访问权限的管理员用户在将“产品”构件添加到CMS页面时收到错误的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2后，即可使用此修补程序。 修补程序ID为MDVA-39043。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

Adobe Commerce（所有部署方法） 2.4.2-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.4 - 2.4.3

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

具有有限访问权限的管理员用户在将“产品”构件添加到CMS页面时收到错误。

<u>重现步骤</u>：

1. 使用仅有权编辑内容的管理员登录到后端。
1. 转到&#x200B;**内容** > **页面**。
1. 打开任意页面进行编辑。
1. 使用&#x200B;**页面生成器**&#x200B;编辑内容。
1. 从&#x200B;**添加内容**&#x200B;部分添加&#x200B;**产品**&#x200B;构件。
1. 在&#x200B;**产品**&#x200B;小组件上单击&#x200B;**配置**。

<u>预期的结果</u>：

未显示错误。

<u>实际结果</u>：

收到以下错误消息：

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。
