---
title: 优化图像以提供响应更快的网站
description: 了解优化图像和使用Fastly图像优化来优化Adobe Commerce网站响应时间的步骤。
role: Developer, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# 优化图像以提供响应更快的网站

对于云基础架构部署中的Adobe Commerce，请在上传图像之前优化图像，以缩短站点响应时间。 然后，利用Fastly图像优化技术来加快图像传输速度，简化图像源集的维护。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

Adobe Commerce云基础架构


## 优化和压缩图像

在将图像上传到您的商务网站之前，请优化并压缩图像，以在性能与查看质量之间取得平衡。 这有助于增加空间并缩短页面加载时间。

- PNG格式可为具有较大纯色区域的图像提供较小大小的图像。

- JPEG格式可为所有其他图像类型提供较小的图像大小。 使用最高的压缩（没有明显的降级）。 通常为60%到80%。

## 启用并配置Fastly图像优化

为Adobe Commerce Cloud项目设置Fastly服务后，请参阅 [快速图像优化](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) 以了解有关启用和配置图像优化的说明。

## 其他信息

- [设置Fastly](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [优化不当的图像可能会导致性能问题](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
