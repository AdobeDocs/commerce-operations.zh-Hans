---
title: ACSD-57570：修复了管理员用户访问共享目录的受限问题
description: 应用ACSD-57570修补程序以修复Adobe Commerce问题：如果有权访问特定存储的受限管理员用户无法一致地查看分配给产品的所有共享目录或保存客户信息，则会导致系统不一致。
feature: B2B, Companies, Roles/Permissions
role: Admin, Developer
exl-id: 3eeaf1f1-0338-459f-99ec-53764f3f12db
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# ACSD-57570：修复了管理员用户访问共享目录的受限问题

ACSD-57570修补程序修复了以下问题：具有特定存储访问权限的受限管理员用户无法一致地查看分配给产品的所有共享目录或保存客户信息，从而导致系统不一致。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57时，此修补程序可用。 修补程序ID为ACSD-57570。 请注意，该问题计划在Adobe Commerce 2.5.0中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4-p3

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.3 - 2.4.4-p9

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

有权访问特定商店的受限管理员用户无法始终查看所有共享目录或保存客户，从而导致不一致。 对于多个商店，受限管理员看不到新公司或自定义共享目录。

<u>重现步骤</u>：

1. 按以下顺序设置商店：
   * 创建一个名为W2的新网站。
   * 为默认网站创建新的商店视图。
   * 为网站W2创建一个名为W2S2的新商店。
   * 为存储W2S2创建新的存储视图W2S2SV1。
   * 为商店W2S2创建另一个名为W2S2SV2的新商店视图。
   * 为W2创建公司。
1. 分配产品：
   * 仅将部分产品分配给W1。
   * 仅将部分产品分配给W2。
   * 将某些产品同时分配给W1和W2。
1. 创建自定义共享目录并将所有产品分配给该目录。
1. 创建只能访问&#x200B;**W2S2**&#x200B;而非&#x200B;**W2**&#x200B;的自定义管理员角色。
1. 将受限管理员用户分配给新的自定义管理员角色。
1. 以受限管理员用户身份登录。
1. 验证访问权限：
   * 查看可查看哪些公司。
   * 检查可查看哪些共享目录。
   * 打开产品列表，验证您是否能够看到产品被分配到的所有共享目录。

<u>预期的结果</u>：

行为应保持一致。

<u>实际结果</u>：

如果只创建了一个额外的网站、商店和商店视图，则受限管理员用户可以在产品列表中看到公司、共享目录和两个共享目录。 进行上述设置后，受限管理员将无法看到新公司或自定义共享目录，并且产品列表中只会显示默认共享目录。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [!DNL Quality Patches Tool]指南中的[[!DNL Quality Patches Tool] >使用情况](/help/tools/quality-patches-tool/usage.md)。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
