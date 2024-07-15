---
title: 配置消息使用者
description: 按照以下步骤配置Adobe Commerce消息队列使用者的行为。
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# 配置消息使用者

运行此命令之前，必须执行以下&#x200B;*或*&#x200B;操作，必须[安装应用程序](../advanced.md)：

* [创建或更新部署配置](deployment.md)
* [创建数据库模式](database.md)

## 配置使用者行为

通过在设置函数中发送键/值对，可配置消费者行为：

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### 参数描述

{{$include /help/_includes/cli-consumers.md}}
