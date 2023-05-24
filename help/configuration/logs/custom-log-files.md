---
title: 写入自定义日志文件
description: 了解如何设置自定义日志文件。
feature: Configuration, Logs
badge: label="Contributed by Atwix" type="Informational" url="https://www.atwix.com/" tooltip="Atwix"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# 写入自定义日志文件

此 `Magento\Framework\Logger` 模块包含以下处理程序类：

| 类 | 日志文件 |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

您可以在 `lib/internal/Magento/Framework/Logger/Handler` 目录。

您可以使用以下方法之一登录到自定义文件：

- 在中设置自定义日志文件 `di.xml`
- 在自定义记录器处理程序类中设置自定义文件

## 在中设置自定义日志文件 `di.xml`

此示例说明如何使用 [虚拟类型](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 以记录 `debug` 消息放入自定义日志文件而不是标准日志文件 `/var/log/debug.log`.

1. 在 `di.xml` 文件，将自定义日志文件定义为 [虚拟类型](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   此 `name` 值 `Magento\Payment\Model\Method\MyCustomDebug` 必须是唯一的。

1. 在另一个中定义处理程序 [虚拟类型](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 具有唯一 `name`：

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. 插入 `MyCustomLogger` [虚拟类型](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 在 `Magento\Payment\Model\Method\Logger` 对象：

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. 虚拟类 `Magento\Payment\Model\Method\MyCustomDebug` 被注入到 `debug` 的处理程序 `$logger` 中的属性 `Magento\Payment\Model\Method\Logger` 类。

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

异常消息将记录到 `/var/log/payment.log` 文件。

## 在记录器处理程序类中设置自定义日志文件

此示例说明如何使用自定义记录器处理程序类进行记录 `error` 将消息写入特定日志文件。

1. 创建记录数据的类。 在此示例中，类定义于 `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`.

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

1. 将此类的处理程序定义为 [虚拟类型](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 在模块的 `di.xml` 文件。

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

1. 在 `type` 定义，指定插入自定义记录器处理程序的类名。 使用上一步中的虚拟类型名称作为此类型的参数。

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   的源代码 `Vendor\ModuleName\Observer\MyObserver` 类：

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

1. 类 `Vendor\ModuleName\Logger\Handler\ErrorHandler` 被注入到 `error` 的处理程序 `$logger` 中的属性 `Vendor\ModuleName\Observer\MyObserver`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

异常消息记录在 `/var/log/my_custom_logger/error.log` 文件。

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
