---
title: 高级 [!DNL JavaScript] 捆绑
description: 了解JavaScript捆绑包如何减少服务器请求的大小和频率。
exl-id: 81a313f8-e541-4da6-801b-8bbd892d6252
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2137'
ht-degree: 0%

---

# 高级 [!DNL JavaScript] 捆绑

捆绑 [!DNL JavaScript] 提高性能的模块涉及减少以下两点：

1. 服务器请求的数量。
1. 这些服务器请求的大小。

在模块化应用程序中，服务器请求的数量可能高达数百个。 例如，以下屏幕快照仅显示列表的开头 [!DNL JavaScript] 全新安装的主页上加载的模块。

![无捆绑](../assets/performance/images/noBundling.png)

## 合并和捆绑

开箱即用， [!DNL Commerce] 提供了两种减少服务器请求数的方法：合并和捆绑。 这些设置默认处于关闭状态。 您可以在中的管理员UI中打开它们 **[!UICONTROL Stores]** > **设置** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL [!DNL JavaScript] Settings]**，或从命令行访问。

![捆绑](../assets/performance/images/bundlingImage.png)

### 基本捆绑

要从命令行启用内置捆绑，请执行以下操作：

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

这是本机 [!DNL Commerce] 一种机制，用于组合系统中存在的所有资产并将它们分发到大小相同的包(bundle_0.js、bundle_1.js ... bundle_x.js)中：

![[!DNL Commerce] 捆绑](../assets/performance/images/magentoBundling.png)

更好，但浏览器仍加载 [!DNL JavaScript] 捆绑包，而不仅仅是所需的捆绑包。

[!DNL Commerce] 捆绑可减少每个页面的连接数，但对于每个页面请求，它会加载所有捆绑包，即使请求的页面可能仅依赖于一个或两个捆绑包中的文件。 在浏览器缓存捆绑包后，性能得以提高。 但是，由于浏览器同步加载这些捆绑包，因此用户第一次访问 [!DNL Commerce] storefront可能需要一段时间才能呈现，并且会损害用户体验。

### 基本合并

要从命令行启用内置合并，请执行以下操作：

```bash
php -f bin/magento config:set dev/js/merge_files 1
```

此命令合并所有同步 [!DNL JavaScript] 文件合并为一个文件。 在不启用捆绑的情况下启用合并没有用，因为 [!DNL Commerce] 使用RequireJS。 如果不启用捆绑， [!DNL Commerce] 仅合并RequireJS及其配置。 当您同时启用捆绑和合并时， [!DNL Commerce] 创建单个 [!DNL JavaScript] 文件：

![现实世界中的融合](../assets/performance/images/magentoMergingDevWorld.png)

## 真实世界渲染时间

在开发环境中，之前的捆绑和合并加载时间看起来很棒。 但在现实世界中，很多事情会减慢渲染速度：连接速度慢，连接阈值大，网络有限。 此外，移动设备的呈现速度不如台式机。

为了测试和准备您的店面部署，以便适应现实情况，我们建议您使用Chrome的本机节流配置文件“慢3G”进行测试。 通过Slow 3G，我们以前捆绑的输出时间现在反映了许多用户的连接现实：

![现实世界的捆绑](../assets/performance/images/magentoBundlingRealWorld.png)

在3G连接速度较慢的情况下，大约需要44秒才能加载干净的主页的所有捆绑包 [!DNL Commerce] 安装。

将捆绑包合并到单个文件中时也是如此。 用户仍然可以等待约42秒的时间进行初始页面加载，如下所示：

![现实世界中的融合](../assets/performance/images/magentoMergingRealWorld.png)

使用更高级的方法实现 [!DNL JavaScript] 捆绑时，我们可以缩短这些加载时间。

## 高级捆绑

请记住，目标 [!DNL JavaScript] 捆绑是为了减少浏览器中加载的每个页面所请求的资产的数量和大小。 为此，我们希望构建捆绑包，以便商店中的每个页面只需要下载一个通用捆绑包和一个特定于页面的捆绑包，即可访问每个页面。

实现此目标的一种方法是按页面类型定义包。 您可以分类 [!DNL Commerce]的页面分为多种页面类型，包括类别、产品、CMS、客户、购物车和结账。 分类为其中一种页面类型的每个页面都有一组不同的RequireJS模块依赖项。 当按页面类型捆绑您的RequireJS模块时，最终将只有少数捆绑包覆盖存储中任何页面的依赖项。

