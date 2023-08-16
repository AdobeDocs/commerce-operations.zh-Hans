---
title: 模块更新失败后回滚
description: 解决Adobe Commerce或Magento Open Source升级中出现的模块更新错误问题。
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---

# 模块更新失败后回滚

如果模块更新失败，控制台日志中会显示与以下内容类似的消息：

```terminal
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

在上例中，没有要回滚的组件版本。 请联系组件供应商或尝试自行解决问题。

同时，您可以通过单击以回退到以前的版本 **回滚**，它可以恢复您的数据，即使您以前未备份。
