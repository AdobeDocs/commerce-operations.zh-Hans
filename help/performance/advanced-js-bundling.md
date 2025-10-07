---
title: 高级 [!DNL JavaScript] 捆绑
description: 了解Adobe Commerce中的高级 [!DNL javascript] 捆绑。 了解实施指导和优化策略。
exl-id: 81a313f8-e541-4da6-801b-8bbd892d6252
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '2133'
ht-degree: 0%

---

# 高级[!DNL JavaScript]捆绑

捆绑[!DNL JavaScript]模块以获得更好的性能，需要减少以下两点：

1. 服务器请求的数量。
1. 这些服务器请求的大小。

在模块化应用程序中，服务器请求的数量可能高达数百个。 例如，以下屏幕快照仅显示全新安装的主页上加载的[!DNL JavaScript]模块列表的开始。

![没有捆绑](../assets/performance/images/noBundling.png)

## 合并和捆绑

[!DNL Commerce]提供了两种现成的方法来减少服务器请求数：合并和捆绑。 默认情况下，这些设置处于关闭状态。 您可以在&#x200B;**[!UICONTROL Stores]** > **设置** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL [!DNL JavaScript] Settings]**&#x200B;中的管理员UI中或从命令行将其打开。

![捆绑](../assets/performance/images/bundlingImage.png)

### 基本捆绑

要从命令行启用内置捆绑包，请执行以下操作：

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

这是一个本机[!DNL Commerce]机制，它将系统中存在的所有资产组合在一起，并在大小相同的捆绑包(bundle_0.js、bundle_1.js ... bundle_x.js)之间分发它们：

![[!DNL Commerce]捆绑](../assets/performance/images/magentoBundling.png)

更好，但浏览器仍加载所有[!DNL JavaScript]包，而不只是所需的包。

[!DNL Commerce]捆绑可减少每页的连接数，但对于每个页面请求，它会加载所有捆绑包，即使所请求的页面可能仅依赖于一个或两个捆绑包中的文件也是如此。 在浏览器缓存捆绑包后，性能得以改进。 但是，由于浏览器同步加载这些捆绑包，因此用户首次访问[!DNL Commerce]店面可能需要一段时间才能呈现，并且会损害用户体验。

### 基本合并

要从命令行启用内置合并，请执行以下操作：

```bash
php -f bin/magento config:set dev/js/merge_files 1
```

此命令将所有同步[!DNL JavaScript]文件合并到一个文件中。 在不启用捆绑的情况下启用合并没有用，因为[!DNL Commerce]使用RequireJS。 如果未启用捆绑包，[!DNL Commerce]只合并RequireJS及其配置。 启用绑定和合并后，[!DNL Commerce]将创建单个[!DNL JavaScript]文件：

![真实世界合并](../assets/performance/images/magentoMergingDevWorld.png)

## 真实世界渲染时间

在开发环境中，之前的捆绑和合并加载时间看起来非常好。 但在现实世界中，很多事情会减慢渲染速度：连接速度慢，连接阈值大，网络有限。 此外，移动设备的呈现速度不如台式机。

要测试和准备店面部署以进行现实世界测试，我们建议您使用Chrome的本机限制配置文件“慢3G”进行测试。 通过Slow 3G，我们以前捆绑的输出时间现在反映了许多用户的连接现实：

![现实世界捆绑](../assets/performance/images/magentoBundlingRealWorld.png)

在3G连接速度较慢的情况下，大约需要44秒才能加载干净的[!DNL Commerce]安装的主页的所有包。

将捆绑包合并到单个文件中时也是如此。 用户仍可以等待约42秒的时间进行初始页面加载，如下所示：

![真实世界合并](../assets/performance/images/magentoMergingRealWorld.png)

通过更高级的[!DNL JavaScript]捆绑方法，我们可以缩短这些加载时间。

## 高级捆绑

请记住，[!DNL JavaScript]捆绑的目标是减少浏览器中加载的每个页面所请求的资产的数量和大小。 为此，我们希望构建捆绑包，以便商店中的每个页面只需要下载一个通用捆绑包和一个针对所访问每个页面的页面特定捆绑包。

