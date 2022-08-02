---
title: 记录器界面
description: 开始使用日志记录器界面。
source-git-commit: f489c3e68c91c6f2e16bff233cf59472ed684b5c
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# 记录器界面

要开始使用日志记录器，必须创建实例 `\Psr\Log\LoggerInterface`. 使用此界面，您可以调用以下函数将数据写入日志文件：

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [紧急()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notice()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

要实现此目的，请参阅 [日志数据库活动](../logs/database-activity.md) 示例。

另一种方式是：

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

上例显示 `SomeModel` 接收 `\Psr\Log\LoggerInterface` 对象。 在方法中 `doSomething`，如果发生某些错误，则会将其记录到方法 `critical` (`$this->logger->critical($e);`)。

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) 定义八个日志级别（调试、信息、通知、警告、错误、严重、警报和紧急）。
