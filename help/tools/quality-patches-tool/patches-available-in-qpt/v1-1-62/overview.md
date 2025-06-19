---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.62
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.62中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
exl-id: be8ffedc-b589-4a30-ba9a-eed705696825
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.62

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.62中提供的修补程序所修复的问题。

QPT v1.1.62包含以下修补程序：

1. **ACSD-63406**：修复了`persistent_clear_expired` cron作业运行时任何cron作业都无法清除过期的永久引号的问题。
1. **ACSD-63520**：修复了通过&#x200B;**[!UICONTROL Configurations]**&#x200B;在管理面板中添加的图像不符合最大上传大小限制的问题。
1. **ACSD-64523**：修复了在导入过程中（通过管理员或API）创建的新产品没有名称的问题，该问题会导致管理员界面中断并导致产品无效。
1. **ACSD-64532**：修复了将设置为&#x200B;*false*&#x200B;的环境变量视为字符串&#x200B;*false*&#x200B;而不是布尔值false的问题。
1. **ACSD-64592**：修复了在非默认商店中礼品卡的电子邮件中的报销申请链接始终将礼品卡报销申请重定向到默认网站的问题。
1. **ACSD-65164**：修复了错误消息&#x200B;*某些选定的项选项当前不可用*&#x200B;的问题，在使用单个选定的复选框自定义选项重新订购可配置产品时出现。
1. **ACSD-64732**：修复了第三方控制器未通过客户区段正确缓存的问题。

使用左侧的菜单导航到特定的修补程序页面。
