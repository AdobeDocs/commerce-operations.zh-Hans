---
title: 模块更新失败后回滚
description: 解决Adobe Commerce升级中遇到的模块更新错误问题。
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# 模块更新失败后回滚

如果模块更新失败，控制台日志中会显示与以下内容类似的消息：

```
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

在上例中，没有要回滚的组件版本。 请联系组件供应商或尝试自行解决问题。

同时，您可以通过单击&#x200B;**回滚**&#x200B;来回滚到以前的版本，这样即使您以前没有备份，也可以恢复您的数据。
