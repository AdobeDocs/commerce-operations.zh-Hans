---
title: 配置“robots.txt”和“sitemap.xml”文件的最佳实践
description: 了解如何将有关您的Adobe Commerce网站的说明传递给Web爬网程序。
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---


# 配置最佳实践 `robots.txt` 和 `sitemap.xml` 文件

本文提供了使用 `robots.txt` 和 `sitemap.xml` 文件，包括配置和安全性。 这些文件指导Web机器人（通常是搜索引擎机器人）如何在网站上爬网页面。 配置这些文件可以提高网站性能并优化搜索引擎。

>[!NOTE]
>
>这些最佳实践仅适用于使用本机Adobe Commerce店面的项目。 它们不适用于使用其他店面解决方案(例如Adobe Experience Manager、无头)的Adobe Commerce项目。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 共：

- Adobe Commerce云基础架构
- Adobe Commerce内部

## Adobe Commerce云基础架构

默认的Adobe Commerce项目包含包含单个网站、商店和商店视图的层次结构。 对于更复杂的实施，您可以为 _多站点_ 店面。

### 单站点店面

在配置 `robots.txt` 和 `sitemap.xml` 单站点店面的文件：

- 确保您的项目正在使用 [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) 版本2002.0.12或更高版本。
- 使用管理应用程序将内容添加到 `robots.txt` 文件。

   >[!TIP]
   >
   >查看自动生成的 `robots.txt` 的 `<domain.your.project>/robots.txt`.

- 使用管理应用程序生成 `sitemap.xml` 文件。

   >[!IMPORTANT]
   >
   >由于云基础架构项目上的Adobe Commerce上的只读文件系统，您必须指定 `pub/media` 路径。

- 使用自定义的Fastly VCL代码片段将从站点的根目录重定向到 `pub/media/` 两个文件的位置：

   ```vcl
   {
     "name": "sitemaprobots_rewrite",
     "dynamic": "0",
     "type": "recv",
     "priority": "90",
     "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
   }
   ```

- 通过在Web浏览器中查看文件来测试重定向。 例如， `<domain.your.project>/robots.txt` 和 `<domain.your.project>/sitemap.xml`. 确保您使用的是为其配置重定向的根路径，而不是其他路径。

>[!INFO]
>
>请参阅 [添加站点地图和搜索引擎机器人](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) 以了解详细说明。


### 多站点店面

您可以在云基础架构上通过单次实施Adobe Commerce来设置和运行多个商店。 请参阅 [设置多个网站或商店](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

配置的最佳实践相同 `robots.txt` 和 `sitemap.xml` 文件 [单站点店面](#single-site-storefronts) 适用于具有两个重要差异的多站点店面：

- 确保 `robots.txt` 和 `sitemap.xml` 文件名包含相应站点的名称。 例如：
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- 使用稍微修改的自定义Fast VCL代码片段将从网站的根目录重定向到 `pub/media` 两个文件在您网站中的位置：

   ```vcl
   {
     "name": "sitemaprobots_rewrite",
     "dynamic": "0",
     "type": "recv",
     "priority": "90",
     "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
   }
   ```

## Adobe Commerce内部

使用管理应用程序配置 `robots.txt` 和 `sitemap.xml` 防止机器人扫描和索引不必要内容的文件(请参阅 [搜索引擎机器人](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots))。

>[!TIP]
>
>对于内部部署，您在何处写入文件取决于您安装Adobe Commerce的方式。 将文件写入 `/path/to/commerce/pub/media/` 或 `/path/to/commerce/media`，以适合您的安装的方式。

## 安全性

请勿在 `robots.txt` 文件。 暴露管理路径是站点黑客攻击和潜在数据丢失的漏洞。 从 `robots.txt` 文件。

有关编辑 `robots.txt` 文件并删除管理路径的所有条目，请参阅 [营销用户指南> SEO和搜索>搜索引擎机器人](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>如果你需要帮助， [提交Adobe Commerce支持票证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.md#submit-ticket).

## 其他信息

- [了解网站、商店和商店视图](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [添加网站](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [使用Fastly阻止您的Adobe Commerce网站的恶意流量](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt在云基础架构2.3.x上的Adobe Commerce中出现404错误](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.md)
