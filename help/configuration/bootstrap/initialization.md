---
title: 应用程序初始化和引导
description: 阅读Commerce应用程序的初始化和引导逻辑。
feature: Configuration, Install, Media
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---

# 初始化和引导概述

要运行Commerce应用程序，请在[pub/index.php][index]中实现以下操作：

- 包括[app/bootstrap.php][bootinitial]，它执行基本初始化例程，如错误处理、初始化自动加载程序、设置性能分析选项和设置默认时区。
- 创建[\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->的实例
- 创建Commerce应用程序实例： [\Magento\Framework\AppInterface][app-face]
- 运行Commerce

## Bootstrap运行逻辑

[引导对象][bootinitial]使用以下算法运行Commerce应用程序：

1. 初始化错误处理程序。
1. 创建随处使用且受环境影响的[对象管理器][object]和基本共享服务。 环境参数将被正确地插入这些对象中。
1. 声明维护模式为&#x200B;_未启用_；否则，将终止。
1. 声明已安装Commerce应用程序；否则，将终止。
1. 启动Commerce应用程序。

   在应用程序启动期间任何未捕获的异常都会自动通过`catchException()`方法传递回Commerce，您可以使用该方法处理该异常。 后者必须返回`true`或`false`：

   - 如果`true`： Commerce已成功处理异常。 没必要做别的事。
   - 如果`false`：（或任何其他空结果）Commerce未处理异常。 bootstrap对象执行缺省的异常处理子例程。

1. 发送由应用程序对象提供的响应。

   >[!INFO]
   >
   >断言已安装Commerce应用程序且未处于维护模式是`\Magento\Framework\App\Bootstrap`类的默认行为。 创建引导对象时，可以使用入口点脚本对其进行修改。

   修改引导数据库对象的入口点脚本示例：

   ```php
   <?php
   use Magento\Framework\App\Bootstrap;
   require __DIR__ . '/app/bootstrap.php';
   
   $params = $_SERVER;
   $params[Bootstrap::PARAM_REQUIRE_MAINTENANCE] = true; // default false
   $params[Bootstrap::PARAM_REQUIRE_IS_INSTALLED] = false; // default true
   $bootstrap = Bootstrap::create(BP, $params);
   
   /** @var \Magento\Framework\App\Http $app */
   $app = $bootstrap->createApplication('Magento\Framework\App\Http');
   $bootstrap->run($app);
   ```

## 默认异常处理

bootstrap对象指定Commerce应用程序如何处理未捕获的异常，如下所示：

- 在[开发人员模式](../bootstrap/application-modes.md#developer-mode)中，按原样显示异常。
- 在任何其他模式下，会尝试记录异常并显示一般错误消息。
- 终止Commerce，错误代码为`1`

## 入口点应用程序

我们有以下入口点应用程序(即Commerce定义的应用程序，由Web服务器用作目录索引)：

### HTTP入口点

[\Magento\Framework\App\Http][http]的工作方式如下：

1. 确定[应用程序区域](https://developer.adobe.com/commerce/php/architecture/modules/areas/)。
1. 启动前端控制器和路由系统，以便查找并执行控制器操作。
1. 使用HTTP响应对象返回从控制器操作获得的结果。
1. 错误处理（按以下优先级顺序）：

   1. 如果您使用[开发人员模式](../bootstrap/application-modes.md#developer-mode)：
      - 如果未安装Commerce应用程序，请重定向到“安装向导”。
      - 如果已安装Commerce应用程序，则显示错误和HTTP状态代码500（内部服务器错误）。
   1. 如果Commerce应用程序处于维护模式，则显示用户友好的“服务不可用”登陆页面，其中HTTP状态代码为503（服务不可用）。
   1. 如果Commerce应用程序&#x200B;_未安装_，请重定向到“安装向导”。
   1. 如果会话无效，请重定向到主页。
   1. 如果存在任何其他应用程序初始化错误，则显示用户友好的“页面未找到”页面，其中HTTP状态代码为404（未找到）。
   1. 出现任何其他错误时，显示包含HTTP响应503的用户友好的“服务不可用”页面，并生成错误报告并在该页面上显示其ID。

### 静态资源入口点

[\Magento\Framework\App\StaticResource][static-resource]是用于检索静态资源(例如，CSS、JavaScript和图像)的应用程序。 它会延迟对静态资源执行任何操作，直到请求该资源为止。

>[!INFO]
>
>未在[生产模式](application-modes.md#production-mode)中使用静态视图文件的入口点，以避免服务器上潜在的漏洞。 在生产模式下，Commerce应用程序希望`<your Commerce install dir>/pub/static`目录中存在所有必要的资源。

在默认或开发人员模式下，根据相应`.htaccess`指定的重写规则，将不存在的静态资源的请求重定向到静态入口点。
当请求被重定向到入口点时，Commerce应用程序根据检索到的参数解析请求的URL并查找请求的资源。

- 在[开发人员](application-modes.md#developer-mode)模式下，将返回文件的内容，这样每次请求资源时，返回的内容都是最新的。
- 在[默认](application-modes.md#default-mode)模式下，已发布检索到的资源，以便先前请求的URL可以访问该资源。

  服务器处理所有未来对静态资源的请求的方式与处理静态文件的方式相同；即，不涉及入口点。 如果必须将已发布的文件与原始文件同步，则应删除`pub/static`目录；因此，会在下次请求时自动重新发布文件。

### 媒体资源入口点

[Magento\MediaStorage\App\Media][media]从数据库中检索媒体资源（即上载到媒体存储的任何文件）。 只要将数据库配置为介质存储，就会使用它。

`\Magento\Core\App\Media`尝试在配置的数据库存储中找到媒体文件并将其写入`pub/static`目录，然后返回其内容。 出错时，它会在标头中返回HTTP 404（未找到）状态代码，并且不含内容。

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
