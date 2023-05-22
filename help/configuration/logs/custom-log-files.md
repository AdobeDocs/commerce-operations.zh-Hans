---
title: 寫入自訂記錄檔
description: 瞭解如何設定自訂記錄檔。
feature: Configuration, Logs
badge: label="Contributed by Atwix" type="Informational" url="https://www.atwix.com/" tooltip="Atwix"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# 寫入自訂記錄檔

此 `Magento\Framework\Logger` 模組包含下列處理常式類別：

| 類別 | 記錄檔 |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

您可在以下連結中找到它們： `lib/internal/Magento/Framework/Logger/Handler` 目錄。

您可以使用下列其中一種方式登入自訂檔案：

- 在中設定自訂記錄檔 `di.xml`
- 在自訂記錄器處理常式類別中設定自訂檔案

## 在中設定自訂記錄檔 `di.xml`

此範例說明如何使用 [虛擬型別](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 以記錄 `debug` 將訊息放入自訂記錄檔而非標準記錄檔 `/var/log/debug.log`.

1. 在 `di.xml` 模組的檔案，將自訂記錄檔定義為 [虛擬型別](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   此 `name` 值 `Magento\Payment\Model\Method\MyCustomDebug` 必須是唯一的。

1. 在另一個中定義處理常式 [虛擬型別](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 具有唯一 `name`：

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. 插入 `MyCustomLogger` [虛擬型別](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 在 `Magento\Payment\Model\Method\Logger` 物件：

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. 虛擬類別 `Magento\Payment\Model\Method\MyCustomDebug` 會插入至 `debug` 的處理常式 `$logger` 中的屬性 `Magento\Payment\Model\Method\Logger` 類別。

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

例外狀況訊息會記錄到 `/var/log/payment.log` 檔案。

## 在記錄器處理常式類別中設定自訂記錄檔

此範例顯示如何使用自訂記錄器處理常式類別來記錄 `error` 訊息放入特定記錄檔。

1. 建立記錄資料的類別。 在此範例中，類別定義於 `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`.

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

1. 將此類別的處理常式定義為 [虛擬型別](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) 在模組的 `di.xml` 檔案。

   ```xml
   <virtualType name="MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
           </argument>
       </arguments>
   </virtualType>
   ```

   `MyCustomLogger` 是唯一識別碼。

1. 在 `type` 定義，指定插入自訂記錄器處理常式的類別名稱。 使用上一個步驟的虛擬型別名稱作為此型別的引數。

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   原始碼： `Vendor\ModuleName\Observer\MyObserver` 類別：

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

1. 類別 `Vendor\ModuleName\Logger\Handler\ErrorHandler` 會插入至 `error` 的處理常式 `$logger` 中的屬性 `Vendor\ModuleName\Observer\MyObserver`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

例外狀況訊息會記錄在 `/var/log/my_custom_logger/error.log` 檔案。

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
