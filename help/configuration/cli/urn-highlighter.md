---
title: URN荧光笔
description: 了解如何在IDE中为Adobe Commerce开发设置URN高亮显示。 发现XSD架构配置和开发优化。
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# URN荧光笔概述

{{file-system-owner}}

Commerce代码以[统一资源名称(URN)](https://www.ietf.org/rfc/rfc2141.txt)的形式引用所有XSD架构。 如果您正在开发代码并需要引用XSD，则此命令将配置您的集成开发人员环境(IDE)以识别和突出显示URN。 这样可以让开发更加容易。

缺省情况下，诸如PhpStorm之类的IDE未配置为识别URN，因此，它们会以红色文本显示，如下所示：

![PhpStorm未配置为识别URN](../../assets/configuration/urn-before.png)

`bin/magento dev:urn-catalog:generate`命令使您的IDE（当前仅支持PhpStorm和Visual Studio代码）能够识别并高亮显示如下所示的URN：

![启用IDE以识别URN](../../assets/configuration/urn-after.png)

具体而言，此命令创建以下PhpStorm配置：

![PhpStorm配置示例](../../assets/configuration/urn-settings.png)

## 配置IDE

目前，仅支持PhpStorm和Visual Studio代码。

命令语法：

```bash
bin/magento dev:urn-catalog:generate <path>
```

其中`<path>`是PhpStorm `misc.xml`文件的路径，该文件位于项目根目录的相对位置。 通常，`<path>`是`.idea/misc.xml`。

>[!INFO]
>
>要使您的“架构和DTD”保持最新，请在每次添加、修改或删除包含`dev:urn-catalog:generate`文件的Commerce 2模块时运行`*.xsd`命令。
