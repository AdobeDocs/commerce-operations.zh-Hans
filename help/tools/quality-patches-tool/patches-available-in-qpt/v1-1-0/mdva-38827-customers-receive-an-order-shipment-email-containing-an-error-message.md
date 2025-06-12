---
title: MDVA-38827：客户通过电子邮件收到订单发运错误
description: MDVA-38827修补程序修复了客户收到包含以下错误消息的订单发运电子邮件的问题： *很抱歉，生成此内容时出错*。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0后，即可使用此修补程序。 修补程序ID为MDVA-38827。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
exl-id: ab522c9c-2983-4c2f-b341-4487bdbee34d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-38827：客户通过电子邮件收到订单发运错误

MDVA-38827修补程序修复了客户收到包含以下错误消息的订单装运电子邮件的问题： *很抱歉，生成此内容时出错*。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0时，此修补程序可用。 修补程序ID为MDVA-38827。 请注意，该问题计划在Adobe Commerce 2.4.4中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

云基础架构上的Adobe Commerce 2.4.2-p1

**与Adobe Commerce版本兼容：**

Adobe Commerce（所有部署方法） 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

如果选择了通过电子邮件通知客户装运选项，客户将收到一封包含以下错误消息的电子邮件： *很抱歉，生成此内容时出错*。

<u>重现步骤</u>：

1. 转到&#x200B;**营销** > **通信** > **电子邮件模板**，然后选择&#x200B;**添加新模板**。
   * 选择&#x200B;**Magento Sales** > **新装运**。
   * 单击&#x200B;**加载模板**。
   * 添加模板名称（例如，核心送货模板）并单击&#x200B;**保存**。
1. 转到&#x200B;**商店** >设置> **配置** > **销售** > **销售电子邮件**：
   * 启用&#x200B;**装运注释**。
   * 在Shipment Comment Email Template and Shipment Comment Email Template for Guest下选择&#x200B;**Core Shipping Template**（参阅步骤1中的“Add a template name”部分）。
1. 下订单。 转到“管理”面板> **销售** > **订单**，单击&#x200B;**查看**，然后发送该订单。
1. 订单状态将从“待处理”更改为“正在处理”。
1. 单击左侧边栏菜单上的&#x200B;**装运**，然后单击&#x200B;**查看**&#x200B;以查看订单。
1. 在&#x200B;**装运历史记录**&#x200B;下方的&#x200B;**注释文本**&#x200B;中添加注释并选中&#x200B;**通过电子邮件通知客户**&#x200B;复选框。
1. 单击&#x200B;**提交评论**。

<u>预期的结果</u>：

生成包含装运注释的销售电子邮件。

<u>实际结果</u>：

电子邮件中收到以下错误消息： *很抱歉，生成此内容时出错。*

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用[!DNL Quality Patches Tool]指南中的Quality Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool]：搜索修补程序](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)。
