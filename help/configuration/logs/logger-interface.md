---
title: Logger界面
description: 日志程序界面入门。
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Logger界面

要开始使用日志程序，您必须创建实例 `\Psr\Log\LoggerInterface`. 通过此界面，您可以调用以下函数将数据写入日志文件：

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [emergency()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [注意()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

实现该目标的一种方法在 [记录数据库活动](../logs/database-activity.md) 示例。

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

上例显示 `SomeModel` 接收 `\Psr\Log\LoggerInterface` 对象使用构造函数注入。 在方法中 `doSomething`，如果发生错误，则将其记录到方法 `critical` (`$this->logger->critical($e);`)。

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) 定义八个日志级别（调试、信息、通知、警告、错误、严重、警报和紧急）。
