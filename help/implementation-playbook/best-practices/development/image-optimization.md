---
title: 为响应速度更快的网站优化图像
description: 了解优化图像的步骤，并使用Fastly图像优化来优化Adobe Commerce网站上的响应时间。
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%
---
# 为响应速度更快的网站优化图像

对于云基础架构部署上的Adobe Commerce，可通过在上传图像之前优化图像来缩短站点响应时间。 然后，使用Fastly图像优化来加快图像投放并简化图像源集的维护。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md)，共：

云基础架构上的Adobe Commerce


## 优化和压缩图像

在将图像上传到Commerce站点之前，请优化和压缩图像以在性能和观看质量之间取得平衡。 这有助于增加空间并减少页面加载时间。

- PNG格式为具有大面积纯色区域的图像提供较小大小的图像。

- JPEG格式为所有其他图像类型提供较小大小的图像。 使用最高的压缩率（无明显降级）。 通常为60%到80%。

## 启用和配置Fastly图像优化

为Adobe Commerce Cloud项目设置Fastly服务后，请参阅[Fastly图像优化](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/cdn/fastly-image-optimization)以获取有关启用和配置图像优化的说明。

## 其他信息

- [设置Fastly](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)
- [优化不佳的图像可能导致性能问题](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow)
