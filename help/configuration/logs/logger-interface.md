---
title: Logger界面
description: 日志程序界面入门。
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Logger界面

要开始使用日志程序，必须创建`\Psr\Log\LoggerInterface`的实例。 通过此界面，您可以调用以下函数将数据写入日志文件：

- [警报()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [紧急()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [错误()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [信息()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [日志()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [通知()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [警告()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

一种方法在[日志数据库活动](../logs/database-activity.md)示例中进行了说明。

另一种方式如下：

```php
class SomeModel
 {
     private $logger;

     public function __construct(\Psr\Log\LoggerInterface $logger)
     {
         $this->logger = $logger;
     }

     public function doSomething()
     {
         try {
             //do something
         } catch (\Exception $e) {
             $this->logger->critical('Error message', ['exception' => $e]);
         }
     }
 }
```

前面的示例显示`SomeModel`使用构造函数注入接收`\Psr\Log\LoggerInterface`对象。 在方法`doSomething`中，如果发生错误，则将其记录到方法`critical` (`$this->logger->critical($e);`)。

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424)定义了八个日志级别（调试、信息、通知、警告、错误、严重、警报和紧急）。
