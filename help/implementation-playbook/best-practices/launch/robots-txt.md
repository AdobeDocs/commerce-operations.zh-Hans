---
title: 配置Web爬网程序的最佳实践
description: 了解如何使用“robots.txt”和“sitemap.xml”文件，将有关Adobe Commerce网站的说明传递给Web爬网程序。
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---


# 配置Web爬网程序的最佳实践

本文提供了在Adobe Commerce中使用`robots.txt`和`sitemap.xml`文件的最佳实践，包括配置和安全性。 这些文件指示Web爬网程序（通常是搜索引擎机器人）如何爬网网站上的页面。 配置这些文件可以提高网站性能和优化搜索引擎。

>[!NOTE]
>
>这些最佳实践仅适用于使用本机Adobe Commerce店面的项目。 它们不适用于使用其他店面解决方案(例如，Adobe Experience Manager、headless)的Adobe Commerce项目。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md)，共：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 云基础架构上的Adobe Commerce

默认的Adobe Commerce项目包含一个层级，其中包括单个网站、商店和商店视图。 对于更复杂的实施，您可以为&#x200B;_多站点_&#x200B;店面创建其他网站、商店和商店视图。

### 单站点店面

为单站点店面配置`robots.txt`和`sitemap.xml`文件时，请遵循以下最佳实践：

- 确保您的项目使用的是[`ece-tools`](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package)版本2002.0.12或更高版本。
- 使用Admin应用程序将内容添加到`robots.txt`文件。

  >[!TIP]
  >
  >在`robots.txt`上查看为您的商店自动生成的`<domain.your.project>/robots.txt`文件。

- 使用管理员应用程序生成`sitemap.xml`文件。

  >[!IMPORTANT]
  >
  >由于Adobe Commerce上的云基础架构项目采用只读文件系统，因此您必须指定`pub/media`路径才能生成文件。

- 使用自定义Fastly VCL代码片段，将两个文件的从站点根目录重定向到`pub/media/`位置：

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- 通过在Web浏览器中查看文件来测试重定向。 例如，`<domain.your.project>/robots.txt`和`<domain.your.project>/sitemap.xml`。 确保您使用的是为其配置重定向的根路径，而不是其他路径。

>[!INFO]
>
>有关详细说明，请参阅[添加站点地图和搜索引擎机器人](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap)。


### 多站点店面

您可以在云基础架构上通过一次实施Adobe Commerce来设置和运行多个商店。 请参阅[设置多个网站或商店](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites)。

为`robots.txt`单站点店面`sitemap.xml`配置[和](#single-site-storefronts)文件的相同最佳实践适用于具有两个重要区别的多站点店面：

- 确保`robots.txt`和`sitemap.xml`文件名包含相应站点的名称。 例如：
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- 使用稍作修改的自定义Fastly VCL代码片段将两个文件从站点的根重定向到站点中的`pub/media`位置：

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
  }
  ```

## Adobe Commerce内部部署

使用管理员应用程序配置`robots.txt`和`sitemap.xml`文件，以防止机器人扫描和索引不必要的内容（请参阅[搜索引擎机器人](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)）。

>[!TIP]
>
>对于内部部署，文件编写位置取决于您安装Adobe Commerce的方式。 将文件写入`/path/to/commerce/pub/media/`或`/path/to/commerce/media`，以适合您的安装为准。

## 安全性

不要在`robots.txt`文件中公开您的管理员路径。 暴露管理员路径是网站黑客攻击和潜在数据丢失的漏洞。 从`robots.txt`文件中删除管理员路径。

有关编辑`robots.txt`文件并删除管理员路径所有条目的步骤，请参阅[营销用户指南> SEO和搜索>搜索引擎机器人](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)。

>[!TIP]
>
>如果需要帮助，请[提交Adobe Commerce支持票证](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket)。

## 其他信息

- [了解网站、商店和商店视图](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [添加网站](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [使用Fastly阻止Adobe Commerce网站的恶意流量](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking)
- [robots.txt在云基础架构2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)上的Adobe Commerce中出现404错误