实现此目标的一种方法是按页面类型定义捆绑包。 您可以将[!DNL Commerce]的页面划分为多种页面类型，包括“类别”、“产品”、“CMS”、“客户”、“购物车”和“结账”。 分类为其中一种页面类型的每个页面都具有一组不同的RequireJS模块依赖项。 当按页面类型捆绑RequireJS模块时，最终将只有少数捆绑包覆盖存储中任何页面的依赖项。

例如，最终可能会有一个用于所有页面所共有依赖项的捆绑包、一个用于仅CMS页面的捆绑包、一个用于仅目录页面的捆绑包、另一个用于仅搜索页面的捆绑包，以及一个用于签出页面的捆绑包。

您还可以按用途创建包：用于常见功能、产品相关功能、配送功能、结账功能、税费和表单验证。 如何定义捆绑包取决于您以及商店的结构。 您可能会发现某些捆绑式策略比其他策略效果更好。

干净的[!DNL Commerce]安装允许通过按页面类型拆分捆绑包来实现足够的良好性能，但某些自定义可能需要更深入的分析和其他资产分配。

### 所需工具

要执行以下步骤，您必须安装并熟悉以下工具：

- [节点](https://nodejs.org/en/download/)
- [r.js](http://requirejs.org/docs/optimization.html#download)
- [[!DNL PhantomJS]](https://phantomjs.org/) （可选）

### 示例代码

可在此处找到本文中使用的示例代码的完整版本：

- [build.js](../assets/performance/code-samples/build.js)
- [deps.js](../assets/performance/code-samples/deps.js)
- [deps-map.sh](../assets/performance/code-samples/deps-map.sh.txt)

### 第1部分：创建捆绑配置

#### 1\。 添加build.js文件

在`build.js`根目录中创建[!DNL Commerce]文件。 此文件将包含捆绑包的整个生成配置。

```javascript
({
    optimize: 'none',
    inlineText: true
})
```

稍后，我们将将`optimize:`设置从_ `none`更改为`uglify2`以缩小包输出。 但现在，在开发过程中，您可以将其保留为`none`以确保更快的生成。

#### 2\。 添加RequireJS依赖项、填充项、路径和映射

将以下RequireJS生成配置节点`deps`、`shim`、`paths`和`map`添加到您的生成文件中：

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

在此步骤中，您需要将存储的`deps`文件中的所有多个`shim`、`paths`、`map`和`requirejs-config.js`配置节点聚合到`build.js`文件中的相应节点中。 为此，您可以在浏览器的“开发人员工具”面板中打开&#x200B;**[!UICONTROL Network]**&#x200B;选项卡，然后导航到应用商店中的任何页面，如主页。 在“网络”选项卡中，您将在顶部附近看到应用商店的`requirejs-config.js`文件实例，该实例在此处突出显示：

![RequireJS配置](../assets/performance/images/RequireJSConfig.png)

在此文件中，您将找到每个配置节点(`deps`、`shim`、`paths`、`map`)的多个条目。 您需要将这些多个节点值聚合到build.js文件的单个配置节点中。 例如，如果存储区的`requirejs-config.js`实例包含15个单独的`map`节点的条目，则需要将所有15个节点的条目合并到`map`文件中的单个`build.js`节点中。 `deps`、`shim`和`paths`节点同样如此。 如果没有脚本来自动执行此过程，则可能需要一些时间。

您需要将配置节点`mage/requirejs/text`中的路径`requirejs/text`更改为`paths`，如下所示：

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

在`build.js`文件末尾，添加模块[]数组作为稍后您将为店面定义的捆绑包的占位符。

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

您可以使用以下方式从存储区的页面类型检索所有[!DNL RequireJS]模块依赖项：

1. 命令行[!DNL PhantomJS]（假设您已安装[!DNL PhantomJS]）。
1. 在浏览器的控制台中需要JS命令。

#### 要使用[!DNL PhantomJS]：

在[!DNL Commerce]根目录中，创建一个名为`deps.js`的新文件并复制下面的代码。 此代码使用[！DNL [!DNL PhantomJS]]打开一个页面，并等待浏览器加载所有页面资产。 然后，它输出给定页面的所有[!DNL RequireJS]依赖项。

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

打开[!DNL Commerce]根目录中的终端，并对存储中表示特定页面类型的每个页面运行脚本：

<pre>
phantomjs deps.js <i>指向特定页面的url</i> &gt; <i>text-file-representing-pagetype-dependencies</i>
</pre>

例如，下面是Luma主题示例存储中的四个页面，这些页面表示我们将用于创建四个包（主页、类别、产品、购物车）的四种页面类型：

```
phantomjs deps.js http://m2.loc/ > bundle/homepage.txt
phantomjs deps.js http://m2.loc/women/tops-women/jackets-women.html > bundle/category.txt
phantomjs deps.js http://m2.loc/beaumont-summit-kit.html > bundle/product.txt
phantomjs deps.js http://m2.loc/checkout/cart/?SID=m2tjdt7ipvep9g0h8pmsgie975 > bundle/cart.txt (prepare a shopping cart)
..............
```

#### 要使用浏览器控制台，请执行以下操作：

如果您不想使用[!DNL PhantomJS]，则可以在查看店面中的每种页面类型时从浏览器的控制台运行以下命令：

```shell
Object.keys(window.require.s.contexts._.defined)
```

此命令（在[!DNL PhantomJS]脚本中使用）创建[!DNL RequireJS]依赖项的相同列表并在浏览器控制台中显示它们。 此方法的缺点是，您必须创建自己的包/页面类型文本文件。

#### 6\。 设置输出格式并筛选

将[!DNL RequireJS]依赖项合并到页面类型文本文件后，您可以对每个页面类型依赖项文件使用以下命令，将文件中的逗号替换为换行符：

```bash
sed -i -e $'s/,/\\\n/g' bundle/category.txt
sed -i -e $'s/,/\\\n/g' bundle/homepage.txt
sed -i -e $'s/,/\\\n/g' bundle/product.txt
....
```

您还应该删除每个文件的所有mixin，因为mixin重复依赖项。 对每个依赖关系文件使用以下命令：

```bash
sed -i -e 's/mixins\!.*$//g' bundle/homepage.txt
sed -i -e 's/mixins\!.*$//g' bundle/category.txt
sed -i -e 's/mixins\!.*$//g' bundle/product.txt
...
```

#### 7\。 识别独特和常见的捆绑包

目标是创建所有页面所需的[!DNL JavaScript]个文件的公共包。 这样，浏览器只需加载通用捆绑包以及一个或多个特定页面类型。

打开[!DNL Commerce]根目录中的终端，然后使用以下命令验证您是否具有可以拆分为单独捆绑包的依赖项：

```bash
sort bundle/*.txt |uniq -c |sort -n
```

此命令合并和排序`bundle/*.txt`文件中找到的依赖项。  输出还显示包含每个依赖项的文件数：

```
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

此输出显示`buildTools`仅在bundle/*.txt文件中的一个文件中为依赖项。 `jquery/jquery.metadata`依赖项位于两(2)个文件中，`es6-collections`位于三(3)个文件中。

我们的输出仅显示三种页面类型（主页、类别和产品），这告诉我们：

- 三个依赖项仅对一种页面类型具有唯一性（由数字1显示）。
- 两种页面类型（如数字2所示）上还存在着三种依赖关系。
- 最后三个依赖项对于我们所有的三种页面类型都是通用的（如数字3所示）。

这告诉我们，一旦我们知道哪些页面类型需要哪些依赖项，就可以将依赖项拆分为不同的捆绑包，从而有可能提高商店的页面加载速度。

#### 8\。 创建依赖项分发文件

要了解哪些页面类型需要依赖项，请在[!DNL Commerce]根目录中创建一个名为`deps-map.sh`的新文件，并复制下面的代码：

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

您还可以在[https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html](https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html)找到该脚本

在[!DNL Commerce]根目录中打开终端并运行文件：

```bash
bash deps-map.sh
```

此脚本的输出应用于我们的三个示例页面类型，应当类似于这样（但时间更长）：

```
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

#### 9\。 在build.js文件中创建包

打开`build.js`配置文件并将您的捆绑包添加到`modules`节点。 每个包应定义以下属性：

- `name` — 包的名称。 例如，名称`bundles/cart`在`cart.js`子目录中生成`bundles`包。

- `create` — 用于创建捆绑包的布尔标记（值： `true`或`false`）。

- `include` — 作为页面的依赖项包括的一组资源（字符串）。 RequireJS跟踪所有依赖关系，并将它们包含在捆绑包中，除非排除这些依赖关系。

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

此示例重复使用`mage/bootstrap`和`requirejs/require`资源，对其必须同步加载的最重要的组件和组件赋予更高的优先级。 提供的捆绑包包括：

- `requirejs/require` — 唯一同步加载的包
- `mage/bootstrap` — 带有UI组件的引导程序捆绑包
- `bundles/default` — 所有页面都需要默认捆绑包
- `bundles/cart` — 购物车页面所需的捆绑包
- `bundles/shipping` — 购物车和结帐页面的通用捆绑包（假设从未直接打开结帐，那么如果以前打开了购物车页面并且已经加载了装运捆绑包，则结帐页面的加载速度会更快）
- `bundles/checkout` — 用于结账的所有内容
- `bundles/catalog` — 产品和类别页面的所有内容

### 第2部分：生成包

以下步骤描述了生成更高效的[!DNL Commerce]捆绑包的基本流程。 您可以按照所需的任何方式自动执行此过程，但您仍需要使用`nodejs`和`r.js`来实际生成捆绑包。 如果您的主题具有与[!DNL JavaScript]相关的自定义项并且无法重用相同的`build.js`文件，则可能需要为每个主题创建多个`build.js`配置。

#### 1.生成静态存储站点

在生成捆绑包之前，请运行静态部署命令：

```bash
php -f bin/magento setup:static-content:deploy -f -a frontend
```

此命令为您设置的每个主题和区域设置生成静态存储部署。 例如，如果您使用Luma主题和一个自定义主题，其中包含英语和法语的区域设置，则会生成四个静态部署：

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

然后从`build.js`的根目录对[!DNL Commerce]文件运行r.js优化程序。 所有目录和文件的路径均相对于工作目录。

```bash
r.js -o build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

此命令在目标目录的`bundles`子目录中生成包，在本例中结果为`pub/static/frontend/Magento/luma/en_US/bundles`。

列出新包目录的内容可能如下所示：

```bash
ll pub/static/frontend/Magento/luma/en_US/bundles
```

```
total 1900
drwxr-xr-x  2 root root    4096 Mar 28 11:24 ./
drwxr-xr-x 70 root root    4096 Mar 28 11:24 ../
-rw-r--r--  1 root root  116417 Mar 28 11:24 cart.js
-rw-r--r--  1 root root  187090 Mar 28 11:24 catalog.js
-rw-r--r--  1 root root  307619 Mar 28 11:24 checkout.js
-rw-r--r--  1 root root 1240608 Mar 28 11:24 default.js
-rw-r--r--  1 root root   74233 Mar 28 11:24 shipping.js
```

#### 4.配置RequireJS以使用捆绑包

要获取RequireJS以使用您的包，请在`onModuleBundleComplete`文件中的`modules`节点之后添加`build.js`回调：

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

在`requirejs-config.js`目录中打开`pub/static/frontend/Magento/luma/en_US`以验证RequireJS是否将该文件附加到捆绑配置调用：

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
>配置捆绑包时，请确保按照您想要的顺序来执行`requirejs.config()`调用，因为这些调用的执行顺序与它们出现的顺序相同。

#### 6.测试结果

加载页面后，请注意浏览器加载了不同的依赖项和捆绑包。 例如，以下是“慢3G”配置文件的结果：

![快一倍](../assets/performance/images/TwiceAsFast.png)

空主页的页面加载时间现在比使用本机[!DNL Commerce]捆绑快一倍。 但是我们可以做得更好。

#### 7.优化包

即使gzipped，[!DNL JavaScript]文件仍然很大。 使用RequireJS来缩小它们，后者使用修饰符来缩小[!DNL JavaScript]以获得良好的结果。

要在`build.js`文件中启用优化程序，请添加`uglify2`作为`build.js`文件顶部的优化属性的值：

```javascript
({
    optimize: 'uglify2',
    inlineText: true
})
```

结果可能非常可观：
![快三倍](../assets/performance/images/ThreeTimesFaster.png)

加载时间现在比使用本机[!DNL Commerce]捆绑快三倍。
