---
title: ACSD-44851：子类别无法打开或展开的类别
description: 当用户无法打开或展开包含子类别的类别时，本文提供了相应问题的解决方案。
feature: Categories
role: Admin
exl-id: c1ad13d8-94e1-47cf-ad65-9bc5ce1c26ad
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-44851：子类别无法打开或展开的类别

ACSD-44851修补程序解决了用户无法打开或扩展具有子类别的类别的问题。 安装[Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20时，此修补程序可用。 修补程序ID为ACSD-44851。 请注意，该问题计划在Adobe Commerce 2.4.6中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.4

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>该修补程序可能适用于具有新的Quality Patches Tool版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

用户无法打开或展开包含子类别的类别。

<u>重现步骤</u>：

1. 在Adobe Commerce管理中，创建一个类别树，该树包含两个根类别以及每个类别的几个子类别。
1. 打开移动设备视图/模拟器或缩小窗口宽度，直到布局变为可移动为止。
1. 打开目录的主菜单。
1. 尝试展开根类别。
1. 尝试打开类别。

<u>预期的结果</u>：

菜单可访问。

<u>实际结果</u>：

移动菜单的第二层未打开。

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： Quality Patches Tool指南中的[Quality Patches Tools >用法](/help/tools/quality-patches-tool/usage.md)。

* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
