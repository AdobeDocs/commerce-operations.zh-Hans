---
title: 应用程序初始化和引导
description: 请阅读有关商务应用程序的初始化和引导逻辑。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---


# 初始化和引导概览

要运行商务应用程序，请在 [pub/index.php][index]:

- 包括 [app/bootstrap.php][bootinitial]，执行基本初始化例程，例如错误处理、初始化自动加载器、设置分析选项和设置默认时区。
- 创建实例 [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- 创建商务应用程序实例： [\Magento\Framework\AppInterface][app-face]
- 运行商务

## Bootstrap运行逻辑

[引导对象][bootinitial] 会使用以下算法来运行商务应用程序：

1. 初始化错误处理程序。
1. 创建 [对象管理器][object] 以及随处使用并受环境影响的基本共享服务。 环境参数会正确插入到这些对象中。
1. 声明维护模式为 _not_ 已启用；否则，终止。
1. 声明已安装Commerce应用程序；否则，终止。
1. 启动商务应用程序。

   在应用程序启动期间出现的任何未捕获的异常都会自动传递回商务 `catchException()` 方法。 后者必须返回 `true` 或 `false`:

   - 如果 `true`:商务已成功处理异常。 没必要做别的事。
   - 如果 `false`:（或任何其他空结果）商务未处理异常。 引导对象执行默认的异常处理子程序。

1. 发送应用程序对象提供的响应。

   >[!INFO]
   >
   >Commerce应用程序已安装且未处于维护模式的断言是 `\Magento\Framework\App\Bootstrap` 类。 在创建引导对象时，可以使用入口点脚本对其进行修改。

   修改引导对象的示例入口点脚本：

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

引导对象指定商务应用程序如何处理未捕获的异常，如下所示：

- 在 [开发人员模式](../bootstrap/application-modes.md#developer-mode)，则按原样显示例外。
- 在任何其他模式下，尝试记录异常并显示一般错误消息。
- 终止商务，并包含错误代码 `1`

## 入口点应用程序

我们有以下入口点应用程序（即由Commerce定义的应用程序，由Web服务器用作目录索引）：

### HTTP入口点

[\Magento\Framework\App\Http][http] 操作如下：

1. 确定 [应用领域](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. 启动前控制器和路由系统以查找和执行控制器操作。
1. 使用HTTP响应对象返回从控制器操作获得的结果。
1. 错误处理（按以下优先级顺序）：

   1. 如果您使用 [开发人员模式](../bootstrap/application-modes.md#developer-mode):
      - 如果未安装Commerce应用程序，请重定向到“安装向导”。
      - 如果已安装Commerce应用程序，则显示错误和HTTP状态代码500（内部服务器错误）。
   1. 如果商务应用程序处于维护模式，则显示用户友好的“服务不可用”登陆页面，其HTTP状态代码为503（服务不可用）。
   1. 如果商务应用程序为 _not_ 已安装，请重定向到“安装向导”。
   1. 如果会话无效，请重定向到主页。
   1. 如果存在任何其他应用程序初始化错误，则显示用户友好的“页面未找到”页面，其HTTP状态代码为404（未找到）。
   1. 在出现任何其他错误时，显示用户友好的“服务不可用”页面（HTTP响应为503），并生成错误报告，并在页面上显示其ID。

### 静态资源入口点

[\Magento\Framework\App\StaticResource][static-resource] 是用于检索静态资源（例如，CSS、JavaScript和图像）的应用程序。 它会使用静态资源推迟任何操作，直到请求资源为止。

>[!INFO]
>
>静态视图文件的入口点不在 [生产模式](application-modes.md#production-mode) 以避免服务器上的潜在漏洞。 在生产模式下，Commerce应用程序希望 `<your Commerce install dir>/pub/static` 目录访问Advertising Cloud的帮助。

在默认或开发者模式下，对不存在的静态资源的请求根据相应的 `.htaccess`.
当请求被重定向到入口点时，Commerce应用程序会根据检索到的参数解析请求的URL并找到请求的资源。

- 在 [开发人员](application-modes.md#developer-mode) 模式下，会返回文件的内容，以便每次请求资源时，返回的内容都是最新的。
- 在 [默认](application-modes.md#default-mode) 模式下，将发布检索到的资源，以便之前请求的URL可以访问该资源。

   将来对静态资源的所有请求都由服务器处理，处理方式与静态文件相同；即，不涉及入口点。 如果需要将已发布的文件与原始文件同步，则 `pub/static` 目录应被删除；因此，文件会随下一个请求自动重新发布。

### 媒体资源入口点

[Magento\MediaStorage\App\Media][media] 从数据库中检索媒体资源（即上传到媒体存储的任何文件）。 每当将数据库配置为媒体存储时，都会使用它。

`\Magento\Core\App\Media` 尝试在配置的数据库存储中查找媒体文件，并将其写入 `pub/static` 目录，然后返回其内容。 出错时，它会在标头中返回一个HTTP 404（未找到）状态代码，其中不包含任何内容。

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
