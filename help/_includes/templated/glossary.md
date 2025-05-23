---
source-git-commit: 0d5eeb691281d7c62aa64a9d8cd042f18504a67f
workflow-type: tm+mt
source-wordcount: '6370'
ht-degree: 0%

---
# Adobe Commerce术语表

## A

### 在折页的上方

_形容词_

在浏览器窗口中，在加载网页之后以及用户向下滚动页面之前立即可见的内容。
在设计布局时，请使用灵活的格式以最好的方式显示此区域中优先级最高的产品、功能、销售、通知、选项等。

使用手机和平板电脑时，折页上方区域存在显着差异，尤其是在屏幕大小和尺寸以及查看时的方向（纵向与横向）上。
使用响应式主题和测试有助于找到内容和布局的正确组合。

_术语属性：_

* _字段：设计_

### 活动分支

_名词_

活动分支或环境是指连接到可访问服务的已部署或正在运行的实例的分支或环境。
当您停用时，与服务和正在运行的实例的连接将被删除，但代码会保留。
它会变成一个普通的Git分支。

_术语属性：_

* _字段： cloud_

### 适配器

_名词_

一个类，它使两个在其他情况下不兼容的系统能够协同工作，而无需修改系统的源代码。
例如，数据库适配器、高速缓存适配器、文件系统适配器、后处理器库适配器以及其他类型的计算适配器。

_术语属性：_

* _字段：编程_

### 管理员

_名词_

在软件中，具有管理所有功能的完全管理员权限的用户角色。
在Adobe Commerce中，管理员用户拥有对管理员中所有功能、选项和功能的完全权限和访问权限。
他们还可以创建用户和角色。

了解详情：[添加用户](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html?lang=zh-Hans)

_术语属性：_

* _字段：商务软件_
* _同义词：管理员，超级用户_
* _相关术语：商务管理员_

### 管理区域

_名词_

商店的受密码保护的后台，在此可管理订单、目录、内容和配置。
用户可访问管理区域来管理商店，包括产品、订单、发货、CMS内容、店面设计、客户信息等。
管理员用户具有一个关联的角色，该角色具有控制对功能、选项和功能访问权限的权限。

了解详情：[Adobe Commerce用户指南](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html?lang=zh-Hans)

_术语属性：_

* _字段：商务软件_
* _同义词：管理员、管理面板、后端、管理界面、管理UI_
* _相关术语： admin_

### 管理员变量

_名词_

管理员变量是项目环境变量，用于覆盖管理员用户帐户的配置设置以访问管理员UI。

了解详情：[管理员变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=zh-Hans)

_术语属性：_

* _字段：管理员，云_

### adminhtml

_名词_

分配给管理员的内部区域名称。

了解详情：[Adobe Commerce用户指南](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html?lang=zh-Hans)

_术语属性：_

* _字段：商务软件_
* _相关术语：区域，商务管理员_

### 区域

_名词_

区域是Magento应用范围的抽象术语。
区域是组织代码以便优化请求处理的逻辑组件。
区域减少了从店面访问的配置对象的内存需求，并且它们通过仅加载所需的依赖代码来简化Web服务调用。
每个区域可以包含完全不同的代码以处理URL和请求。

Adobe Commerce领域包括：

* 管理员(adminhtml)
* 店面
* Web API REST (webapi_rest)

_术语属性：_

* _字段：商务软件_
* _相关术语：商务组件，店面_

### 属性

_名词_

描述产品某些方面的产品特性或属性。
Adobe Commerce用户可以创建自定义属性，以添加到默认属性集或自定义属性集。
通过管理员或以编程方式创建这些属性。
示例：颜色、大小、重量、价格、年龄、性别等。

自定义属性是一种实体属性值(EAV)属性。

对于Google购物广告渠道和AmazonSales Channel等集成，您可以将Commerce属性映射到第三方中的属性，以正确显示和销售产品、显示广告。

