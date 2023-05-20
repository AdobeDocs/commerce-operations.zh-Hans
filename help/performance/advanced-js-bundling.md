---
title: 進階 [!DNL JavaScript] 套裝
description: 瞭解JavaScript套件組合如何減少伺服器請求的大小和頻率。
exl-id: 81a313f8-e541-4da6-801b-8bbd892d6252
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2137'
ht-degree: 0%

---

# 進階 [!DNL JavaScript] 套裝

套裝 [!DNL JavaScript] 改善效能的模組需要減少兩件事：

1. 伺服器要求的數目。
1. 這些伺服器要求的大小。

在模組化應用程式中，伺服器要求的數量可能高達數百個。 例如，下列熒幕擷取畫面只會顯示 [!DNL JavaScript] 在全新安裝的首頁上載入的模組。

![無套件組合](../assets/performance/images/noBundling.png)

## 合併和捆綁

開箱即用 [!DNL Commerce] 提供兩種減少伺服器請求數的方法：合併和捆綁。 這些設定預設為關閉。 您可以在下列位置的管理員UI中將其開啟： **[!UICONTROL Stores]** > **設定** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL [!DNL JavaScript] Settings]**，或從命令列。

![套裝](../assets/performance/images/bundlingImage.png)

### 基本組合

若要從命令列啟用內建組合：

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

這是原生檔案 [!DNL Commerce] 此機制結合系統中存在的所有資產，並將它們分散在大小相同的組合(bundle_0.js、bundle_1.js ... bundle_x.js)中：

![[!DNL Commerce] 套裝](../assets/performance/images/magentoBundling.png)

雖然更好，但瀏覽器仍會載入 [!DNL JavaScript] 套件組合，而不只是需要的套件組合。

[!DNL Commerce] 套件組合可減少每頁的連線數量，但對於每個頁面請求，它會載入所有套件，即使請求的頁面可能僅取決於一或兩個套件組合中的檔案。 在瀏覽器快取套件組合後，效能得以改善。 但是，由於瀏覽器會同步載入這些套件組合，因此使用者的第一次造訪會是 [!DNL Commerce] storefront可能需要一些時間才能呈現，並損害使用者體驗。

### 基本合併

若要從命令列啟用內建合併：

```bash
php -f bin/magento config:set dev/js/merge_files 1
```

此命令會合併所有同步 [!DNL JavaScript] 檔案合併為一個檔案。 啟用合併而不啟用繫結沒有用處，因為 [!DNL Commerce] 使用RequireJS。 如果您未啟用套件組合， [!DNL Commerce] 僅合併RequireJS及其設定。 當您同時啟用套件和合併時， [!DNL Commerce] 建立單一 [!DNL JavaScript] 檔案：

![真實世界合併](../assets/performance/images/magentoMergingDevWorld.png)

## 真實世界轉譯時間

之前的套件和合併載入時間在開發環境中看起來很棒。 但在現實世界中，許多因素都會拖慢呈現速度：連線緩慢、連線臨界值大、網路有限。 此外，行動裝置的呈現速度不如桌上型電腦。

為了測試和準備您的店面部署以進行現實世界的測試，我們建議您使用Chrome的原生節流設定檔「慢3G」進行測試。 透過Slow 3G，我們先前提供的輸出時間能反映許多使用者的連線實際情況：

![現實世界的套裝](../assets/performance/images/magentoBundlingRealWorld.png)

在3G連線速度緩慢的情況下，載入全新首頁的所有套件組合大約需要44秒 [!DNL Commerce] 安裝。

將套件組合合併至單一檔案時，亦是如此。 使用者仍可等待約42秒才開始載入頁面，如下所示：

![真實世界合併](../assets/performance/images/magentoMergingRealWorld.png)

透過更進階的方法 [!DNL JavaScript] 套裝，我們可以縮短載入時間。

## 進階套裝

記住，目標 [!DNL JavaScript] 套件組合可針對瀏覽器中載入的每個頁面，減少請求資產的數量和大小。 為此，我們希望建立套件組合，讓商店中的每個頁面只需要下載通用的套件組合，以及每個存取頁面的頁面專屬套件組合。

達成此目標的一種方式是依頁面型別定義您的組合。 您可以分類 [!DNL Commerce]的頁面分為數種頁面型別，包括類別、產品、CMS、客戶、購物車和結帳。 分類為其中一種頁面型別的每個頁面都有一組不同的RequireJS模組相依性。 當您依頁面型別來捆綁RequireJS模組時，您最後只會看到少數幾個捆綁包，這些捆綁包涵蓋存放區中任何頁面的相依性。

