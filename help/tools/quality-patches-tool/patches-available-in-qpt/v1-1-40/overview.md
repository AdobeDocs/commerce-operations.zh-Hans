---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.40
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.40中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
exl-id: fd0caa46-834a-4553-bb59-e4c968c59c15
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.40

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.40中提供的修补程序所修复的问题。

QPT v1.1.40包含以下修补程序：

1. **ACSD-54680**：修复了无法处理为具有多个已分配来源的产品提交的B2B报价的问题。
1. **ACSD-54040**：修复了在启用B2B模块时，订单详细信息中&#x200B;*[!UICONTROL Created]*&#x200B;字段为空的问题。
1. **ACSD-54319**：修复了&#x200B;*[!UICONTROL Product in Cart]*&#x200B;报表中产品价格为零的问题。
1. **ACSD-53378**：为拥有大地址簿的客户缩短结帐页面加载时间。
1. **ACSD-52657**：修复了在使用子域的辅助存储上未更新minicart的问题。
1. **ACSD-53414**：修复了受限管理员用户在其权限范围之外查看CMS页面的问题。
1. **ACSD-54472**：修复了被拒绝公司的客户仍然可以进行身份验证，被阻止和被拒绝公司的客户仍然可以下订单的问题。 该修补程序添加了对GraphQL端点的其他验证。
1. **ACSD-52801**：添加在GraphQL中搜索产品时进行部分匹配的选项。
1. **ACSD-55004**：修复了在上传大于`php.ini`中配置的值的导入文件时，验证器崩溃的问题。
1. **ACSD-54989**：修复了当&#x200B;*[!UICONTROL Enable Purchase Orders]*&#x200B;设置为&#x200B;*[!UICONTROL Yes]*&#x200B;且&#x200B;*[!UICONTROL Purchase Order]*&#x200B;设置为&#x200B;*[!UICONTROL No]*&#x200B;时，公司管理员无法下订单的问题。
1. **ACSD-54007**：修复了导入客户数据时出现错误&#x200B;*“未定义数组键“_scope”*。
1. **ACSD-55031**：修复了在编译期间&#x200B;*类型“混合”不能为nullable*&#x200B;错误。
1. **ACSD-54961**：修复了受限管理员用户无法批量更新&#x200B;*产品评论*&#x200B;状态的问题。

使用左侧的菜单导航到特定的修补程序页面。
