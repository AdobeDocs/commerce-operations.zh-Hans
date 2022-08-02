---
title: 写入自定义日志文件
description: 了解如何设置自定义日志文件。
contributor_name: Atwix
contributor_link: https://www.atwix.com/
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---


# 写入自定义日志文件

的 `Magento\Framework\Logger` 模块包含以下处理程序类：

| 类 | 日志文件 |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

您可以在 `lib/internal/Magento/Framework/Logger/Handler` 目录访问Advertising Cloud的帮助。

您可以使用以下方法之一登录自定义文件：

- 在 `di.xml`
- 在自定义日志记录器处理程序类中设置自定义文件

## 在 `di.xml`

此示例说明了如何使用 [虚拟类型](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types) 登录 `debug` 消息传入自定义日志文件，而不是标准日志文件 `/var/log/debug.log`.

1. 在 `di.xml` 文件，将自定义日志文件定义为 [虚拟类型](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   的 `name` 值 `Magento\Payment\Model\Method\MyCustomDebug` 必须是唯一的。

1. 在另一个中定义处理程序 [虚拟类型](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types) 具有唯一 `name`:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. 插入 `MyCustomLogger` [虚拟类型](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types) 在 `Magento\Payment\Model\Method\Logger` 对象：

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. 虚拟类 `Magento\Payment\Model\Method\MyCustomDebug` 插入 `debug` 处理程序 `$logger` 属性 `Magento\Payment\Model\Method\Logger` 类。

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

例外消息已记录到 `/var/log/payment.log` 文件。

## 在记录器处理程序类中设置自定义日志文件

此示例说明如何使用自定义日志记录器处理程序类进行记录 `error` 消息传入特定日志文件。

1. 创建用于记录数据的类。 在本例中，类在 `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`.

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   namespace Vendor\ModuleName\Logger\Handler;
   
   use Magento\Framework\Logger\Handler\Base as BaseHandler;
   use Monolog\Logger as MonologLogger;
   
   /**
    * Class ErrorHandler
    */
   class ErrorHandler extends BaseHandler
   {
       /**
        * Logging level
        *
        * @var int
        */
       protected $loggerType = MonologLogger::ERROR;
   
       /**
        * File name
        *
        * @var string
        */
       protected $fileName = '/var/log/my_custom_logger/error.log';
   }
   ```

1. 将此类的处理程序定义为 [虚拟类型](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types) 的 `di.xml` 文件。

   ```xml
   <virtualType name="MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
           </argument>
       </arguments>
   </virtualType>
   ```

   `MyCustomLogger` 是唯一标识符。

1. 在 `type` 定义中，指定插入自定义日志记录器处理程序的类名称。 使用上一步中的虚拟类型名称作为此类型的参数。

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   源代码 `Vendor\ModuleName\Observer\MyObserver` 类：

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   declare(strict_types=1);
   
   namespace Vendor\ModuleName\Observer;
   
   use Psr\Log\LoggerInterface as PsrLoggerInterface;
   use Exception;
   use Magento\Framework\Event\ObserverInterface;
   use Magento\Framework\Event\Observer;
   
   /**
    * Class MyObserver
    */
   class MyObserver implements ObserverInterface
   {
       /**
        * @var PsrLoggerInterface
        */
       private $logger;
   
       /**
        * MyObserver constructor.
        *
        * @param PsrLoggerInterface $logger
        */
       public function __construct(
           PsrLoggerInterface $logger
       ) {
           $this->logger = $logger;
       }
   
       /**
        * @param Observer $observer
        */
       public function execute(Observer $observer)
       {
           try {
               // some code goes here
           } catch (Exception $e) {
               $this->logger->error($e->getMessage());
           }
       }
   }
   ```

1. 类 `Vendor\ModuleName\Logger\Handler\ErrorHandler` 插入 `error` 处理程序 `$logger` 属性 `Vendor\ModuleName\Observer\MyObserver`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

例外消息记录在 `/var/log/my_custom_logger/error.log` 文件。

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
