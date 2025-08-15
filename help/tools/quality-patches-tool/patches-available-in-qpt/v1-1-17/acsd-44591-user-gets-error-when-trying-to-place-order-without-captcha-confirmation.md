---
title: ACSD-44591：订单时出错且未进行验证码确认
description: ACSD-44591修补程序解决了用户在未经CAPTCHA确认的情况下尝试下达订单时出现错误的问题。
feature: Orders
role: Admin
exl-id: 4b8a8090-a2ba-428c-9a04-7c0842e94a6f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-44591：订单时出错且未进行验证码确认

ACSD-44591修补程序解决了用户在未经CAPTCHA确认的情况下尝试下达订单时出现错误的问题。
安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17时，此修补程序可用。 修补程序ID为ACSD-44591。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.3-p1

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户在尝试下达订单但未进行验证码确认时会收到错误。

<u>重现步骤</u>：

1. 配置Google ReCaptcha v2（我不是机器人）。
1. 启用ReCaptcha以进行签出。
1. 尝试在不单击ReCaptcha的情况下下订单。
1. 收到有关缺少ReCaptcha的错误消息（*ReCaptcha验证失败，请重试*），单击&#x200B;**ReCaptcha**，然后尝试下订单。

<u>预期的结果</u>：

使用不正确的ReCaptcha将不会下订单。

<u>实际结果</u>：

您会收到以下错误：

* *ReCaptcha验证失败，请重试*
* *没有ID = 1*&#x200B;的此类购物车

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关Quality Patches Tool的更多信息，请参阅：

* 已发布[质量修补程序工具：支持知识库中用于自助提供质量修补程序](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)的新工具。
* [使用](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)指南中的Quality Patches Tool[!DNL Quality Patches Tool]，检查修补程序是否可用于Adobe Commerce问题。

有关QPT中其他可用修补程序的信息，请参阅[[!DNL Quality Patches Tool]指南中的](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)：搜索修补程序[!DNL Quality Patches Tool]。
