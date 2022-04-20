---
title: 高级 [!DNL JavaScript] 捆绑
description: 了解JavaScript捆绑如何减小服务器请求的大小和频率。
source-git-commit: 09c4d0e09354230c8779b930f085d8c7c131b85b
workflow-type: tm+mt
source-wordcount: '2137'
ht-degree: 0%

---


# 高级 [!DNL JavaScript] 捆绑

捆绑 [!DNL JavaScript] 提高性能的模块主要是减少两方面：

1. 服务器请求数。
1. 这些服务器请求的大小。

在模块化应用程序中，服务器请求数可以达到数百个。 例如，以下屏幕截图仅显示 [!DNL JavaScript] 模块已加载到干净安装的主页上。

![无捆绑](../assets/performance/images/noBundling.png)

## 合并和捆绑

开箱即用， [!DNL Commerce] 提供了两种减少服务器请求数的方法：合并和捆绑。 默认情况下，这些设置处于关闭状态。 您可以在的管理员UI中打开 **[!UICONTROL Stores]** > **设置** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL [!DNL JavaScript] Settings]**，或从命令行中。

![捆绑](../assets/performance/images/bundlingImage.png)

### 基本捆绑

要从命令行启用内置捆绑：

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

这是本机 [!DNL Commerce] 一种机制，用于组合系统中存在的所有资产，并将它们分发到相同大小的包(bundle_0.js、bundle_1.js..bundle_x.js)中。

![[!DNL Commerce] 捆绑](../assets/performance/images/magentoBundling.png)

更好，但浏览器仍会加载 [!DNL JavaScript] 包，而不只是需要的包。

[!DNL Commerce] 捆绑会减少每页的连接数，但对于每个页面请求，它会加载所有包，即使当请求的页面可能只依赖于其中一个或两个包中的文件时也是如此。 浏览器缓存包后，性能会得到提高。 但是，由于浏览器同步加载这些包，因此用户首次访问 [!DNL Commerce] storefront可能需要一段时间才能渲染并影响用户体验。

### 基本合并

要从命令行启用内置合并：

```bash
php -f bin/magento config:set dev/js/merge_files 1
```

此命令将合并所有同步 [!DNL JavaScript] 文件合为一个文件。 在不启用捆绑的情况下启用合并是没有用的，因为 [!DNL Commerce] 使用RequireJS。 如果不启用捆绑， [!DNL Commerce] 仅合并RequireJS及其配置。 启用捆绑和合并后， [!DNL Commerce] 创建单个 [!DNL JavaScript] 文件：

![真实世界的融合](../assets/performance/images/magentoMergingDevWorld.png)

## 真实世界渲染时间

以前捆绑和合并的加载时间在开发环境中看起来非常好。 但在现实世界中，许多事物可能会减缓渲染速度：连接速度慢、连接阈值大、网络有限。 此外，移动设备的呈现速度不如台式机。

为了测试和准备面向真实世界的店面部署，我们建议您使用Chrome的本机限制配置文件“Slow 3G”进行测试。 使用Slow 3G时，我们以前的捆绑输出时间现在反映了许多用户的连接现实：

![实际捆绑](../assets/performance/images/magentoBundlingRealWorld.png)

在慢速3G连接中，需要大约44秒钟才能加载所有包，以便在主页上实现干净 [!DNL Commerce] 安装。

将包合并到单个文件中时，情况也是如此。 用户仍然可能等待约42秒才能完成初始页面加载，如下所示：

![真实世界的融合](../assets/performance/images/magentoMergingRealWorld.png)

使用更高级的方法 [!DNL JavaScript] 捆绑，我们可以缩短这些加载时间。

## 高级捆绑

记住， [!DNL JavaScript] 捆绑即为减少浏览器中加载的每个页面所请求的资产的数量和大小。 为此，我们要构建包，以便我们商店中的每个页面只需为每个访问的页面下载通用包和特定于页面的包。

实现此目的的一种方法是按页面类型定义包。 您可以对 [!DNL Commerce]的页面分为多种页面类型，包括类别、产品、CMS、客户、购物车和结账。 分类为其中一个页面类型的每个页面都有一组不同的RequireJS模块依赖项。 按页面类型捆绑RequireJS模块时，最终只会有几个包，其中涵盖存储中任何页面的依赖项。

