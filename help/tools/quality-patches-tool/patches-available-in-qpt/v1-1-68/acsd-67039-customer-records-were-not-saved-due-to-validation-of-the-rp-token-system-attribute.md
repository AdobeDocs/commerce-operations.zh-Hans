---
title: ACSD-67039：由于rp_token系统属性验证，未保存客户记录
description: 应用ACSD-67039修补程序以修复编码变音导致rp_token上的验证中断的Adobe Commerce问题。
feature: Customers, Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: e5995e28-b6b5-4955-a52a-895842c6b6e8
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 1%
---
# ACSD-67039：由于`rp_token`系统属性验证，未保存客户记录

ACSD-67039修补程序修复了由于`rp_token`系统属性的验证而无法保存客户记录的问题，并且变音符号验证仅应用于生成的客户电子邮件。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68时，此修补程序可用。 修补程序ID为ACSD-67039。 请注意，此问题已在Adobe Commerce 2.4.7中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p9

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6-p9 - 2.4.6-p11

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

编码变音符号导致`rp_token`验证失败，该验证操作已从验证中排除。 仅允许按预期对电子邮件地址使用变音符。

<u>重现步骤</u>：

1. 安装Adobe Commerce 2.4.4版本。
1. 创建客户。
1. 将Adobe Commerce从已创建客户的2.4.4早期版本升级到版本2.4.6。
1. 将加密密钥设置为`env.php` =
   *d337b914e91ff703b1e94ba4156aadf0*
1. 将以下值设置为`customer_entity`表下的任何客户的数据库中：
*`rp_token` = *incr4869*
*`rp_token_created_at` =* 2021-04-29 20:06:14*
1. 在“管理”面板中，转到&#x200B;**[!UICONTROL Customers]** > **[!UICONTROL All Customers]**。
1. 编辑刚刚为其更新了上述值的客户。
1. 单击&#x200B;**[!UICONTROL Save Customer]**&#x200B;或&#x200B;**[!UICONTROL Save and Continue Edit]**。

<u>预期的结果</u>：

客户值保存成功。

<u>实际结果</u>：

未保存客户记录，管理员用户看到错误消息&#x200B;*保存客户时出现问题。*
`system.log`包含以下错误：

```text
report.CRITICAL: Exception message: Notice: iconv(): Detected an incomplete multibyte character in input string in /vendor/magento/module-eav/Model/Attribute/Data/Text.php on line 190
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)
* 云基础架构上的Adobe Commerce： Commerce on Cloud Infrastructure指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： Tools指南中用于优质修补程序的Self-service工具](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)