例如，您最终可能会得到一个捆绑包，用于所有页面通用的依赖项，一个捆绑包用于仅CMS页面，一个捆绑包用于仅目录页面，另一个捆绑包用于仅搜索页面，以及一个捆绑包用于签出页面。

您还可以按用途创建包：用于常见功能、产品相关功能、配送功能、结帐功能、税费和表单验证。 如何定义捆绑包取决于您以及商店的结构。 您可能会发现某些捆绑策略将比其他策略效果更好。

干净 [!DNL Commerce] 安装可通过按页面类型拆分捆绑包来实现足够的良好性能，但某些自定义可能需要更深入的分析和其他资产分发。

### 所需工具

以下步骤需要您安装并熟悉以下工具：

- [节点集](https://nodejs.org/en/download/)
- [r.js](http://requirejs.org/docs/optimization.html#download)
- [[!DNL PhantomJS]](https://phantomjs.org/) （可选）

### 示例代码

可在此处找到本文中使用的示例代码的完整版本：

- [build.js](../assets/performance/code-samples/build.js)
- [deps.js](../assets/performance/code-samples/deps.js)
- [deps-map.sh](../assets/performance/code-samples/deps-map.sh.txt)

### 第1部分：创建捆绑配置

#### 1\. 添加build.js文件

创建 `build.js` 中的文件 [!DNL Commerce] 根目录。 此文件将包含捆绑包的整个生成配置。

```javascript
({
    optimize: 'none',
    inlineText: true
})
```

稍后，我们将更改 `optimize:` 从_设置 `none` 到 `uglify2` 以缩小捆绑包输出。 但现在，在开发过程中，您可以将其保留为 `none` 以确保更快的构建。

#### 2\. 添加RequireJS依赖项、垫片、路径和映射

添加以下RequireJS内部版本配置节点， `deps`， `shim`， `paths`、和 `map`，到您的构建文件：

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

#### 3\. 聚合requirejs-config.js实例值

在此步骤中，您将需要聚合所有多个 `deps`， `shim`， `paths`、和 `map` 来自存储中的配置节点 `requirejs-config.js` 文件放入中的相应节点 `build.js` 文件。 为此，您可以打开 **[!UICONTROL Network]** 在浏览器的“开发人员工具”面板中按Tab键，然后导航到商店中的任何页面，例如主页。 在“网络”选项卡中，您将看到您商店的 `requirejs-config.js` 文件顶部附近，在此处突出显示：

![需要JS配置](../assets/performance/images/RequireJSConfig.png)

在此文件中，您将找到每个配置节点的多个条目(`deps`， `shim`， `paths`， `map`)。 您需要将这些多个节点值聚合到build.js文件的单个配置节点中。 例如，如果您的商店 `requirejs-config.js` 实例具有15个单独的条目 `map` 节点中，您需要将所有15个节点的条目合并到单个节点中 `map` 节点的位置 `build.js` 文件。 同样的情况也适用于 `deps`， `shim`、和 `paths` 节点。 如果没有脚本来自动化此过程，则可能需要一些时间。

您需要更改路径 `mage/requirejs/text` 到 `requirejs/text` 在 `paths` 配置节点如下所示：

```javascript
({
    //...
    paths: {
        //...
        "text": "requirejs/text"
    },
})
```

#### 4\. 添加模块节点

在 `build.js` 文件，添加模块[] 数组，作为您稍后为店面定义的捆绑包的占位符。

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

#### 5\. 检索RequireJS依赖项

您可以检索所有 [!DNL RequireJS] 使用以下方式从存储区的页面类型中依赖模块：

1. [!DNL PhantomJS] 从命令行(假设您拥有 [!DNL PhantomJS] 已安装)。
1. 在浏览器的控制台中需要JS命令。

#### 使用 [!DNL PhantomJS]：

在 [!DNL Commerce] 根目录，创建一个名为 `deps.js` 并复制下面的代码。 此代码使用[！DNL [!DNL PhantomJS]]打开一个页面，然后等待浏览器加载所有页面资产。 然后，输出所有 [!DNL RequireJS] 指定页面的依赖关系。

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

打开内部的终端 [!DNL Commerce] 根目录并对存储中表示特定页面类型的每个页面运行脚本：

<pre>
phantomjs deps.js <i>URL到特定页面</i> &gt; <i>text-file-representing-pagetype-dependencies</i>
</pre>

例如，下面是Luma主题示例存储中的四个页面，这些页面表示我们将用于创建四个包（主页、类别、产品、购物车）的四种页面类型：

```terminal
phantomjs deps.js http://m2.loc/ > bundle/homepage.txt
phantomjs deps.js http://m2.loc/women/tops-women/jackets-women.html > bundle/category.txt
phantomjs deps.js http://m2.loc/beaumont-summit-kit.html > bundle/product.txt
phantomjs deps.js http://m2.loc/checkout/cart/?SID=m2tjdt7ipvep9g0h8pmsgie975 > bundle/cart.txt (prepare a shopping cart)
..............
```

#### 要使用浏览器控制台，请执行以下操作：

如果您不想使用 [!DNL PhantomJS]时，您可以从浏览器的控制台运行以下命令，同时查看店面中的每种页面类型：

```shell
Object.keys(window.require.s.contexts._.defined)
```

此命令(用于 [!DNL PhantomJS] script)创建相同的列表 [!DNL RequireJS] 依赖关系并在浏览器的控制台中显示它们。 此方法的缺点是，您必须创建自己的包/页面类型文本文件。

#### 6\. 设置输出格式并筛选

合并之后 [!DNL RequireJS] 将依赖关系转换为页面类型文本文件，可以在每个页面类型依赖关系文件上使用以下命令，将文件中的逗号替换为换行符：

```terminal
sed -i -e $'s/,/\\\n/g' bundle/category.txt
sed -i -e $'s/,/\\\n/g' bundle/homepage.txt
sed -i -e $'s/,/\\\n/g' bundle/product.txt
....
```

您还应该删除每个文件的所有mixin，因为mixin重复依赖关系。 对每个依赖项文件使用以下命令：

```terminal
sed -i -e 's/mixins\!.*$//g' bundle/homepage.txt
sed -i -e 's/mixins\!.*$//g' bundle/category.txt
sed -i -e 's/mixins\!.*$//g' bundle/product.txt
...
```

#### 7\. 确定独特和常见的捆绑包

目标是创建一组通用的 [!DNL JavaScript] 所有页面所需的文件。 这样，浏览器只需加载通用捆绑包以及一个或多个特定页面类型。

在中打开终端 [!DNL Commerce] 根目录，并使用以下命令验证是否具有可以拆分为单独捆绑的依赖项：

```bash
sort bundle/*.txt |uniq -c |sort -n
```

此命令合并和排序在 `bundle/*.txt` 文件。  输出还显示包含每个依赖项的文件数：

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

此输出显示 `buildTools` 仅在bundle/*.txt文件中的一个文件中为依赖项。 此 `jquery/jquery.metadata` 依赖关系位于两(2)个文件中，并且 `es6-collections` 在三(3)个文件中。

我们的输出仅显示三种页面类型（主页、类别和产品），它们告诉我们：

- 三个依赖项仅对一种页面类型具有唯一性（由数字1显示）。
- 两种页面类型（如数字2所示）上存在另外三种依赖关系。
- 最后三个依赖项对于我们所有的三种页面类型都是通用的（如数字3所示）。

这告诉我们，一旦我们知道哪些页面类型需要哪些依赖项，就可以将依赖项拆分为不同的捆绑包，从而有可能提高商店的页面加载速度。

#### 8\. 创建依赖项分发文件

要了解哪些页面类型需要哪些依赖项，请在 [!DNL Commerce] 已调用根目录 `deps-map.sh` 并复制以下代码：

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

您还可以在中找到脚本 [https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html](https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html)

在中打开终端 [!DNL Commerce] 根目录并运行文件：

```bash
bash deps-map.sh
```

此脚本的输出应用于我们的三个示例页面类型，应当类似于以下内容（但时间更长）：

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

此信息足以构建捆绑包配置。

#### 9\. 在build.js文件中创建包

打开 `build.js` 配置文件并将您的捆绑包添加到 `modules` 节点。 每个包应定义以下属性：

- `name` — 包的名称。 例如，名称 `bundles/cart` 生成 `cart.js` 中的捆绑包 `bundles` 子目录。

- `create` — 用于创建捆绑包的布尔标记(值： `true` 或 `false`)。

- `include` — 作为页面的依赖项包含的资产（字符串）数组。 RequireJS跟踪所有依赖项并将它们包含在包中，除非将其排除。

- `exclude` — 要从捆绑包中排除的捆绑包或资源的数组。

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

此示例重用 `mage/bootstrap` 和 `requirejs/require` 资产，对其必须同步加载的最重要的组件和组件赋予更高的优先级。 存在的捆绑包包括：

- `requirejs/require` — 唯一同步加载的捆绑包
- `mage/bootstrap` — 带UI组件的引导程序捆绑包
- `bundles/default` — 所有页面都需要默认捆绑包
- `bundles/cart` — 购物车页面所需的捆绑包
- `bundles/shipping` — 购物车和结帐页面的通用捆绑包（假设从未直接打开结帐，则如果以前打开了购物车页面并且已加载配送捆绑包，则结帐页面的加载速度会更快）
- `bundles/checkout` — 结账所需的一切
- `bundles/catalog` — 产品和类别页面所需的一切

### 第2部分：生成包

以下步骤描述了提高效率的基本过程 [!DNL Commerce] 捆绑包。 您可以按照所需的任何方式自动执行此过程，但您仍需要使用 `nodejs` 和 `r.js` 以实际生成您的包。 如果你的主题有 [!DNL JavaScript] — 相关的自定义项，无法重复使用 `build.js` 文件，您可能需要创建多个 `build.js` 每个主题的配置。

#### 1.生成静态存储站点

在生成捆绑包之前，请运行静态部署命令：

```bash
php -f bin/magento setup:static-content:deploy -f -a frontend
```

此命令为您设置的每个主题和区域设置生成静态存储部署。 例如，如果您使用Luma主题和具有英语和法语区域设置的自定义主题，则会生成四个静态部署：

- ...luma/en_US
- ...luma/fr_FR
- ...custom/en_US
- ...custom/fr_FR

要生成所有商店主题和区域设置的包，请对每个商店主题和区域设置重复以下步骤。

#### 2.将静态存储内容移动到临时目录

首先，需要将静态内容从目标目录移动到某个临时目录，因为RequireJS会替换目标目录中的所有内容。

```bash
mv pub/static/frontend/Magento/{theme}/{locale} pub/static/frontend/Magento/{theme}/{locale}_tmp
```

例如：

```bash
mv pub/static/frontend/Magento/luma/en_US pub/static/frontend/Magento/luma/en_US_tmp
```

#### 3.运行r.js优化器

然后，在上运行r.js优化器 `build.js` 文件来源 [!DNL Commerce]的根目录。 所有目录和文件的路径均相对于工作目录。

```bash
r.js -o build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

此命令在 `bundles` 目标目录的子目录，在本例中会导致 `pub/static/frontend/Magento/luma/en_US/bundles`.

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

要让RequireJS使用您的包，请添加 `onModuleBundleComplete` 回调晚于 `modules` 中的节点 `build.js` 文件：

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

运行以下命令进行部署：

```bash
r.js -o app/design/frontend/Magento/luma/build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

打开 `requirejs-config.js` 在 `pub/static/frontend/Magento/luma/en_US` 目录，以验证RequireJS是否将该文件附加到捆绑配置调用：

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
>配置捆绑包时，请确保将 `requirejs.config()` 调用，因为调用是按其显示的顺序执行的。

#### 6.测试结果

加载页面后，请注意浏览器加载了不同的依赖项和捆绑包。 例如，以下是“慢3G”配置文件的结果：

![快两倍](../assets/performance/images/TwiceAsFast.png)

现在，空主页的页面加载时间比使用本机页面的加载时间快一倍 [!DNL Commerce] 捆绑销售。 但是我们可以做得更好。

#### 7.优化包

即使压缩了， [!DNL JavaScript] 文件仍然很大。 使用RequireJS来缩小它们，后者使用修饰符进行缩小 [!DNL JavaScript] 以取得良好的效果。

要在中启用优化器，请执行以下操作 `build.js` 文件，添加 `uglify2` 作为optimize属性的值，该属性位于 `build.js` 文件：

```javascript
({
    optimize: 'uglify2',
    inlineText: true
})
```

结果可能非常显着：
![快三倍](../assets/performance/images/ThreeTimesFaster.png)

现在，加载时间比本机快三倍 [!DNL Commerce] 捆绑销售。
