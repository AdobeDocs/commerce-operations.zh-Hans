---
title: 概述： [!DNL Quality Patches Tool] (QPT) v1.1.71
description: 此子部分详细描述了 [!DNL Quality Patches Tool] (QPT) v1.1.71中提供的修补程序所修复的问题。
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 4660942d90435eaeb6960206c29733bed6453b6a
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# 概述：[!DNL Quality Patches Tool] (QPT) v1.1.71

此子部分详细描述了[!DNL Quality Patches Tool] (QPT) v1.1.71中提供的修补程序所修复的问题。

QPT v1.1.71包含以下修补程序：


* **ACSD-60624**： [!DNL Page Builder]中图像、横幅和滑块部分中的空内容无法上传图像
* **ACSD-67089**： `inventory/export-stock-salable-qty` API中的分页问题，错误地将`total_count`限制为页面大小。
* **ACSD-67093**：使用日期范围筛选器通过[!DNL GraphQL]检索订单时返回错误结果。
* **ACSD-67459**：无法导入描述长度超过65,536个字符的产品。
* **ACSD-67603**：启用图像包含的产品的Sitemap生成处理时间较长
* **ACSD-67643**：在含有大量嵌套类别的环境中进行计划更新期间，会创建重复条目。
* **ACSD-67652**：在[!DNL GraphQL]调用中，即使子产品和父产品有库存，捆绑包产品状态也会作为缺货而返回。
* **ACSD-67904**：如果城市名称包含数字(0-9)、&amp;符号(&amp;)、句点(.)或圆括号()，则无法下达订单。

使用左侧的菜单导航到特定的修补程序页面。
