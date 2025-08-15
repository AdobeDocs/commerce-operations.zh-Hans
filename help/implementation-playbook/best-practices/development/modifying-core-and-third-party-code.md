---
title: 修改核心和第三方PHP代码的最佳实践
description: 了解如何以及何时修改核心Adobe Commerce和第三方PHP代码。
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2023-12-8
exl-id: 32b3137d-fc00-4be8-ba02-5d8d48a51fe1
source-git-commit: d47567a8d69ccdae3db01e964f1db12e8ae26717
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 0%

---

# 修改或覆盖核心和第三方PHP代码的最佳实践

本文档描述了在需要修改您未创作或未直接控制的任何代码的功能、结果或输入时的最佳实践。 换言之，核心代码和第三方代码。 本文档主要介绍后端PHP代码。

## 修改代码的方法

在修改代码时，请务必考虑更改的范围。 更改的“范围”是指代码更改的影响范围。 作为最佳实践，应基于占地面积最小和资源使用最少的选项来确定最终实施的完成方式。 覆盖代码的范围越广，开发团队就越偏离核心Adobe Commerce功能，这增加了出现错误的可能性，并且未来会更加努力地维护代码库。

### Patch

修补程序是一个文件，其中包含直接更改文件内代码的说明，但该文件不在开发团队的直接控制之下。 当没有其他选项时，通常应将这一选项视为最后的手段。 修补程序旨在作为临时解决方案。 如果您必须创建补丁程序（作为一般最佳实践），请在接下来的2-4周内删除该补丁程序，以采用更永久的解决方案。 

修补程序很容易断开。 如果更新了补丁程序目标的文件，这通常会导致补丁程序停止工作。 这是因为修补程序文件包含行号和列号，它们专门指明了修补程序要更改的内容。 如果有任何内容与修补程序所预期的内容不匹配，它将停止应用并破坏代码。

```bash
diff --git a/vendor/magento/module-quote/Model/QuoteManagement.php b/vendor/magento/module-quote/Model/QuoteManagement.php
index 51b68411d40..ac4a3468322 100644
--- a/vendor/magento/module-quote/Model/QuoteManagement.php
+++ b/vendor/magento/module-quote/Model/QuoteManagement.php
@@ -424,8 +424,9 @@ class QuoteManagement implements CartManagementInterface
                 }
             }
             $quote->setCustomerIsGuest(true);
-            $groupId = $customer ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID;
-            $quote->setCustomerGroupId($groupId);
+            $quote->setCustomerGroupId(
+                $quote->getCustomerId() ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID
+            );
         }
  
         $remoteAddress = $this->remoteAddress->getRemoteAddress();
```

#### 使用修补程序可以更改的内容

任何事。 实际上，任何目标文件中的任何字符都可以更改。 修补程序不限于任何特定的文件类型或代码语言。 通常，您将使用修补程序来定位`vendor`目录中的文件。 

#### 何时使用修补程序

如果您意识到不存在其他选项。 例如，当供应商尚未发布代码修补程序时，您可以在等待永久解决方案时使用修补程序临时解决此问题。

#### 缺点

修补程序很容易断开。 当目标代码发生更改时，修补程序将停止工作。 它们只是一种短期解决方案。

### 首选项

偏好设置是设计到Adobe Commerce平台中的概念。 它本质上是一个“PHP类替换”。

Adobe Commerce平台使用“对象管理器”来实例化PHP类，因为它不会像在传统PHP应用程序中那样使用新关键字实例化PHP类。 相反，对象管理器交叉引用要针对已编译配置实例化的PHP类的名称，以确定是否有任何模块声明了对原始类的首选项。 如果找到了PHP类的首选项，则对象管理器将改为实例化指定的类。

需要注意的是，（通常）替换原始PHP类的新PHP类从原始PHP类扩展/继承。 这样做有几个原因：

- 确保遵循依赖项注入/类型提示。 否则，发生致命错误并且应用程序中断。
- 允许最小代码写入。 如果原始PHP类包含10种方法，但您只需要覆盖一种方法，则通常可以单独更改一种方法，而保留其它9种方法。 这对于确保当平台升级到新版本时不会阻止对核心功能的更新很重要。

#### 声明首选项

声明偏好设置是一个相当简单的过程。 需要将一行代码添加到模块中的`di.xml`文件中。 此操作可以在全局范围内或任何Adobe Commerce“区域”内完成，例如`frontend`、`adminhtml`、`graphql`、`webapi_rest`和`crontab`。

