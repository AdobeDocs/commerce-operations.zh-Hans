---
title: 配置消息使用者
description: 请按照以下步骤配置Adobe Commerce或Magento Open Source消息队列使用者的行为。
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---


# 配置消息使用者

运行此命令之前，必须执行以下操作 *或* 您必须 [安装应用程序](../advanced.md):

* [创建或更新部署配置](deployment.md)
* [创建数据库模式](database.md)

## 配置消费者行为

通过在设置函数中发送键/值对，可完成配置消费者行为：

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### 参数描述

{{$include /help/_includes/cli-consumers.md}}
