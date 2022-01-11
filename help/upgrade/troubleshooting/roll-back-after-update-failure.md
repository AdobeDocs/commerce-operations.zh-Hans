---
title: 模块更新失败后回滚
description: 在遇到模块更新错误后，对Adobe Commerce或Magento Open Source升级进行故障诊断。
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---


# 模块更新失败后回滚

如果您的模块更新失败，控制台日志中将显示与以下类似的消息：

```terminal
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

在上例中，没有要回滚到的组件版本。 请联系组件供应商或尝试自行解决问题。

同时，您可以通过单击 **回滚**，即使您之前未备份，也会恢复数据。