例如，您最終可能會得到一個用於所有頁面通用的相依性的套件、一個用於僅CMS頁面的套件、一個用於僅目錄頁面的套件、另一個用於僅搜尋頁面的套件和一個「出庫」頁面的套件。

您也可以依用途建立套件組合：針對常見功能、產品相關功能、送貨功能、結帳功能、稅金及表單驗證。 如何定義您的套件組合取決於您和商店的結構。 您可能會發現某些套件組合策略會比其他策略更有效。

乾淨 [!DNL Commerce] 安裝可讓您透過按頁面型別分割套件組合來達到足夠的良好效能，但某些自訂可能需要更深入的分析和其他資產分佈。

### 必要工具

下列步驟需要您安裝並熟悉下列工具：

- [nodejs](https://nodejs.org/en/download/)
- [r.js](http://requirejs.org/docs/optimization.html#download)
- [[!DNL PhantomJS]](https://phantomjs.org/) （選擇性）

### 程式碼範例

本文中使用的範常式式碼完整版本可在此處取得：

- [build.js](../assets/performance/code-samples/build.js)
- [deps.js](../assets/performance/code-samples/deps.js)
- [deps-map.sh](../assets/performance/code-samples/deps-map.sh.txt)

### 第1部分：建立套件組合設定

#### 1\. 新增build.js檔案

建立 `build.js` 中的檔案 [!DNL Commerce] 根目錄。 此檔案將包含您套件組合的完整組建設定。

```javascript
({
    optimize: 'none',
    inlineText: true
})
```

稍後，我們將變更 `optimize:` 從_設定 `none` 至 `uglify2` 以縮小組合輸出。 但就目前而言，在開發期間，您可以將其保留為 `none` 以確保更快的建置。

#### 2\. 新增RequireJS相依性、墊片、路徑和對應

新增下列RequireJS組建設定節點， `deps`， `shim`， `paths`、和 `map`，至您的建置檔案：

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

#### 3\. 彙總requirejs-config.js例項值

在此步驟中，您需要彙總所有多個 `deps`， `shim`， `paths`、和 `map` 來自您商店的設定節點 `requirejs-config.js` 檔案放入中的對應節點 `build.js` 檔案。 若要這麼做，您可以開啟 **[!UICONTROL Network]** 在瀏覽器的「開發人員工具」面板中按Tab鍵，然後導覽至商店中的任何頁面，例如首頁。 在「網路」標籤中，您會看到商店的執行個體 `requirejs-config.js` 頂部附近的檔案，在這裡反白顯示：

![RequireJS設定](../assets/performance/images/RequireJSConfig.png)

在此檔案中，您會找到每個設定節點的多個專案(`deps`， `shim`， `paths`， `map`)。 您需要將這些多個節點值彙總到您的build.js檔案的單一設定節點中。 例如，若您的商店在 `requirejs-config.js` 執行個體有15個獨立專案 `map` 節點，您需要將所有15個節點的專案合併為單一 `map` 節點於 `build.js` 檔案。 同樣的情況也適用於 `deps`， `shim`、和 `paths` 節點。 如果沒有指令碼來自動化此程式，則可能需要一段時間。

您需要變更路徑 `mage/requirejs/text` 至 `requirejs/text` 在 `paths` 設定節點如下：

```javascript
({
    //...
    paths: {
        //...
        "text": "requirejs/text"
    },
})
```

#### 4\. 新增模組節點

在 `build.js` 檔案，新增模組[] 陣列，作為您稍後為店面定義的套件組合的預留位置。

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

#### 5\. 擷取RequireJS相依性

您可以擷取所有 [!DNL RequireJS] 使用下列方式，從存放區的頁面型別取得模組相依性：

1. [!DNL PhantomJS] 從命令列(假設您有 [!DNL PhantomJS] 已安裝)。
1. 瀏覽器主控台中的RequireJS命令。

#### 使用 [!DNL PhantomJS]：

在 [!DNL Commerce] 根目錄，建立名為的新檔案 `deps.js` 並複製下列程式碼。 此程式碼使用[！DNL [!DNL PhantomJS]]開啟頁面並等待瀏覽器載入所有頁面資產。 然後輸出所有 [!DNL RequireJS] 指定頁面的相依性。

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

開啟內的終端機 [!DNL Commerce] 根目錄，並對存放區中代表特定頁面型別的每個頁面執行指令碼：

<pre>
phantomjs deps.js <i>url-to-specific-page</i> &gt; <i>text-file-representing-pagetype-dependencies</i>
</pre>

例如，以下是Luma主題範例商店中的四個頁面，代表我們將用來建立四個組合（首頁、類別、產品、購物車）的四個頁面型別：

```terminal
phantomjs deps.js http://m2.loc/ > bundle/homepage.txt
phantomjs deps.js http://m2.loc/women/tops-women/jackets-women.html > bundle/category.txt
phantomjs deps.js http://m2.loc/beaumont-summit-kit.html > bundle/product.txt
phantomjs deps.js http://m2.loc/checkout/cart/?SID=m2tjdt7ipvep9g0h8pmsgie975 > bundle/cart.txt (prepare a shopping cart)
..............
```

#### 若要使用瀏覽器主控台：

如果您不想使用 [!DNL PhantomJS]時，您可以從瀏覽器的主控台執行下列命令，同時檢視店面中的每個頁面型別：

```shell
Object.keys(window.require.s.contexts._.defined)
```

此命令(用於 [!DNL PhantomJS] script)建立相同的 [!DNL RequireJS] 相依性並在瀏覽器的主控台中顯示它們。 此方法的缺點在於您必須建立自己的套件/頁面型別文字檔案。

#### 6\. 格式化並篩選輸出

合併之後 [!DNL RequireJS] 相依性轉換為頁面型別文字檔案，您可在每個頁面型別相依性檔案上使用下列指令，以換行來取代檔案中的逗號：

```terminal
sed -i -e $'s/,/\\\n/g' bundle/category.txt
sed -i -e $'s/,/\\\n/g' bundle/homepage.txt
sed -i -e $'s/,/\\\n/g' bundle/product.txt
....
```

您也應該移除每個檔案的所有mixin，因為mixin重複相依性。 對每個相依性檔案使用以下命令：

```terminal
sed -i -e 's/mixins\!.*$//g' bundle/homepage.txt
sed -i -e 's/mixins\!.*$//g' bundle/category.txt
sed -i -e 's/mixins\!.*$//g' bundle/product.txt
...
```

#### 7\. 識別唯一和常見的組合

目標是建立下列專案的通用組合： [!DNL JavaScript] 所有頁面所需的檔案。 如此一來，瀏覽器只需要載入通用套件組合以及一個或多個特定頁面型別。

在中開啟終端機 [!DNL Commerce] 根目錄，並使用下列指令來驗證您是否有相依性可以分割成個別的組合：

```bash
sort bundle/*.txt |uniq -c |sort -n
```

此命令合併和排序在 `bundle/*.txt` 檔案。  輸出也會顯示包含每個相依性的檔案數：

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

此輸出會顯示 `buildTools` 只在bundle/*.txt檔案的其中一個檔案中有相依性。 此 `jquery/jquery.metadata` 相依性位於兩(2)個檔案中，且 `es6-collections` 位於三(3)個檔案中。

我們的輸出僅顯示三種頁面型別（首頁、類別和產品），這會告訴我們：

- 只有一種頁面型別有三種相依性（由數字1顯示）。
- 兩種頁面型別上還有三種相依性（如數字2所示）。
- 最後三個相依性對於我們所有的三種頁面型別都是共同的（由數字3顯示）。

這告訴我們，一旦我們知道哪些頁面型別需要哪些相依性，就可以將相依性分割成不同的套件，藉此提高市集的頁面載入速度。

#### 8\. 建立相依性散發檔案

若要瞭解哪些頁面型別需要哪些相依性，請在 [!DNL Commerce] 呼叫的根目錄 `deps-map.sh` 並複製下列程式碼中的：

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

您也可以在此找到指令碼 [https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html](https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html)

在中開啟終端機 [!DNL Commerce] 根目錄並執行檔案：

```bash
bash deps-map.sh
```

此指令碼的輸出套用至我們的三個範例頁面型別，看起來應該像這樣（但時間更長）：

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

這些資訊足以建置套件組合設定。

#### 9\. 在您的build.js檔案中建立套件組合

開啟 `build.js` 設定檔案並將您的套件組合新增至 `modules` 節點。 每個束都應該定義以下屬性：

- `name` — 束的名稱。 例如，名稱 `bundles/cart` 產生 `cart.js` 中的組合 `bundles` 子目錄。

- `create` — 建立套件組合的布林值標幟(值： `true` 或 `false`)。

- `include` — 包含作為頁面相依性的一組資產（字串）。 RequireJS會追蹤所有相依性，並將它們包含在套件中（除非排除）。

- `exclude` — 要從套件組合中排除的套件組合或資產陣列。

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

此範例會重複使用 `mage/bootstrap` 和 `requirejs/require` 資產，對於必須同步載入的最重要元件和元件設定較高的優先順序。 呈現的套件組合為：

- `requirejs/require` — 唯一同步載入的組合
- `mage/bootstrap` — 具有UI元件的啟動程式套件
- `bundles/default` — 所有頁面都需要預設套件組合
- `bundles/cart` — 購物車頁面所需的套件組合
- `bundles/shipping` — 購物車和結帳頁面的通用套件組合（假設從未直接開啟結帳，如果先前已開啟購物車頁面且已載入送貨套件組合，則結帳頁面載入速度會更快）
- `bundles/checkout` — 結帳所需的一切
- `bundles/catalog` — 產品和類別頁面的一切

### 第2部分：產生組合

以下步驟說明提高效率的基本程式 [!DNL Commerce] 套件組合。 您可以透過任何所需方式自動化此程式，但您仍需使用 `nodejs` 和 `r.js` 以實際產生您的組合。 如果您的主題有 [!DNL JavaScript] — 相關的自訂專案且無法重複使用 `build.js` 檔案，您可能需要建立多個 `build.js` 每個主題的設定。

#### 1.產生靜態存放區網站

在產生套件組合之前，請執行靜態部署命令：

```bash
php -f bin/magento setup:static-content:deploy -f -a frontend
```

此命令會為您已設定的每個主題和區域設定產生靜態存放區部署。 例如，如果您使用Luma主題和含有英文及法文地區設定的自訂主題，則會產生四個靜態部署：

- ...luma/en_US
- ...luma/fr_FR
- ...custom/en_US
- ...custom/fr_FR

若要產生所有商店主題和區域設定的組合，請對每個商店主題和區域設定重複下列步驟。

#### 2.將靜態存放區內容移至暫存目錄

首先，您必須將靜態內容從目標目錄移至某個暫存目錄，因為RequireJS會取代目標目錄中的所有內容。

```bash
mv pub/static/frontend/Magento/{theme}/{locale} pub/static/frontend/Magento/{theme}/{locale}_tmp
```

例如：

```bash
mv pub/static/frontend/Magento/luma/en_US pub/static/frontend/Magento/luma/en_US_tmp
```

#### 3.執行r.js最佳化程式

接著在「 」上執行r.js最佳化程式 `build.js` 檔案來源 [!DNL Commerce]的根目錄。 所有目錄和檔案的路徑均相對於工作目錄。

```bash
r.js -o build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

這個指令會在以下專案產生組合： `bundles` 目標目錄的子目錄，在此例中會產生 `pub/static/frontend/Magento/luma/en_US/bundles`.

列出新套件目錄的內容看起來可能像這樣：

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

#### 4.設定RequireJS使用套件組合

若要讓RequireJS使用您的套件組合，請新增 `onModuleBundleComplete` 回呼晚於 `modules` 中的節點 `build.js` 檔案：

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

#### 5.重新執行部署命令

執行以下命令以部署：

```bash
r.js -o app/design/frontend/Magento/luma/build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

開啟 `requirejs-config.js` 在 `pub/static/frontend/Magento/luma/en_US` 目錄，以驗證RequireJS是否已附加具有套件組合設定呼叫的檔案：

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
>設定套件組合時，請務必將 `requirejs.config()` 呼叫的執行順序，因為呼叫是以其出現的順序執行。

#### 6.測試結果

頁面載入後，請注意瀏覽器載入了不同的相依性和套件組合。 例如，以下是「慢3G」設定檔的結果：

![快兩倍](../assets/performance/images/TwiceAsFast.png)

空白首頁的頁面載入時間現在比使用原生快一倍 [!DNL Commerce] 套裝。 但是我們可以做得更好。

#### 7.最佳化組合

即使gzipped， [!DNL JavaScript] 檔案仍然很大。 使用RequireJS來縮制這些引數，後者會使用精簡符號來縮制 [!DNL JavaScript] 以取得良好的結果。

若要在中啟用最佳化程式 `build.js` 檔案，新增 `uglify2` 作為optimize屬性的值，在 `build.js` 檔案：

```javascript
({
    optimize: 'uglify2',
    inlineText: true
})
```

結果可能相當可觀：
![快三倍](../assets/performance/images/ThreeTimesFaster.png)

載入時間現在比原生快三倍 [!DNL Commerce] 套裝。