```xml
<preference for="Magento\Elasticsearch7\SearchAdapter\Adapter" type="Vendor\Namespace\Adapter\AlgoliaElasticSearch7Adapter"/>
```

```php
<?php

declare(strict_types=1);

namespace Vendor\Namespace\Adapter;

class AlgoliaElasticSearchAdapter extends \Magento\Elasticsearch7\SearchAdapter\Adapter
{
}
```

#### 可以使用首选项更改的内容

只有PHP类可以使用首选项覆盖。 在PHP类中，可以修改公共方法和受保护的方法和属性。 对于公共方法和受保护方法，您可以完全覆盖方法，也可以修改进入（或传出）原始父方法的参数。

技术上不能覆盖私有方法。 但是，您可以为原始私有方法创建自己的替换。 您甚至可以为它指定任意名称，也可以使用原始名称。 这无关紧要，因为私有方法仅存在于包含它的实际文件中。 要覆盖私有方法，您需要覆盖或修改调用原始私有方法的公共方法或受保护方法，并且需要替换您自己的功能。

#### 何时使用首选项

再次重申，当不存在其他选项并且无法通过依赖项注入、插件或观察器完成目标时，您应该使用首选项。 如果需要修改或覆盖私有或受保护的方法或属性，有时您可能需要首选项。 应当指出，应当谨慎使用偏好设置。 它们是一种相当的“贪婪”方法，用于更改应用程序，而且您实际上拥有了PHP类的所有权。 这可能会导致与第三方模块发生冲突，并且可能会阻止对核心类的更新，并导致难以诊断的错误。 Adobe Commerce平台经过精心设计，包括能够以较小的占用空间对底层代码进行更改的其他途径。

#### 缺点

首选项是一种修改代码的贪婪方法，只应在不存在其他选项时使用。 首选项经常会导致代码库内发生冲突，并且更糟，它们可能会阻止随平台升级发生的核心更新。 

### 观察者

观察者是一种事件侦听器的概念，在许多应用程序、平台、库和编码语言中都存在。 这个概念并不是Adobe Commerce平台特有的。 从Magento 1时代起，观察者就被植入平台，并被视为如何修改核心代码和第三方代码的主要选择。 

核心代码库和任何第三方模块都可以在代码中的选定位置发送事件。 观察程序在`events.xml`文件中声明并正在按名称侦听已调度的事件，该观察程序可以在全局级别工作，或约束到任何Adobe Commerce“区域”，如`frontend`、`adminhtml`、`graphql`、`webapi_rest`和`crontab`。

#### 如何声明观察者

可以在全局或特定于区域的`events.xml`文件中配置观察程序。

```xml
    <event name="sales_model_service_quote_submit_before">
        <observer name="set_reward_flag_order" instance="Adobe\RewardAdjustments\Observer\SetOrderRewardFlag" />
    </event>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\RewardAdjustments\Observer;

use Magento\Framework\Event\ObserverInterface;
use Magento\Framework\Event\Observer;
use Magento\Quote\Model\Quote;
use Magento\Sales\Api\Data\OrderInterface;

class SetOrderRewardFlag implements ObserverInterface
{
    /**
     * @param Observer $observer
     * @return void
     */
    public function execute(Observer $observer)
    {
        $event = $observer->getEvent();
        /* @var $order OrderInterface */
        $order = $event->getOrder();
        /** @var $quote Quote $quote */
        $quote = $event->getQuote();

        // do something to the order and/or quote object here
    }
}
```

#### 可以使用观察者进行更改的内容

观察者仅适用于Adobe Commerce平台中的PHP代码。 您只能修改通过事件调度传递的特定数据和对象。

#### 何时使用观察者

随时可用！ 如果观察家能够更广泛地获得和灵活地运作，那么观察家将占据这个名单的第二位。 与插件相比，观察器的处理开销更少，可用的插件更少，灵活性也更低。

#### 缺点

虽然观察者是截获和修改代码的绝佳方法，但必须将事件调度添加到核心代码或第三方代码中，以供您的代码监听。 这使得使用观察者的概念有点受限。 仅限开发人员有远见卓识的事件包含在代码中。

此外，观察者的另一个限制因素是，调度的事件仅提供对开发人员决定随事件一起传递的特定数据和对象的访问。

### 插件

插件是Adobe Commerce平台中引入的灵活概念。 它允许您截取、替换和修改任何公共PHP方法。 插件允许您在执行目标方法之前修改进入方法的参数，在执行目标方法之后修改结果，或者完全替换目标方法。 可以在单个插件文件中修改目标PHP类的许多方法。 此外，可以使用`$subject`参数执行目标PHP类中存在的任何公共方法。

