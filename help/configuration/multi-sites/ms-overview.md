---
title: 多个网站或商店
description: 了解如何启动多个网站或使用不同的选项、域和内容实施商店视图。
exl-id: 724d75d9-13fc-40f9-951a-69aa407adb6f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# 多个网站或商店

通过单个Adobe Commerce软件实例，您可以启动多个使用不同属性和内容的网站或商店视图，例如：

- 默认语言
- 域名
- 类别
- 产品
- 货币

此灵活的解决方案允许一个Commerce代码库和管理员管理和显示不同的商店。 您可以在“管理员”中配置网站、商店和商店视图。 在虚拟主机中使用某些变量，以使用这些网站或商店视图启动Commerce应用程序。

典型用法是在不同域中设置具有不同选项的商店。 例如，您可以在一个域上拥有一组类别和产品，在单独的域上拥有另一组类别和产品，并使用不同的语言。

您可以在Commerce管理员中配置网站、商店和商店视图。 使用 `MAGE_RUN_TYPE` 和 `MAGE_RUN_CODE` 变量来启动使用这些网站或商店视图的Commerce应用程序。

请考虑以下术语：

- **网站** — 是站点、投放方法、支付方法等的顶级容器。 要创建不共享购物车、投放方法或其他的完全独立的网站，您必须创建单独的网站。

  网站客户帐户可以在单个Commerce实例内的多个网站之间共享。 网站至少包含一家商店。 目录价格应在网站层面进行管理。

- **存储** — 包含在网站中。 反过来，商店至少包含一家 *商店视图*.

  多个商店可以共享购物车、用户会话、支付网关等，但它们具有独立的目录结构和目录价格。

  无法在存储级别管理目录数量（库存）。 库存仅在网站或全球级别进行管理。

  商店视图会更改页面的显示方式，通常用于显示具有不同布局或语言的商店。 您可以为每个商店视图管理不同的货币。

  每个网站和每个商店视图必须具有唯一标识符。 此标识符是使用 `MAGE_RUN_TYPE` 和 `MAGE_RUN_CODE` 变量如下所示：

- `MAGE_RUN_TYPE` 可以是 `store` 或 `website`

   - 使用 `website` 在您的店面中加载网站。
   - 使用 `store` 以载入店面中的任何商店视图。

- `MAGE_RUN_CODE` 是与对应的独特网站或商店视图代码 `MAGE_RUN_TYPE`

以下是必须执行的任务摘要：

1. [在“管理员”中设置网站、商店和商店视图。](ms-admin.md)
1. 创建虚拟主机以加载多个网站，或为每个Commerce网站或商店视图加载一个虚拟主机，以允许为每个商店使用特定指令。
1. 传递值 `MAGE_RUN_TYPE` 和 `MAGE_RUN_CODE` 到Web服务器。
