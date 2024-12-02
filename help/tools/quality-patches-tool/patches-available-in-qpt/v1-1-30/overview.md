---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.30
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.30中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin
exl-id: 36c6e0cc-fd8c-4583-b147-fe4897b101d8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.30

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.30中提供的修补程序所修复的问题。

QPT v1.1.30包含以下修补程序：

1. **ACSD-50336**：修复了在产品重新上架或价格更改时未发送产品警报电子邮件的问题。
1. **ACSD-50367**：修复了在创建不含值的多选客户地址属性时，客户地址导出无法正常工作的问题。
1. **ACSD-49877**：修复了当视频直接链接到远程视频文件而不是流服务时，视频自动播放在移动设备[!DNL Safari]上不起作用的问题。
1. **ACSD-50165**：修复了错误&#x200B;*无法删除该文件。 警告！unlink：从Admin*&#x200B;刷新JS/CSS缓存时没有此类文件或目录。
1. **ACSD-49737**：修复了在信用卡付款失败后优惠券被错误地标记为使用的问题。
1. **ACSD-50814**：修复了管理员用户无法创建贷项通知单的问题。
1. **ACSD-50116**：修复了管理员用户无法为子类别级别3或更低级别创建URL重写的问题。
1. **ACSD-49513**：修复了远程存储同步因0字节文件而失败的问题。
1. **ACSD-46683**：修复了配送价格显示&#x200B;*尚未计算*&#x200B;的问题。
1. **ACSD-49129**：修复了`rest/V1/products/sku/media`产品媒体API响应中未返回内容属性([!UICONTROL base64 image code])的问题。
1. **ACSD-50276**：修复了在创建多选客户属性后店面中无法正常使用客户注册表单的问题。
1. **ACSD-50527**：修复了在保存具有空动态块的页面时发生的错误。
1. **ACSD-49973**：改进通过GraphQL获取捆绑产品的性能。
1. **ACSD-51114**：修复了在启用异步索引后，随机产品从大型目录中消失的问题。 改进大型目录的异步重新索引性能。
1. **B2B-2598**：向`availableStores`、`countries`、`country`、`currency`和`storeConfig`个GraphQL查询添加了缓存功能。

使用左侧的菜单导航到特定的修补程序页面。