了解详情：[EAV和extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_术语属性：_

* _字段：商务软件，产品_
* _同义词：产品属性，自定义属性_
* _相关术语：扩展属性_

### 属性组

_名词_

属性集中属性的逻辑分组。

_术语属性：_

* _字段：商务软件_
* _相关术语：属性_

### 属性集

_名词_

为特定产品自定义的属性组集合。
示例：T恤属性集可能包括颜色、大小、性别和品牌。

_术语属性：_

* _字段：商务软件，产品_
* _相关术语：属性_

### 平均库存成本

_名词_

产品价格，减去优惠券或折扣，加上运费和适用税。
平均数通过将每月库存的起始成本加上期间最后一个月库存的终止成本相加来确定。

_术语属性：_

* _字段：产品、定价、库存_

## B

### 基础货币

_名词_

所有在线付款的每次商店视图使用的主要货币。
商店可以接受来自全球200多个国家的货币。
店面为特定国家/地区或区域设置的多个接受货币提供了一个货币选择器。
货币符号出现在产品价格和销售文档中，如订单和发票。
您可以根据需要自定义货币符号，并为每个商店或视图单独设置价格的显示。

了解详情： [货币](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency.html?lang=zh-Hans)

_术语属性：_

* _字段：定价_

### 批次处理

_名词_

执行一项任务或同时更改多个项目，而无需手动重复。

_术语属性：_

* _字段：编程_
* _同义词：批量操作_

### 块

_名词_

一个页面输出单位，可为最终用户呈现某些独特内容（一段信息、一个用户界面元素）以及任何视觉上可见的内容。
[块](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html?lang=zh-Hans)由模块实现和提供。
块使用模板生成HTML。
数据块的示例包括类别列表、迷你购物车、产品标记和产品列表。

[动态块](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/dynamic-blocks/dynamic-blocks.html?lang=zh-Hans)提供基于逻辑的内容，如价格规则。

页面生成器扩展了[块](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/block.html?lang=zh-Hans)和[动态块](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/dynamic-block.html?lang=zh-Hans)的交互性和创建。

_术语属性：_

* _字段：商务软件_
* _同义词：动态块_
* _相关术语： cms块、静态块、容器、布局_

### 品牌

_名词，动词_

由制造商或Designer定义特定产品或产品组的唯一标识。
这些品牌包括服装、家用电器、奢侈品等名牌。
您的公司也可以是品牌，根据业务单元、目标受众等在多个品牌下销售产品。

使用自定义属性保存产品的品牌信息。

例如，Google购物广告渠道和AmazonSales Channel等，某些扩展和集成可能会为您的产品使用或要求使用品牌。

_术语属性：_

* _字段：业务_

### 实体砂浆

_形容词_

具有永久物理位置的零售业务，与通过互联网几乎或完全运作的业务不同。

对于[Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html?lang=zh-Hans)和[Order Management](#oms)，此商店是跟踪产品数量、送货订单和支持店内提货的来源。

_术语属性：_

* _字段：业务，库存_

### 批量操作

_名词_

批量操作是大规模执行的操作。
批量操作任务示例包括导入或导出物料、批量更改价格以及将产品分配给仓库。

了解详情： [DevDocs批量操作](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

_术语属性：_

* _字段：编程_

### 捆绑产品

_名词_

允许客户从各种选项和配置中组装“构建您自己的”可定制产品。
捆绑包中的每个项目都是单独的简单或虚拟产品。

了解更多： [可配置产品](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html?lang=zh-Hans)

_术语属性：_

* _字段：商务软件，产品_
* _相关术语：简单产品、虚拟产品、产品类型_

### 捆绑扩展

_名词_

扩展或自定义Adobe Commerce行为的代码被视为捆绑扩展。
它可以包含模块、主题和语言包。

_术语属性：_

* _字段：捆绑扩展，扩展_
* _同义词：扩展_
* _相关术语：扩展，供应商捆绑的扩展_

## C

### 缓存后端

_名词_

在Zend的默认框架中将缓存记录存储到二级后端系统中。
第一级缓存速度快（例如APC或Memcached后端），但受限，并且不支持标记和分组缓存条目。
二级缓存（例如，文件系统或Redis后端）较慢，但支持标记和分组。

_术语属性：_

* _字段：编程_
* _相关术语：后端_

### 缓存前端

_名词_

指定在缓存后端中存储哪种类型的数据。

_术语属性：_

* _字段：编程_
* _相关术语：前端_

### 缓存类型

_名词_

缓存存储数据，以便将来调用该数据时能更快地加载。

Adobe Commerce包括以下类型：
* 配置
* 版面
* 阻止HTML输出
* 收藏集数据
* 反射数据
* 数据库DDL操作
* 已编译的配置
* EAV类型和属性
* 客户通知
* 集成配置
* 集成API配置
* 页面缓存（最著名的）
* Web服务配置
* 翻译
* Target规则
* Google产品缓存
* 顶点

可以创建和定义其他类型。

_术语属性：_

* _字段：编程_

### capture

_谓词_

将授权订单金额转换为可开单事务处理的流程。
只有在获得授权后才能获取事务处理，并且在货物或服务发运后才能获取授权。

_术语属性：_

* _字段：业务_
* _相关术语：授权，订单状态_

### 持卡人

_名词_

金融机构授权在信用卡账户中进行购买的人员。

_术语属性：_

* _字段：商业，订单_

### 购物车规则

_名词_

应用于购物车并触发操作以响应一组条件的价格规则。
用于创建促销活动。

_术语属性：_

* _字段：商务软件，定价，产品_
* _相关术语：目录规则，购物车_

### 目录

_名词_

对于商家而言，目录代表其产品库存。
在Adobe Commerce架构中，目录由类别、产品和产品属性组成。

每个Commerce商店只有一个产品目录，所有商店视图都共享该产品目录。
在多存储安装中，每个存储可以有一个单独的目录，也可以共享该目录。
当前商店目录由默认根类别确定，用户可在商店的顶部导航（主菜单）中看到该目录。
（术语“根类别”可能会让人感到困惑，因为“根类别”实际上根本不是类别，而是菜单的容器，由类别和子类别组成。）

您可以创建任意多个根类别，但一次只能使用一个（默认值）。

_术语属性：_

* _字段：商务软件，定价，产品_
* _相关术语：共享目录，目录规则_

### 目录规则

_名词_

应用于特定产品并触发操作以响应一组条件的价格规则。
用于创建促销活动。

_术语属性：_

* _字段：商务软件，定价，产品_
* _相关术语：购物车规则，目录_

### 类别

_名词_

一组具有共同点的产品。
商店的主菜单被组织成产品的类别和子类别。

_术语属性：_

* _字段：商务软件，产品_

### 结账

_名词_

收集完成购物车中商品购买所需的付款和运送信息的过程。
客户查看信息并提交订单后，会向客户发送电子邮件确认。

签出具有许多现成可用的选项和配置，并且可通过扩展实现。

了解更多： [查看教程](https://developer.adobe.com/commerce/php/tutorials/frontend/custom-checkout/)

_术语属性：_

* _字段：商业、设计、订购、产品、编程_

### 云变量

_名词_

云变量是特定于云基础架构上的Adobe Commerce的环境变量，并使用&#x200B;**`MAGENTO_CLOUD`**&#x200B;前缀。

了解更多： [云变量](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html?lang=zh-Hans)

_术语属性：_

* _字段： cloud_

### CMS块

_名词_

[块](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html?lang=zh-Hans)的特殊变体，只能在Admin中创建，不能通过布局文件引用。

_术语属性：_

* _字段：商务软件_
* _相关术语：块，静态块_

### 复杂数据

_名词_

与多个产品选项关联的数据。

_术语属性：_

* _字段：编程_

### 组件

_名词_

用于引用Adobe Commerce中的模块、主题或语言包。

_术语属性：_

* _字段：商务软件_
* _同义词：组件_
* _相关术语： ui组件_

### 可配置产品

_名词_

可配置产品看起来像单个产品，具有适用于每个变体的选项下拉列表。
每个选项实际上都是一个单独的简单产品，具有唯一的SKU，因此能够跟踪每个产品变体的库存。
要达到类似的效果，可以将简单的产品与自定义选项一起使用，但无法跟踪每个变体的库存。
具有多个选项的产品有时称为复合产品。

虽然可配置产品使用更多的SKU，并且最初可能需要更长的时间进行设置，但这可以节省最终所需的时间。
如果您计划拓展业务，对于具有多个选项的产品来说，可配置产品类型可能是更好的选择。

示例：有两种颜色和三种尺寸的T恤。
必须将6个变体创建为单独的产品（每个产品都有自己的SKU）。
然后，所有变体都会添加到可配置产品中，客户可以在其中选择大小和颜色，然后将其添加到购物车。

_术语属性：_

* _字段：商务软件，产品_
* _相关术语：产品类型_

### 转化率

_名词_

转化为购买者的访客所占的百分比。

_术语属性：_

* _字段：商业，订单_

### 核心层扩展

_名词_

核心层扩展包括三个用于数据存储、缓存和服务的服务节点，如OpenSearch、Elasticsearch、MariaDB和Redis。

_术语属性：_

* _字段： cloud_

### 贷项通知单

_名词_

商家向客户出具的单据，用于核销由于超额收费、返点或退货而导致的未清余额。
备忘会将资金还原到客户的帐户。

_术语属性：_

* _字段：商业，订单_

### 贷项通知单备注

_名词_

贷项通知单金额贷记至客户的详细信息。

_术语属性：_

* _字段：商业，订单_

### 贷项通知单项目

_名词_

商家为其创建贷项通知单的已开票物料。

_术语属性：_

* _字段：商业，订单_

### 交叉销售

_名词，形容词，动词_

购物车旁边显示的产品。
当客户导航到购物车页面时，这些产品显示为对购物车中已有的项目的交叉销售。
它们类似于冲动购买，比如杂志和杂货店收银机旁的糖果。

_术语属性：_

* _字段：商业、产品_
* _相关条款：追加销售_

### CVM

_名词_

“持卡人验证方法”的缩写。
一种验证客户身份的方法，通过付款处理器确认3位数或4位数信用卡安全代码。

_术语属性：_

* _字段：商业，订单_
* _同义词：持卡人验证方法_
* _相关术语：安全代码_

## D

### 数据库模式

_名词_

数据库中的数据结构。
定义数据的组织方式以及数据关系的管理方式，包括应用于数据的所有约束。
如果某个模块具有必须存储在数据库中的数据，则该模块可以包含数据库模式的片段。

_术语属性：_

* _字段：编程_
* _同义词：架构_

### 依赖注入

_名词_

一种软件设计模式，允许类指定其依赖项而无需构造它们。
此类将依赖项的注入责任委托给调用类。
用于简化测试。
要定义类的依赖关系，请编辑di.xml配置文件。

_术语属性：_

* _字段：编程_

### 部署密钥

_名词_

部署密钥是您的项目SSH公钥，它支持对Git存储库的只读或读写（如果已启用）访问。

了解更多： [安全连接](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=zh-Hans)

_术语属性：_

* _字段： cloud_

### 双重选择加入

_名词，动词_

一种电子邮件验证过程，它要求潜在订阅者完成确认其订阅意向的第二步。

_术语属性：_

* _字段：业务_

### 可下载的产品

_名词_

一种可数字下载的产品，包含下载的一个或多个文件，例如电子书、音乐、视频、软件应用程序或更新。
您可以提供专辑进行销售，并单独销售每首歌曲。
可下载的产品可以交付产品目录的电子版本。

可下载的文件可以驻留在您的服务器上，或作为URL提供给任何其他服务器或内容交付网络。

_术语属性：_

* _字段：商务软件，产品_
* _相关术语：产品类型_

### 动态内容

_名词_

由代码生成而不是从静态模板读取的内容。
在用户访问页面时最初呈现动态内容后，有时可以缓存并重用内容，而无需在重新访问时再次进行动态调用。

_术语属性：_

* _字段：设计_
* _相关术语： php_

### dynamic media URL

_名词_

系统动态生成的用于引用图像或其他媒体的URL地址。
地址直接链接到存储在服务器或内容交付网络上的资产。
要使用静态URL，请更改配置设置。
但是，如果在禁用设置时目录中包含了Dynamic Media URL，则目录中的每个引用都会成为断开的链接。
再次启用Dynamic Media URL可恢复链接。
使用Dynamic Media URL可能会影响目录搜索性能。

代码格式： media url=&quot;path/to/image.jpg&quot;

_术语属性：_

* _字段：编程_
* _相关术语：内容交付网络，url_

## E

### ece-tools包

_名词_

一组用于管理和部署Commerce应用程序的脚本和工具。 此软件包简化了云基础架构流程中的许多Adobe Commerce，包括部署到Docker环境、管理cron、验证项目配置和应用Adobe修补程序。

了解详情： [ece-tools包](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html?lang=zh-Hans)

_术语属性：_

* _字段： cli，云，部署_

### 实体

_名词_

编程中的唯一单位或对象。
包含可修改的属性或参数。
示例包括暂存（更新可以更改价格规则、产品或类别等实体）和数据库记录（其中服务合同包括发送和接收的数据结构）。

_术语属性：_

* _字段：商务软件_
* _相关术语：属性、购物车规则、目录规则_

### 实体属性值

_名词_

对于数据库实体，是一种对实体进行高效编码的数据模型。
将实体ID、属性名称和值存储为三重，这样可以随时创建新的实体属性名称。
在编码中，可用于描述实体的属性数量可以大幅扩展，但应用于给定实体的数量会最小化。
此数据模型很灵活，但速度可能较慢。

了解详情：[EAV和extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_术语属性：_

* _字段：编程_
* _同义词： eav_

### 常青内容

_名词_

保质期长或可重复使用的内容。

_术语属性：_

* _字段：业务_

### 扩展

_名词_

扩展或自定义Adobe Commerce行为的代码。
您可以选择在Commerce Marketplace或其他扩展分发系统上打包和分发扩展。
Commerce扩展可以包括模块、主题和语言包。

_术语属性：_

* _字段：商务软件_
* _相关术语：组件、模块、包_

### 扩展属性

_名词_

扩展功能，并且通常使用比自定义属性更复杂的数据类型。 这些属性不会出现在GUI中。

了解更多： [将扩展属性添加到实体](https://developer.adobe.com/commerce/php/development/components/add-attributes/)

_术语属性：_

* _字段：商务软件_
* _相关术语：属性，实体属性值_

## F

### 船上运费

_名词_

在国际航运中，该术语意味着接收方负责收取运费。
FOB可以基于原产地或目的地，并指定为托运或预付运费。

_术语属性：_

* _字段：商业、订单、定价_
* _同义词： fob_

### 前端

_形容词_

在客户端 — 服务器应用程序中，有后端和前端。
前端组件或客户端是一个界面，允许用户处理底层后端代码或与之交互。
后端代码在服务器上运行。
用户无法直接访问后端代码。
用户与店面交互，店面又使用在Commerce服务器上运行的代码。

注意：过去，店面称为“前端”，管理员称为“后端”。 不再支持此用法。

_术语属性：_

* _字段：设计，编程_
* _同义词：客户端_
* _相关术语：后端、店面、缓存前端_

### 前端属性

_名词_

从商店中客户的角度确定属性的表示和行为的属性。

_术语属性：_

* _字段：设计，编程_

### 履行

_名词_

管理客户发运的流程。

_术语属性：_

* _字段：业务_

## G

### 礼品卡

_名词_

可在商店中购买的预付卡或礼品证书。
每个礼品卡都分配了一个唯一的代码，该代码在结账时输入。
礼品卡的价值反映在礼品卡帐户余额中。
礼品卡有三种类型：

* “实物”礼品卡可以用塑料或卡片材生产，然后发运给客户。
* “虚拟”礼品卡通过电子邮件发送。
* “组合”礼品卡是两者的组合，作为实物卡发往收件人，并通过电子邮件发送。
礼品卡可以进行配置，包括产品资格选项以及未结或固定金额的选择。

在后端创建订单时，商店管理员还可以根据客户请求兑换礼品卡。

礼品卡还有助于促销，因为商店管理员可以在后端手动创建礼品卡帐户，并将礼品卡代码发送到特定客户区段。
礼品卡可以用作忠诚度计划，针对在节假日从网络商店或特定促销活动中进行大量购买的最活跃客户。

_术语属性：_

* _字段：商务软件_
* _相关术语：产品类型_

### 毛利

_名词_

产品的成本和价格之间的差额。

_术语属性：_

* _字段：业务_

### 已分组的产品

_名词_

一种产品类型，具有分组到单个页面上的多个类似的独立产品。
可以随单个产品的变体提供，也可以通过按季节或主题分组它们以创建协调集。
每个产品均可单独购买，或作为群组的一部分购买。

例如，对于有四种尺寸的刀具，所有四种刀具都可以显示在分组产品页面中。
客户可以选择他们想要的大小，并将其从此页面添加到购物车。

_术语属性：_

* _字段：商务软件，产品_
* _相关术语：简单产品，产品类型_

## H

### 句柄

_名词_

通常，句柄是引用对象的一种方式。
在Adobe Commerce中，句柄在许多位置使用，最常用于标识页面。
对于页面句柄，句柄名称派生自URL，然后用于查找和加载引用页面的布局文件。
例如，在客户模块中，有一个名为“view/frontend/layout/checkout_cart_index.xml”的布局文件。
其中，“frontend”是区域名称，“checkout_cart_index”是句柄名称，这两个名称都派生自URL。

_术语属性：_

* _字段：编程_
* _同义词：页面句柄_

### 水平缩放

_名词_

横向扩展（也称为扩展）是指向基础架构中添加更多节点或计算机以满足不断增长的需求的过程。

_术语属性：_

* _字段： cloud_

## I

### 拦截

_名词_

在PHP类的现有公共函数之前、之后或周围注入新代码的过程。

为了截取函数，插件实现了要调用的附加代码。
插件通过依赖关系注入配置文件(di.xml)与拦截点相关联。
如果在同一函数上定义了多个插件，则依赖项注入配置将定义插件的调用顺序，从而允许在不发生冲突的情况下使用多个插件。

_术语属性：_

* _字段：编程_
* _相关术语：插件_

## L

### 布局

_名词_

在Commerce页面的构建中，布局是指一系列以层次结构装配的块，表示页面的结构。

页面布局文件侧重于页面结构的最高级别（页眉、页脚、主内容区域、左侧边栏等）。
然后，布局文件将内容（块）组合到页面上的这些不同区域中。

_术语属性：_

* _字段：设计、商务软件_
* _相关术语：布局说明，块_

### 布局说明

_名词_

布局文件中的标记，描述要应用于块、容器和UI组件的结构化元素树中的更改。
单个布局文件可以包含多个布局指令。
布局指令在布局文件中以XML格式编码。

_术语属性：_

* _字段：设计，编程_
* _相关术语：布局、块、容器、用户界面组件_

### 布局更新

_名词_

用于已添加的代码片段，以修改XML布局或从其他文件导入布局说明。

_术语属性：_

* _字段：设计、商务软件_

### 许可证所有者

_名词_

许可证所有者（也称为帐户所有者）是业务组织中为Adobe Commerce on cloud infrastructure帐户管理支付和其他业务相关问题的指定人员。
此人充当与Adobe的联系人。
企业购买云基础架构订阅上的Adobe Commerce后，初始项目和代码访问权限仅可供指定为许可证所有者的人员使用。

_术语属性：_

* _字段：业务_

## M

### MAGEID

_名词_

MAGEID通常是Adobe Commerce帐户上的账单联系人(可能不是Adobe Commerce on cloud infrastructure项目的项目所有者)。
要获得对Adobe Commerce和Adobe Commerce在云基础架构包上的访问权限，您必须使用与已授予对这些包访问权限的MAGEID关联的访问密钥。

了解更多： [获取您的身份验证密钥](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html?lang=zh-Hans)

_术语属性：_

* _字段：商务软件_

### 标记

_名词_

在营销和零售中，为确定零售价而添加到项目成本的百分比。
[通过产品可自定义选项配置产品的标记](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/settings/settings-advanced-custom-options.html?lang=zh-Hans)或Markdown。

在开发中，一种计算机语言，控制文本的处理、表示和格式设置。
此外，标记标记是向CMS页面或块添加功能或内容的代码片段。

_术语属性：_

* _字段：业务，编程_
* _同义词： Markdown_

### 主环境

_名词_

在云基础架构上的Adobe Commerce上，Pro项目使用名为master的活动Platform as a Service (PaaS)环境，其中包括生产环境数据库和Web服务器的副本。

_术语属性：_

* _字段： cloud_

### 商户帐户

_名词_

在银行或金融机构中可以接受信用卡交易的帐户。

_术语属性：_

* _字段：业务_

### MFTF

_名词_

MFTF是[功能测试框架](https://developer.adobe.com/commerce/testing/functional-testing-framework/)。
它为Commerce开发人员和软件工程师（如QA专家、PHP开发人员和系统集成商）提供了一个测试框架。
开发人员和QA可以编写测试来尝试用户与Web应用程序的交互，验证功能，并自动进行回归测试。

_术语属性：_

* _字段：商务软件，编程_
* _相关术语： cms块、静态块、容器、布局_

### 模块

_名词_

更改或扩展Magento应用程序所提供功能的代码。
模块包含在目录结构中，该目录结构包含与特定功能相关的PHP和XML文件（配置、块、控制器、帮助程序、模型等），以提供独特的产品特征集合。
每个模块的目的是通过实施新功能或扩展其他模块的功能来提供特定的产品功能。
每个模块均设计为独立运行，因此包含或排除特定模块不会影响其他模块的功能。

模块还可以实施构件，构件是业务用户可以在“管理员”中自定义的页面元素。

可以禁用或删除模块，而不会破坏Magento应用程序的一致性。
一个例外：当模块依赖于其他模块时，这需要禁用或删除依赖的模块。

_术语属性：_

* _字段：商务软件_
* _相关术语： php， xml，块_

## O

### OMS

_名词_

OMS是Adobe的Order Management System产品。

>[!IMPORTANT]
>
>Adobe Commerce Order Management (OMS)的生命周期已终止，不再受支持。

OMS是一种灵活且经济实惠的解决方案，可用于从任何销售渠道管理、销售和完成库存。
OMS提供了无缝的客户体验，在提高销售额的同时降低了成本，并加快了上市时间。

OMS功能包括：

* 全球查看和管理所有库存
* 随时随地发货的能力
* 更轻松、响应更迅速的客户服务
* 更好的客户体验和忠诚度

了解详情： [存档的OMS文档站点](https://commerce-docs.github.io/oms-documentation-archive/)

_术语属性：_

* _字段：功能，商务软件，订单管理_
* _同义词：订单管理、MOM、订单管理系统、Magento Order Management_
* _相关术语：订单管理_

### 源遮蔽

_名词_

源遮蔽是一项安全功能，允许云基础架构上的Adobe Commerce阻止任何流向云基础架构（源）的非Fastly流量以防御DDoS攻击。

了解更多：[Fastly源遮蔽](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/fastly-origin-cloaking-enablement-faq.html?lang=zh-Hans)

_术语属性：_

* _字段：安全性_
* _相关术语： Web应用程序防火墙_

## P

### 页面生成器

_名词_

Page Builder是一个Commerce扩展，通过拖放预建控件来定义自定义布局，从而创建内容丰富的页面。
这些控件也称为“内容类型”。
商家无需编码体验即可设计版面和页面。
为开发人员提供扩展支持以扩展Page Builder。

了解详情：[页面生成器用户指南](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html?lang=zh-Hans)，[页面生成器DevDocs](https://developer.adobe.com/commerce/frontend-core/page-builder/)

_术语属性：_

* _字段：商务软件，设计_
* _同义词：管理员、管理面板、后端、管理界面、管理UI_
* _相关术语： admin_

### 支付网关

_名词_

支付网关是一种第三方服务，无需客户离开商家站点即可无缝处理信用卡交易。

_术语属性：_

* _字段：业务、订单、编程_

## R

### 相关产品

_名词_

一种产品选择，以奖励购买附加物品。
例如，如果客户正在查看相机的产品页面，则相关产品可能包括其他同类相机、相机壳和三脚架。

_术语属性：_

* _字段：商务软件，产品_

## S

### 销售规则

_名词_

包括购物车和目录规则，用于为促销活动定价产品。

_术语属性：_

* _字段：商务软件，产品_
* _相关术语：购物车规则，目录规则_

### 范围

_名词_

在Adobe Commerce中，范围描述设置可能影响的存储层次结构的范围。
范围可以应用于以下内容：

* 全球 — 所有网站、商店和商店视图
* 网站 — 选定的网站及其下的所有商店和商店视图
* 存储 — 选定的存储及其下的所有存储视图
* 存储视图 — 选定的存储视图。

在层级中，在较低级别应用的设置可以覆盖某些较高级别的设置。

_术语属性：_

* _字段：商务软件_

### 服务合同

_名词_

为模块定义的一组PHP接口。
服务合同包括保持数据完整性的数据接口和服务接口，所述服务接口隐藏业务逻辑细节，使其对服务请求者（例如控制器、Web服务和其他模块）不可见。
Web API可以通过配置文件绑定到服务协定。

_术语属性：_

* _字段：编程_
* _相关术语： php， web api_

### 结算

_名词_

当收购银行与发行人交换资金及所得款项存入商家账户时进行结算。

_术语属性：_

* _字段：业务_

### 共享目录

_名词_

一种功能，允许商家创建一个目录作为其整个目录或一部分目录，然后为一个或多个产品指定自定义价格。
然后，商家可以将此目录分配给一个或多个公司。

例如，一个B2B商家有三个客户，他们已为该商家的电子分发站点协商了特定费率。
通过使用共享目录功能，商家可以：

* 主目录
* 客户1目录（可能只有三个主目录中的大折扣SKU）
* Customer 2目录（可以是整个目录，10%折扣）
* 客户3目录（主目录折扣为5%至60%的几十种产品）。

_术语属性：_

* _字段：商务软件，产品_
* _相关术语：目录，b2b_

### 装运

_名词_

装运包含要交付的产品，并生成已装运订单中产品的记录。
多个发运可以与单个订单关联。

_术语属性：_

* _字段：商业，订单_

### 装运单据

_名词_

装运随附的文档。 该文档列出了投放包中的产品及其数量。

_术语属性：_

* _字段：商业，订单_

### 装运承运人

_名词_

运输软件包的公司。 常见的运营商包括UPS、FedEx、DHL和USPS。

_术语属性：_

* _字段：商业，订单_

### 购物车

_名词_

客户已选择购买但尚未购买的产品集。
还指电子商务网站的一个区域，在这些区域可以找到这些产品进行审查和结账。

_术语属性：_

* _字段：商业、设计、产品、编程_
* _同义词：购物车，购物篮_
* _相关术语：购物车规则_

### 简单产品

_名词_

最基本的产品类型，具有单个SKU的物理物料。
简单产品具有各种定价和输入控制，这使得销售产品的变体成为可能。
简单产品可与分组、捆绑和可配置产品关联使用。
具有自定义选项的简单产品有时称为复合产品。

_术语属性：_

* _字段：商务软件，产品_
* _相关术语：产品类型_

### SKU

_名词_

库存单位的缩写。
分配给产品的编号或代码，用于标识产品、选项、价格和制造商。

_术语属性：_

* _字段：商业、定价、产品、编程_
* _相关术语：共享目录_

### 启动页面

_名词_

带有产品或广告的促销页面；通常显示在主页之前。

_术语属性：_

* _字段：设计_

### 静态块

_名词_

一种模块化内容单元，用户可在CMS中将其放置到页面上以显示文本和图像，或执行代码片段。
静态块包含可编辑的内容，并可作为产品类别的登陆页面。
可以将小组件添加到静态块以提供其他功能。

_术语属性：_

* _字段：商务软件_
* _相关术语： cms块，块_

### 静态内容

_名词_

不经常更改的用户生成内容（不是由代码生成）。

_术语属性：_

* _字段：设计_
* _相关术语：动态内容_

### 静态文件

_名词_

资产集合，如主题使用的CSS、字体、图像和JavaScript。

_术语属性：_

* _字段：商务软件_

### 存储

_名词_

“商店”的Commerce范围级别是网站层次结构的第二级，如下所示：网站>商店>商店视图。
可以将商店组织为一个或多个。 每个商店可能都有自己的根类别，并且所有商店都共享目录和客户数据。

每个商店可以有多个商店视图，这些视图通常用于以不同的区域设置和语言呈现商店。

_术语属性：_

* _字段：商务软件，产品_
* _相关术语：商店视图，网站_

### 商店视图

_名词_

“商店视图”的Commerce范围级别是指网站、商店和商店视图层次结构中的第三级。
商店视图通常以不同的区域设置和语言呈现店面。
要更改商店视图，请使用标头中的商店选择器。

_术语属性：_

* _字段：商务软件，产品_
* _相关术语：商店，网站_

### 店面

_名词_

客户访问Commerce网站时体验的在线商店。

_术语属性：_

* _字段：商务软件，产品_

## T

### 税则

_名词_

产品税分类、客户税分类和税率的组合。 此规则定义要应用的计税。

_术语属性：_

* _字段：业务_

### 模板

_名词_

HTML模板或PHTML模板的简称。
PHTML文件包含将HTML标记和PHP代码混合在一起以将动态内容插入HTML。
大多数块至少有一个PHTML（模板）文件，其中包含块生成的静态HTML。
在管理员中，电子邮件和新闻稿模板将文本、图像和变量与HTML标记相结合，生成由系统发送的个性化内容。

_术语属性：_

* _字段：商务软件_
* _相关术语：块_

### 主题

_名词_

包含图形和外观信息。
自定义商店的外观。
Adobe Commerce可以在（编辑器）包中发送主题。
但是，主题可以放置在应用程序/设计下，而应用程序/设计未随包提供。
包是用于Composer的下载单元，通过Commerce Marketplace，Commerce用户可以下载CE或EE作为一系列包，其中包包含模块、主题或语言包。

_术语属性：_

* _字段：商务软件_

## U

### UI组件

_名词_

一种标记，专为Adobe Commerce软件设计，用于实现更简单、更灵活的用户界面(UI)渲染。
UI组件系统的目标包括：

* 简化布局句柄XML文件
* 将管理员用户界面元素从HTML+JavaScript移动到“纯JavaScript”自定义构件系统
* 允许从较小的组件创建更复杂的UI组件
* 将UI组件的数据预呈现为JSON，与后端数据对象紧密绑定
* 使用AJAX更新组件数据
* 介绍用于创建上述项目的新DSL

了解详情： [UI组件指南](https://developer.adobe.com/commerce/frontend-core/ui-components/)，[页面生成器](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html?lang=zh-Hans)

_术语属性：_

* _字段：编程_
* _相关术语： JavaScript、布局、组件、页面生成器_

### 向上

_名词_

[PWA Studio](https://github.com/magento/pwa-studio)在开发中使用[UPLOAD](https://developer.adobe.com/commerce/pwa-studio/guides/packages/upward/)。
UPPER是统一渐进式Web应用程序响应定义的缩写。
UPLOAD定义文件描述Web服务器如何提供和支持Progressive Web Application。

UPPER定义文件使用独立于平台的声明性语言提供有关服务器行为的详细信息。
这允许Progressive Web Application在任何技术栈栈上的任何语言的UPPER兼容服务器上运行，因为应用程序只关心来自UPPER服务器的HTTP端点行为。

UPLOAD服务器使用定义文件为来自应用程序shell的请求确定适当的进程或服务。
它描述了服务器应如何处理请求并为其构建响应。

PWA项目可以包括UPPER定义文件以指定其服务依赖关系。

_术语属性：_

* _字段：设计、商务软件、编程_
* _同义词：PWA Studio，统一渐进式Web应用程序响应定义_
* _相关术语： pwa_

## V

### 供应商捆绑扩展

_名词_

供应商生成的代码，用于扩展或自定义Commerce行为并作为第三方扩展运行，这被视为供应商捆绑扩展(VBE)。
VBE经过彻底测试，并包含在每个受支持的Adobe Commerce版本中。
VBE可以包括模块、主题和语言包。

在[供应商捆绑扩展主题](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html?lang=zh-Hans)中了解详情。

_术语属性：_

* _字段：商务扩展，供应商捆绑扩展，扩展， VBE_
* _同义词：扩展， VBE_
* _相关术语：扩展，捆绑扩展_

### 垂直缩放

_名词_

垂直扩展（扩展）是指通过添加磁盘或网络I/O、CPU或RAM来提高单个服务器或群集的处理能力。

_术语属性：_

* _字段：环境_

### 虚拟产品

_名词_

表示可以销售的非物理产品，例如会员资格、服务、保修或订阅。
虚拟产品可以单独销售，也可以作为以下产品类型的一部分包括在内：分组产品和捆绑产品。
不需要装运或盘存。

创建虚拟产品和简单产品的过程几乎相同。
但是，由于虚拟产品未发货，因此没有“重量”字段或选项可包含礼品卡。

_术语属性：_

* _字段：商务软件，产品_
* _相关术语：产品类型_

### 虚拟类型

_名词_

虚拟类型是一种将不同的依赖项插入到现有PHP类中的方法，它不会影响其他类，并且无需创建类文件。
虚拟类型只能由di.xml文件中`<type>`元素中的参数覆盖引用，在源代码中则不能引用。
它们不能被扩展，也不能作为类构造函数中的依赖项引用。

_术语属性：_

* _字段：编程_
* _相关术语： php_

## W

### 网站

_名词_

在Adobe Commerce软件中，位于商店和商店视图之上的网站层次结构的最高级别。
您可以拥有多个网站，每个网站可以拥有不同的域名。
网站可以设置为共享客户数据，也可以设置为不共享数据。

_术语属性：_

* _字段：商务软件、设计、产品_
* _相关术语：商店，商店视图_

### 构件

_名词_

[小组件](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/widgets/widgets.html?lang=zh-Hans)是一个预准备的代码片段，可用于在存储页面上的特定位置放置块、链接和动态内容。
您可以使用小组件为营销活动创建登陆页面，并在商店中的特定位置显示促销内容。
小组件还可用于为外部审阅系统、视频聊天、投票和订阅表单添加交互元素和操作块，或者为标记云和图像滑块提供导航元素。

_术语属性：_

* _字段：商业、商务软件、设计_
* _相关术语：块_
