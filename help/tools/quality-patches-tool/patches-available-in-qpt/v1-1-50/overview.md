---
title: '概述： [!DNL Quality Patches Tool] (QPT) v1.1.50'
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.50中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.50

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.50中提供的修补程序所修复的问题。

QPT v1.1.50包含以下修补程序：

1. **ACSD-59280**：修复了在安装2.4.4-pX版本时出现错误&#x200B;*调用未定义的方法ReflectionUnionType：：getName()*&#x200B;的问题。
1. **ACSD-45049**：修复了客户&#x200B;*[!UICONTROL Is required]*&#x200B;属性设置无法按照Admin中的网站范围正确工作的问题。
1. **ACSD-46938**：修复了`setup:upgrade`期间重新创建数据库触发器的性能问题。
1. **ACSD-48210**：修复了在特定存储视图中更新&#x200B;*[!UICONTROL website scope]*&#x200B;属性会覆盖全局范围中的属性值的问题。
1. **ACSD-54887**：修复了在启用&#x200B;*[!UICONTROL Persistent Shopping Cart]*&#x200B;后客户会话过期后客户购物车被清空的问题。
1. **ACSD-58141**：修复了在启用[!UICONTROL L2 Redis cache]且客户从Admin中更新的情况下，在已登录客户的店面区域上重新生成`PHPSESSID`的POST请求的问题。
1. **ACSD-58352**：修复了在请求标头中指定非默认商店视图时，通过GraphQL API返回默认商店视图的返回属性标签的问题。
1. **ACSD-58442**：修复了宽度为&#x200B;*768px*&#x200B;的设备被视为移动设备，导致菜单和标题加载到移动视图而非桌面的问题。
1. **ACSD-58790**：修复了[!DNL Chrome]上移动设备视图中的产品详细信息页面图像的&#x200B;*缩放夹入*&#x200B;功能。
1. **ACSD-59036**：修复了在加载上下限均等于&#x200B;*$0*&#x200B;的产品价格时发生的异常。
1. **ACSD-59229**：修复了由于请求中[!UICONTROL X-Magento-Vary]的旧值而导致客户组相关信息保存在错误区段中的问题。
1. **ACSD-59378**：修复了在导入期间存储级别URL重写被错误更新的问题。
1. **ACSD-59514**：修复了具有[!DNL Page Builder]的管理员区域中的表单抛出&#x200B;*[!DNL Page Builder]5秒后未释放锁定的问题。提交表单后，浏览器控制台中出现*&#x200B;错误，无法保存更改。
1. **ACSD-60303**：修复了在启用HTML缩小功能后无法向管理员下达订单的问题。
1. **ACSD-60441**：修复了在使用从后端生成的集成访问令牌时通过`V1/customers REST API`端点更新客户的问题。

使用左侧的菜单导航到特定的修补程序页面。