#### 如何声明插件

可以在全局或特定于区域的`di.xml`文件中配置插件。

```xml
    <type name="Magento\Catalog\Api\CategoryRepositoryInterface">
        <plugin name="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin" type="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin"/>
    </type>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\CatalogAdjustments\Plugin;

class CategoryRepositoryPlugin
{
    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param int $categoryId
     * @param int $storeId
     *
     * @return array
     */
    public function beforeGet($subject, $categoryId, $storeId = null): array
    {
        // modify the $categoryId or $storeId arguments or perform some other functionality prior to execution of the `get` method
        return [$categoryId, $storeId];
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Closure $origMethod
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function aroundGet($subject, $origMethod, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you can do something before calling the original method
        $result = $origMethod($categoryId, $storeId);
        // here you can do something after calling the original method
        // you can also NOT call the original method at all and instead, substitute our own functionality

        return $result;
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Magento\Catalog\Api\Data\CategoryInterface $result
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function afterGet($subject, $result, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you modify the result produced by the original `get` function or you can execute some other functionality
        // note that you also have access to the original function arguments. it's too late to modify them, but if needed, they are available for reading

        return $result;
    }
}
```

#### 使用插件可以更改的内容

此功能仅适用于目标PHP类。 您可以更改公共方法的输入或输出，也可以使用插件触发其他功能。 如果多个插件针对同一个PHP类，则可以设置插件的执行排序顺序，以允许插件在其他插件之前或之后运行。

#### 何时使用插件

当依赖项替换不可用时。 插件在整个核心代码库和第三方代码中通常使用，并且通常可以在您自己的自定义代码中使用。 通常，在必须修改自定义代码不拥有或不控制的功能时，可以使用插件。

#### 缺点

无法修改受保护的方法或属性。 处理开销高于观察者。 这并非不使用插件的真正理由，差别微乎其微。 不过，这是值得牢记的事情。

### 依赖项替换

依赖项注入是一个标准的面向对象编码概念，在此概念中，使用构造函数将所需的依赖项传递到类中。 但是，Adobe Commerce平台提供了多种途径，以XML替代依赖关系，从而更进一步地实现了这一点。 本质上，依赖性替换。 依赖项替换不适用于所有情况，但它允许最小代码写入，开销较低，并且您可以仅精确定位确切的代码段。 您可以通过依赖项替换来修改私有方法和受保护方法。

#### 如何使用依赖项替换

依赖项替换可以在全局或特定区域的基础上进行。

```php
<?php

class SomeClass
{
    public function __construct(
        private readonly AllowedCountries $allowedCountriesReader
    ) {}

    /**
     * Check is address allowed for store
     *
     * @param AddressInterface $address
     * @param int|null $storeId
     * @return bool
     */
    private function isAddressAllowedForWebsite(AddressInterface $address, $storeId): bool
    {
        $allowedCountries = $this->allowedCountriesReader->getAllowedCountries(ScopeInterface::SCOPE_STORE, $storeId);

        return in_array($address->getCountryId(), $allowedCountries);
    }
}
```

```php
<?php

use Magento\Store\Model\ScopeInterface;

class OverrideAllowedCountries extends AllowedCountries
{
    /**
     * Retrieve all allowed countries for scope or scopes
     *
     * @param string $scope
     * @param string|null $scopeCode
     * @return array
     * @since 100.1.2
     */
    public function getAllowedCountries(
        $scope = ScopeInterface::SCOPE_WEBSITE,
        $scopeCode = null
    ) {
        // do some stuff here
        // you can call the original method or override it completely
        
        return $something;
    }
}
```

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Vendor\Namespace\SomeClass">
        <arguments>
            <argument name="allowedCountriesReader" xsi:type="object">OverrideAllowedCountries</argument>
        </arguments>
    </type>
</config>
```

在执行这些步骤后，您将成功修改私有方法的行为。

#### 依赖项替换可以更改的内容

公共、受保护以及私有方法可以通过依赖关系替换进行更改。 与插件类似，您可以修改传入的参数，完全替换函数，或修改函数的输出。

#### 何时使用依赖项替换

这是第一个很好的选择，当它实际能够达到预期目标时，假设不必做太复杂的操作即可实施。

#### 缺点

不是很多。 不是所有情况都能用。 主要缺点是必须扩展包含要修改的功能的原始类。 这违背了“构成高于继承”的原则。