例如，您最终可能会获得所有页面通用的依赖项包、仅CMS页面的包、仅目录页面的包、仅搜索页面的另一包以及签出页面的包。

您还可以专门创建包：有关常用功能、产品相关功能、送货功能、结帐功能、税金和表单验证。 如何定义包取决于您和商店的结构。 您可能会发现，一些捆绑策略的效果会优于其他策略。

干净 [!DNL Commerce] 安装后，可以按页面类型拆分包以获得足够的良好性能，但某些自定义设置可能需要进行更深入的分析和其他资产分发。

### 必需工具

以下步骤要求您安装并熟悉以下工具：

- [nodejs](https://nodejs.org/en/download/)
- [r.js](http://requirejs.org/docs/optimization.html#download)
- [[!DNL PhantomJS]](http://phantomjs.org/) （可选）

### 示例代码

本文中使用的示例代码的完整版本可在此处获取：

- [build.js](../assets/performance/code-samples/build.js)
- [deps.js](../assets/performance/code-samples/deps.js)
- [deps-map.sh](../assets/performance/code-samples/deps-map.sh.txt)

### 第一部分：创建捆绑配置

#### 1\。 添加build.js文件

创建 `build.js` 文件 [!DNL Commerce] 根目录。 此文件将包含包的整个内部版本配置。

```javascript
({
    optimize: 'none',
    inlineText: true
})
```

稍后，我们将 `optimize:` 从_设置 `none` to `uglify2` 缩小包输出。 但是，就目前而言，在开发过程中，您可以将其设置为 `none` 以确保更快的生成。

#### 2\。 添加RequireJS依赖项、岛、路径和映射

添加以下RequireJS内部版本配置节点， `deps`, `shim`, `paths`和 `map`，到内部版本文件中：

```javascript
({
    optimize: 'none',
    inlineText: true,

    deps: [],
    shim: {},
    paths: {},
    map: { "*": {} },
})
```

#### 3\。 聚合requirejs-config.js实例值

在此步骤中，您需要聚合所有多个 `deps`, `shim`, `paths`和 `map` 从您存储的配置节点 `requirejs-config.js` 文件到 `build.js` 文件。 为此，您可以打开 **[!UICONTROL Network]** 选项卡，然后导航到您商店中的任何页面，如主页。 在“网络”选项卡中，您将看到您商店的 `requirejs-config.js` 文件靠近顶部，突出显示在此处：

![需要JS配置](../assets/performance/images/RequireJSConfig.png)

在此文件中，您将找到每个配置节点(`deps`, `shim`, `paths`, `map`)。 您需要将这些多个节点值聚合到build.js文件的单个配置节点中。 例如，如果您的商店 `requirejs-config.js` 实例包含15个单独的条目 `map` 节点，则需要将所有15个节点的条目合并到单个中 `map` 节点 `build.js` 文件。 对于 `deps`, `shim`和 `paths` 节点。 如果没有脚本来自动化此过程，可能需要一些时间。

您需要更改路径 `mage/requirejs/text` to `requirejs/text` in `paths` 配置节点如下所示：

```javascript
({
    //...
    paths: {
        //...
        "text": "requirejs/text"
    },
})
```

#### 4\。 添加模块节点

在 `build.js` 文件，添加模块[] 数组作为稍后为店面定义的包的占位符。

```javascript
({
    optimize: 'none',
    inlineText: true,

    deps: [],
    shim: {},
    paths: {},
    map: { "*": {} },

    modules: [],
})
```

#### 5\。 检索RequireJS依赖项

您可以检索 [!DNL RequireJS] 使用：

1. [!DNL PhantomJS] 从命令行(假定您拥有 [!DNL PhantomJS] )。
1. 在浏览器控制台中使用RequireJS命令。

#### 使用 [!DNL PhantomJS]:

在 [!DNL Commerce] 根目录，创建名为 `deps.js` 并复制下面的代码。 此代码使用[!DNL [!DNL PhantomJS]]打开页面并等待浏览器加载所有页面资产。 然后输出所有 [!DNL RequireJS] 给定页面的依赖关系。

```javascript
"use strict";
var page = require('webpage').create(),
    system = require('system'),
    address;

if (system.args.length === 1) {
    console.log('Usage: $phantomjs deps.js url');
    phantom.exit(1);
} else {
    address = system.args[1];
    page.open(address, function (status) {
        if (status !== 'success') {
            console.log('FAIL to load the address');
        } else {
            setTimeout(function () {
                console.log(page.evaluate(function () {
                    return Object.keys(window.require.s.contexts._.defined);
                }));
                phantom.exit();
            }, 5000);
        }
    });
}
```

在 [!DNL Commerce] 根目录，并针对存储中表示特定页面类型的每个页面运行脚本：

<pre>
phantomjs deps.js <i>特定页面的url</i> &gt; <i>text-file-represening-pagetype-dependencies</i>
</pre>

例如，以下是Luma主题样例店的四个页面，这些页面表示我们将用来创建四个包（主页、类别、产品、购物车）的四种页面类型：

```terminal
phantomjs deps.js http://m2.loc/ > bundle/homepage.txt
phantomjs deps.js http://m2.loc/women/tops-women/jackets-women.html > bundle/category.txt
phantomjs deps.js http://m2.loc/beaumont-summit-kit.html > bundle/product.txt
phantomjs deps.js http://m2.loc/checkout/cart/?SID=m2tjdt7ipvep9g0h8pmsgie975 > bundle/cart.txt (prepare a shopping cart)
..............
```

#### 要使用浏览器控制台，请执行以下操作：

如果您不想使用 [!DNL PhantomJS]，则在店面中查看每个页面类型时，您可以从浏览器控制台中运行以下命令：

```shell
Object.keys(window.require.s.contexts._.defined)
```

此命令(在 [!DNL PhantomJS] 脚本)会创建相同的列表 [!DNL RequireJS] 依赖关系，并在浏览器控制台中显示它们。 这种方法的缺点在于，您必须创建自己的包/页面类型文本文件。

#### 6\。 设置输出格式并过滤输出

合并 [!DNL RequireJS] 依赖关系到页面类型文本文件中，您可以对每个页面类型依赖关系文件使用以下命令，将文件中的逗号替换为换行符：

```terminal
sed -i -e $'s/,/\\\n/g' bundle/category.txt
sed -i -e $'s/,/\\\n/g' bundle/homepage.txt
sed -i -e $'s/,/\\\n/g' bundle/product.txt
....
```

您还应删除每个文件的所有mixin，因为mixin重复依赖项。 对每个依赖关系文件使用以下命令：

```terminal
sed -i -e 's/mixins\!.*$//g' bundle/homepage.txt
sed -i -e 's/mixins\!.*$//g' bundle/category.txt
sed -i -e 's/mixins\!.*$//g' bundle/product.txt
...
```

#### 7\。 识别唯一的常用包

其目标是创建 [!DNL JavaScript] 所有页面所需的文件。 这样，浏览器只需加载通用包以及一个或多个特定页面类型即可。

在 [!DNL Commerce] 根目录并使用以下命令验证是否具有依赖关系，可以拆分到单独的包中：

```bash
sort bundle/*.txt |uniq -c |sort -n
```

此命令可合并和排序 `bundle/*.txt` 文件。  输出还显示包含每个依赖项的文件数：

```terminal
1 buildTools,
1 jquery/jquery.parsequery,
1 jsbuild,
2 jquery/jquery.metadata,
2 jquery/validate,
2 mage/bootstrap,
3 jquery
3 jquery/ui
3 knockoutjs/knockout
...
```

此输出显示 `buildTools` 只有一个bundle/*.txt文件中存在依赖项。 的 `jquery/jquery.metadata` 依赖关系位于两(2)个文件中，并且 `es6-collections` 位于三(3)个文件中。

我们的输出仅显示三种页面类型（主页、类别和产品），它们告诉我们：

- 只有一种页面类型具有三个依赖关系（如数字1所示）。
- 另外还有三种依赖关系发生在两种页面类型上（如数字2所示）。
- 最后三个依赖项对于我们所有三种页面类型都是通用的（如数字3所示）。

这告知我们，只要我们知道哪些页面类型需要哪些依赖项，就可以将依赖项拆分到不同的包中，就有可能提高商店的页面加载速度。

#### 8\。 创建依赖关系分发文件

要了解哪些页面类型需要哪些依赖关系，请在 [!DNL Commerce] 名为的根目录 `deps-map.sh` 并复制以下代码：

```shell
awk 'END {
 for (R in rec) {
   n = split(rec[R], t, "/")
   if (n > 1)
     dup[n] = dup[n] ? dup[n] RS sprintf("\t%-20s -->\t%s", rec[R], R) : \
       sprintf("\t%-20s -->\t%s", rec[R], R)
   }
 for (D in dup) {
   printf "records found in %d files:\n\n", D
   printf "%s\n\n", dup[D]
   }
 }
{
 rec[$0] = rec[$0] ? rec[$0] "/" FILENAME : FILENAME
}' bundle/*.txt
```

您还可以在 [https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html](https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html)

在 [!DNL Commerce] 根目录并运行文件：

```bash
bash deps-map.sh
```

此脚本的输出应用于我们的三个示例页面类型，其外观应当如下（但要长得多）：

```terminal
bundle/product.txt   -->   buildTools,
bundle/category.txt  -->   jquery/jquery.parsequery,
bundle/product.txt   -->   jsbuild,

bundle/category.txt/bundle/homepage.txt -->    jquery/jquery.metadata,
bundle/category.txt/bundle/homepage.txt -->    jquery/validate,
bundle/category.txt/bundle/homepage.txt -->    mage/bootstrap,

bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> jquery,
bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> jquery/ui,
bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> knockoutjs/knockout,
```

此信息足以构建包配置。

#### 9\。 在build.js文件中创建包

打开 `build.js` 配置文件，并将包添加到 `modules` 节点。 每个包应定义以下属性：

- `name` — 包的名称。 例如，名称 `bundles/cart` 生成 `cart.js` 捆绑在 `bundles` 子目录。

- `create` — 用于创建包的布尔标记(值： `true` 或 `false`)。

- `include` — 作为页面的依赖项包含的资产（字符串）数组。 RequireJS会跟踪所有依赖项并将它们包含在包中，除非排除。

- `exclude` — 要从包中排除的包或资产数组。

```javascript
{
    name: 'bundles/catalog',
    create: true,
    include: [
        'addToWishlist',
        'priceBundle',
        'priceUtils',
        'priceOptions',
        'sticky',
        'productSummary',
        'slide'
    ],
    exclude: [
        'requirejs/require',
        'bundles/default',
        'mage/bootstrap'
    ],
}
```

此示例将重用 `mage/bootstrap` 和 `requirejs/require` 资产，优先考虑必须同步加载的最重要组件和组件。 存在的包包括：

- `requirejs/require` — 唯一同步加载的束
- `mage/bootstrap` — 带有UI组件的引导包
- `bundles/default` — 所有页面都需要默认包
- `bundles/cart` — 购物车页面所需的包
- `bundles/shipping` — 购物车和结帐页面的常用捆绑包（假定以前打开购物车页面且已加载送货捆绑包时，结帐页面从未直接打开，加载速度会更快）
- `bundles/checkout` — 结账时的一切
- `bundles/catalog` — 产品和类别页面的所有内容

### 第2部分：生成包

以下步骤描述了生成更高效的基本过程 [!DNL Commerce] 包。 您可以通过任何方式自动完成此过程，但仍需要使用 `nodejs` 和 `r.js` 来生成包。 如果你的主题 [!DNL JavaScript] — 相关的自定义项，且无法重复使用 `build.js` 文件，则可能需要创建多个 `build.js` 每个主题的配置。

#### 1.生成静态存储站点

在生成包之前，请运行静态部署命令：

```bash
php -f bin/magento setup:static-content:deploy -f -a frontend
```

此命令会为您设置的每个主题和区域设置生成静态存储部署。 例如，如果您使用Luma主题和自定义主题，并在其中以英语和法语区域设置，则将生成四个静态部署：

- ...luma/en_US
- ...luma/fr_FR
- ...custom/en_US
- ...custom/fr_FR

要为所有存储主题和区域设置生成包，请为每个存储主题和区域设置重复以下步骤。

#### 2.将静态存储内容移动到临时目录

首先，您需要将静态内容从目标目录移动到某些临时目录，因为RequireJS会替换目标目录内的所有内容。

```bash
mv pub/static/frontend/Magento/{theme}/{locale} pub/static/frontend/Magento/{theme}/{locale}_tmp
```

例如：

```bash
mv pub/static/frontend/Magento/luma/en_US pub/static/frontend/Magento/luma/en_US_tmp
```

#### 3.运行r.js优化程序

然后，在 `build.js` 文件来源 [!DNL Commerce]的根目录。 指向所有目录和文件的路径都与工作目录相关。

```bash
r.js -o build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

此命令在 `bundles` 目录的子目录，在本例中，该子目录将在 `pub/static/frontend/Magento/luma/en_US/bundles`.

列出新包目录的内容可能如下所示：

```bash
ll pub/static/frontend/Magento/luma/en_US/bundles
```

```terminal
total 1900
drwxr-xr-x  2 root root    4096 Mar 28 11:24 ./
drwxr-xr-x 70 root root    4096 Mar 28 11:24 ../
-rw-r--r--  1 root root  116417 Mar 28 11:24 cart.js
-rw-r--r--  1 root root  187090 Mar 28 11:24 catalog.js
-rw-r--r--  1 root root  307619 Mar 28 11:24 checkout.js
-rw-r--r--  1 root root 1240608 Mar 28 11:24 default.js
-rw-r--r--  1 root root   74233 Mar 28 11:24 shipping.js
```

#### 4.配置RequireJS以使用包

要使RequireJS使用包，请添加 `onModuleBundleComplete` 回调之后 `modules` 节点 `build.js` 文件：

```javascript
[
    {
       //...
       exclude: [
           'requirejs/require',
           'bundles/default',
           'bundles/checkout',
           'bundles/cart',
           'bundles/shipping',
           'mage/bootstrap'
       ],
   },
],
bundlesConfigOutFile: `${config.dir}/requirejs-config.js`,
onModuleBundleComplete: function(data) {
    if (this.bundleConfigAppended) {
        return;
    }
    this.bundleConfigAppended = true;

    // bundlesConfigOutFile requires a simple require.config call in order to modify the configuration
    const bundleConfigPlaceholder = `
(function (require) {
require.config({});
})(require);
    `;

    fs.appendFileSync(this.bundlesConfigOutFile, bundleConfigPlaceholder);
}
```

#### 5.重新运行部署命令

运行以下命令以部署：

```bash
r.js -o app/design/frontend/Magento/luma/build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

打开 `requirejs-config.js` 在 `pub/static/frontend/Magento/luma/en_US` 用于验证RequireJS是否已通过捆绑配置调用附加了文件的目录：

```javascript
require.config({
    bundles: {
        "bundles/default": ["mage/template", "mage/apply/scripts", "mage/apply/main", "mage/mage", "mage/translate", "mage/loader"],
        "bundles/cart": ["Magento_Ui/js/lib/validation/utils", "Magento_Ui/js/lib/validation/rules", "Magento_Ui/js/lib/validation/validation"]
    }
}
```

>[!NOTE]
>
>配置包时，请确保在 `requirejs.config()` 调用的执行顺序，因为调用的执行顺序与调用的显示顺序相同。

#### 6.测试结果

页面加载后，请注意浏览器加载了不同的依赖项和包。 例如，以下是“慢3G”配置文件的结果：

![速度提高一倍](../assets/performance/images/TwiceAsFast.png)

现在，空主页的页面加载时间是使用本机主页的两倍 [!DNL Commerce] 捆绑。 但我们可以做得更好。

#### 7.优化捆绑包

即使有弹簧， [!DNL JavaScript] 文件仍然很大。 使用RequireJS缩小它们，RequireJS会使用增强符进行缩小 [!DNL JavaScript] 效果不错。

在 `build.js` 文件，添加 `uglify2` 作为位于 `build.js` 文件：

```javascript
({
    optimize: 'uglify2',
    inlineText: true
})
```

结果可能非常显着：
![速度快3倍](../assets/performance/images/ThreeTimesFaster.png)

现在，加载时间比使用本机快三倍 [!DNL Commerce] 捆绑。
