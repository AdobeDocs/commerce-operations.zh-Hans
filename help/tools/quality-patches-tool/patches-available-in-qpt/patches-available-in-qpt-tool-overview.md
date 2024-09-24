---
title: QPT工具中提供的修补程序概述
description: 本文概述了 [!DNL Quality Patches Tool] (QPT)，并提供了资源链接，以说明如何使用QPT。
feature: Support, Tools and External Services
role: Admin
source-git-commit: 6f311fc4c20caca8b98d4c3c06642e5f61dc614f
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# QPT工具中提供的修补程序概述

本文概述了[!DNL Quality Patches Tool] (QPT)，并提供了资源链接，以说明如何使用QPT。

## 受影响的产品和版本

* Adobe Commerce内部部署，所有[支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* 云基础架构上的Adobe Commerce，所有[支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 什么是质量修补程序工具？

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) (QPT)是一种允许您应用由Adobe和Magento Open Source团体开发的单个质量修补程序的工具。

它允许您：

* 将优质补丁程序应用到包
* 还原以前应用的修补程序
* 查看有关适用于已安装的Adobe Commerce版本的质量修补程序的一般信息。

下面是状态表的示例，您可以获得该表以查看可用的修补程序：

![Magento修补程序列表](/help/assets/tools/status_table.png)

该工具旨在让您能够自助提供修补程序，以解决在Adobe Commerce中可能遇到的问题，或轻松应用Adobe Commerce支持人员建议的修补程序。

>[!NOTE]
>
>QPT仅适用于高质量的修补程序。 在[Adobe Commerce和Magento Open Source的发行说明](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/overview.html)中提供了安全修补程序。

## [!DNL Quality Patches Tool]中可用的修补程序

在Adobe Commerce支持知识库的此部分中，您将找到按QPT修补程序解决的问题按QPT发行版本分组的详细说明。
您还可以查看可用QPT修补程序的列表，并使用我们的支持知识库中[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)上动态生成的表按组件进行筛选。

## 如何安装和使用[!DNL Quality Patches Tool]

对于云基础架构上的Adobe Commerce内部部署和Adobe Commerce，安装和使用命令有所不同，因为对于云，QPT包包含在ece-tools包中。

### 如何在Adobe Commerce内部部署安装和使用QPT

有关如何安装和使用QPT以应用和还原修补程序的详细信息，请参阅我们的开发人员文档中的[Commerce >工具>用法](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html)。

### 如何在云基础架构上安装和使用QPT for Adobe Commerce

请参阅我们的开发人员文档中的[Commerce on Cloud Infrastructure Guide > Apply patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)，了解有关如何在Adobe Commerce on Cloud Infrastructure上安装和使用QPT来应用和还原修补程序的详细信息。

## 相关阅读

* [[!DNL Quality Patches Tool] 发行说明](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html)（位于我们的开发人员文档中）。
