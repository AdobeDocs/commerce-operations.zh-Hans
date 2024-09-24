---
title: 使用Quality Patches Tool检查Adobe Commerce问题的修补程序
description: 本文概述了Quality Patches Tool (QPT) ，并提供了资源链接，这些资源说明了如何使用QPT。
feature: Tools and External Services
role: Admin
source-git-commit: 6f311fc4c20caca8b98d4c3c06642e5f61dc614f
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# 使用Quality Patches Tool检查Adobe Commerce问题的修补程序

本文概述了Quality Patches Tool (QPT) ，并提供了资源链接，这些资源说明了如何使用QPT。

## 受影响的产品和版本

* Adobe Commerce内部部署，所有[支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* 云基础架构上的Adobe Commerce，所有[支持的版本](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## 什么是质量修补程序工具

[Quality Patches Tool](https://github.com/magento/quality-patches) (QPT)是由Adobe和Magento Open Source团体开发的单个修补程序。

它允许您：

* 将优质补丁程序应用到包
* 还原以前应用的修补程序
* 查看有关适用于已安装的Adobe Commerce版本的质量修补程序的一般信息。

下面是状态表的示例，您可以获得该表以查看可用的修补程序：

![Magento修补程序列表](/help/assets/tools/status_table.png)

该工具旨在让您能够自助提供修补程序，以解决在Adobe Commerce中可能遇到的问题，或轻松应用Adobe Commerce支持人员建议的修补程序。

>[!NOTE]
>
>QPT仅适用于高质量的修补程序。 [Magento安全中心](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview)中有安全修补程序。

## Quality Patches Tool中提供的修补程序

有关可用修补程序的列表，请参阅开发人员文档中的[Quality Patches Tool](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)。

## 如何安装和使用Quality Patches工具

对于云基础架构上的Adobe Commerce内部部署和Adobe Commerce，安装和使用命令有所不同，因为对于云，QPT包包含在ece-tools包中。

### 如何在Adobe Commerce内部部署安装和使用QPT

有关如何安装和使用QPT来应用和还原修补程序的详细信息，请参阅我们的开发人员文档中的[软件更新指南>修补](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage)。

### 如何在云基础架构上安装和使用QPT for Adobe Commerce

请参阅我们的开发人员文档中的[Cloud for Adobe Commerce >应用修补程序](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)，了解有关如何在Adobe Commerce上安装和使用QPT来应用和还原修补程序的详细信息。

## 相关阅读

* 开发人员文档中的[Quality Patches Tool发行说明](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/release-notes)。
* [如何应用支持知识库中Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento)提供的编辑器修补程序。
