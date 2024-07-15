---
title: 为响应速度更快的网站优化图像
description: 了解优化图像的步骤，并使用Fastly图像优化来优化Adobe Commerce网站上的响应时间。
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%

---

# 为响应速度更快的网站优化图像

对于云基础架构部署上的Adobe Commerce，可通过在上传图像之前优化图像来缩短站点响应时间。 然后，使用Fastly图像优化来加快图像投放并简化图像源集的维护。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md)，共：

云基础架构上的Adobe Commerce


## 优化和压缩图像

在将图像上传到Commerce站点之前，请优化和压缩图像以在性能和观看质量之间取得平衡。 这有助于增加空间并减少页面加载时间。

- PNG格式为具有大面积纯色区域的图像提供较小大小的图像。

- JPEG格式可为所有其他图像类型提供较小大小的图像。 使用最高的压缩率（无明显降级）。 通常为60%到80%。

## 启用和配置Fastly图像优化

在为Adobe Commerce Cloud项目设置Fastly服务后，请参阅[Fastly图像优化](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html)以获取有关启用和配置图像优化的说明。

## 其他信息

- [设置Fastly](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [优化不佳的图像可能导致性能问题](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
