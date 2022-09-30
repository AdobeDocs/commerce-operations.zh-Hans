---
title: 发布策略
description: 了解不同类型的Adobe Commerce版本，包括次要、修补程序、安全修补程序、功能、修补程序、单个修补程序和自定义修补程序。
source-git-commit: 79f36e3728e6bc436e8093bd4051143a48e681d6
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 0%

---


# Adobe Commerce发布政策

Adobe Commerce和Magento Open Source使用 [语义版本控制](https://semver.org/) 在单个模块级别(例如 `magento/framework 101.1.1`)，但不适用于营销版本号。 例如：

- **主要版本**—2
- **次要版本**—2.4
- **PATCH版本**—2.4.1
   - **安全修补程序版本**—2.4.1-p1
      - 安全错误修复
      - 安全性增强
- **功能发布**
- **修补程序**
- **单个修补程序**
- **自定义修补程序**

## 次要版本

以下准则适用于次要版本：

- 可能会发生重大变化；为Adobe Commerce 2.2.x编写的代码可能不再适用于Adobe Commerce 2.3.x。例如，次要版本可以引入对主要系统要求和依赖项（如PHP）的支持。
- 模块版本可能有所不同。 例如，某些模块更改在新修补程序中引入，而其他模块更改则在次要版本中引入。
- 次要版本可能包含一些新功能，在升级过程中，您或您的解决方案合作伙伴可能需要进行额外的工作以确保兼容性。
- 次要版本可能包含针对安全和质量问题的修复。

## PATCH版本

修补程序版本主要侧重于提供安全性、性能、合规性和高优先级质量修复，以帮助您的网站保持最高性能。

以下准则适用于修补程序版本：

- 最新支持的次要版本提供了完整的功能质量修复和增强功能。
- 可以避免可能破坏扩展或代码兼容性的更改。 例如，为版本2.2.0编写的代码仍应适用于版本2.2.7。
- 在特殊情况下，可能会发布中断更改或其他补丁或修补程序，以解决安全性或合规性问题以及高影响质量问题。 在模块级别上，这主要是PATCH级别的更改；有时会进行次要级别的更改。

## 安全修补程序版本

**安全错误修复**:一种软件代码更改，可解决已识别的安全问题，并在受影响的产品区域中提供预期结果。 这些修复通常向后兼容。

**安全增强功能**:软件改进或配置更改，以主动提高应用程序内的安全性。 这些安全增强有助于解决安全风险，这些风险会影响Adobe Commerce应用程序的安全态势，但可能是后向不兼容的。

使用安全修补程序版本，您无需应用季度修补程序版本中包含的其他质量修补程序和增强功能，即可更加安全地保护网站。 安全修补程序版本将附加“ — pN”，其中N是以1开头的增量修补程序版本（例如，2.3.5-p1）。 安全修补程序版本还可以包含解决影响Adobe Commerce应用程序的关键问题所需的修补程序。

每个安全修补程序版本都基于之前的完整修补程序版本。 它包含先前修补程序版本中的质量和安全修补程序，以及先前完整修补程序版本与安全修补程序版本之间创建的安全修补程序。

随着我们 [新的发布策略和更新的生命周期策略](https://business.adobe.com/blog/how-to/accelerating-innovation-through-simplified-release-strategy) (9/16/2021)，我们会根据安全修补程序版本是否适用于受支持的最新次要版本或仍受支持的先前次要版本行的一部分，来区分我们的安全修补程序版本：

- **最新支持的次要版本的安全修补程序版本**:

   - 最新支持的次要版本(当前为Adobe Commerce 2.4)的安全修补程序版本包括：

      - 自上一个完整修补程序版本以来创建的安全错误修复。

      - 这些安全修补程序版本还可以包含解决可能影响Adobe Commerce应用程序的关键问题所需的修补程序。
   - 最新支持的次要版本(当前为Adobe Commerce 2.4)的安全修补程序版本通常不包含安全增强功能。 相反，对于最新支持的次要版本，这些修补程序都包含在完整的修补程序版本中。


- **支持的以前次要版本的安全修补程序版本**:

   - 以前仍受支持的次要版本(当前为Adobe Commerce 2.3)的安全修补程序版本包括：

      - 自上一个修补程序或安全修补程序版本以来创建的安全错误修复，以及新的安全增强功能。

      - 这些安全修补程序版本还可以包含解决影响Adobe Commerce应用程序的关键问题所需的修补程序。

      |  | 安全错误 | 安全增强功能 |
      |--------------------------------------------------------------------------------|--------------|----------------------|
      | 最新支持的次要版本的安全修补程序版本（当前为2.4） | X |  |
      | 以前支持的次要版本的安全修补程序版本（当前为2.3） | X | X |


有关安全版本的常规信息，请参阅 [引入新的仅安全修补程序版本](https://community.magento.com:443/t5/Magento-DevBlog/Introducing-the-New-Security-Patch-Release/ba-p/141287). 有关下载和应用安全修补程序的说明，请参阅 [快速入门安装](../installation/composer.md).

## 功能发布

功能版本包含作为独立服务提供的新功能和功能更新，这些功能和修补程序版本是分开提供的。 示例包括产品Recommendations和实时搜索等服务、PWA Studio和Inventory management(MSI)等独立模块，以及云服务和基础架构的更新。

## 修补程序

修补程序是包含高影响安全性或高质量修补程序的修补程序，例如针对零日漏洞的修复，这些修补程序会影响许多商家。 Adobe发布适用于Adobe Commerce版本的修补程序，这些修补程序仍受支持，并会根据需要受到关键安全或质量问题的影响。 修补程序发布到 [“已知问题”部分](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) 知识库。 这些修复包含在下一个计划的修补程序版本中。

>[!NOTE]
>
>修补程序可以包含向后不兼容的更改。

## 单个修补程序

单个修补程序包含针对特定问题的低影响质量修补程序。 这些修复已应用于支持的次要版本Adobe Commerce。 Adobe根据我们的 [软件生命周期策略](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>单个修补程序不包含向后不兼容的更改。

## 自定义修补程序

由非Adobe人员创建，用于修复问题或修改Adobe Commerce代码，具体原因各不相同。 自定义修补程序通过 [质量补丁工具](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## 相关主题

- [商务升级周期的计划和预算编制](https://magento.com/sites/default/files8/2019-08/Magento-Release-Cycle-Infosheet_Aug_2019.pdf)
- [版本控制](https://developer.adobe.com/commerce/php/development/versioning/)
- [即将发行的版本](schedule.md)
- [软件生命周期策略](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
