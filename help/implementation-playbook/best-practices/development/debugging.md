---
title: 调试最佳实践
description: 学习解决常见Adobe Commerce开发问题的技术。
feature: Best Practices
role: Developer
exl-id: 78fbea7b-28e8-4713-990d-b4cae159250c
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 0%

---

# Adobe Commerce的调试最佳实践

本主题介绍如何系统和有效地调试Adobe Commerce框架。 目标是帮助您快速找到问题的根源并最大限度地缩短调查时间。

## 故障诊断：常见问题

本节介绍您在开发过程中可能遇到的最常见问题。

### 缓存

- 在进一步调查之前刷新缓存
- 考虑APC缓存、CDN、Varnish、生成的代码以及`var/view_preprocessed`和`pub/static/`目录
- 在刷新缓存或修改代码后停止并重新启动队列处理程序

以下代码示例提供了与管理缓存（不在生产环境中运行）相关的有用命令：

```bash
# restart php-fpm to flush APC
sudo service php-fpm restart
 
# restart varnish to force full flush
sudo service varnish restart
 
# clear generated files
rm -rf generated/*
 
# clear static file cache
rm -rf var/view_preprocessed/*
rm -rf pub/static/*
 
# flush redis cache
redis-cli -n <db_number> FLUSHDB
 
# flush redis cache and sessions
redis-cli FLUSHALL
 
# flush redis cache with telnet
telnet <ip_or_host> 6379
SELECT <db_number>
FLUSHDB
Ctrl + ]
quit
 
# flush redis cache and sessions with telnet
telnet <ip_or_host> 6379
FLUSHALL
Ctrl + ]
quit
 
# find consumers
pgrep -af queue:consumers:start
 
# kill all queue consumers (they will restart by cron job)
sudo pkill -f queue:consumers:start
 
# kill a specific queue consumer (it will restart by cron job)
sudo kill <process_id>
```

### 索引数据

如果问题可能与索引相关，则重新索引所有内容。 调试索引数据通常在非生产环境中进行。 在生产环境中，您可能需要在重新索引之前调查索引未对齐的原因。 故障状态的特征可以揭示问题的起源。

### Composer

由于分支更改或在以前的调试工作中编辑的核心文件，您的代码可能已过时。 要消除潜在问题，请运行以下命令：

```bash
rm -rf vendor/*
composer clear-cache
composer install
```

### 生成的内容

在调试JS、CSS、图像、翻译和其他文件中生成的内容之前，请重新构建前端文件。

```bash
rm -rf generated/* var/cache/* var/page_cache/* var/session/* var/view_preprocessed/* pub/static/*
bin/magento setup:static-content:deploy
bin/magento cache:flush
```

### 开发人员模式

确保您的本地安装处于`developer`模式。

### 新建模块

如果您已创建模块，请检查以下问题：

- 模块是否已启用？

  ```bash
  bin/magento module --enable Your_Module
  ```

  检查`app/etc/config.php`文件以查找新模块。

- 检查文件和目录结构嵌套。 例如，布局文件是在`view/layout/`目录中而不是`view/frontend/layout`目录中吗？ 模板是否位于`view/frontend/template`目录而非`view/frontend/templates`目录中？

## 故障诊断：半拆分

如果通常的怀疑者不能提供问题的解决方案，那么最快速的办法是半分割（或二分）问题。 使用此方法，您可以消除大块并划分剩余的部分，以找到根本原因，而不是以线性方式浏览代码。

请参阅以下图表：

![二叉图](../../../assets/playbooks/bisect.png)

![二叉图](../../../assets/playbooks/bisect2.png)

虽然存在几种平分方法，但Adobe建议遵循以下顺序：

- 按主题二分
- 按承诺二分
- 按文件二分

### 步骤1：按主题二分

如果问题可能与代码无关，请先消除大块。 要考虑的一些大块资产包括：

- **Adobe Commerce框架** — 问题是否与Adobe Commerce有关，或者是否与其他连接的系统有关？
- **服务器和客户端** — 清除浏览器缓存和存储。 问题是否已解决？ 这可能会排除与服务器相关的原因。 问题是否仍然存在？ 无需再浪费浏览器调试时间。
- **会话** — 问题是否对每个用户都出现？ 如果不能，问题可能仅限于与会话或浏览器相关的主题。
- **缓存** — 禁用所有缓存是否会更改任何内容？ 如果是这样，您可以专注于与缓存相关的主题。
- **数据库** — 运行相同代码的每个环境是否都出现问题？ 如果没有，请在配置中查找问题以及其他与数据库相关的主题。
- **代码** — 如果以上都不能解决问题，请查找代码问题。

### 步骤2：按承诺二分

如果问题是在现在到两个月之前开始的，请将代码回退到两个月之前。 验证问题是否仍然存在。 往前推一个月。 问题是否出现在那里？ 如果不能，请继续两周。 现在发生吗？ 一周后再回来。 还在那里吗？ 回到四天前。 在某个时刻，您只剩下一项承诺可能包含与问题相关的代码。 现在，您的根本原因可能仅限于在该提交中编辑的文件。

您可以使用承诺代替周和天。 例如，回滚100次提交，前进50次，前进25次，后退12次。

### 步骤3：按文件二分法

- 按文件类型（核心和非核心）划分Adobe Commerce。 首先，禁用所有客户和市场模块。 问题是否仍然存在？ 这极有可能是一个非核心问题。
- 再次启用`app/etc/config.php`文件中的一半模块（大约）。 了解依赖关系。 最好一次启用具有相同主题的模块群集。 问题是否仍然存在？
- 启用四分之一的剩余模块。 问题是否仍然存在？ 禁用一半您启用的内容。 此方法可帮助您将根本原因隔离到单个模块。

## 节省时间

除了故障诊断技术之外，本节还提供了一些常规规则，这些规则有助于在调试期间节省时间。

### 限制数据

考虑是需要完整目录还是所有存储视图来复制问题。 您可以调试数据库克隆的索引问题，在开始调试之前，您已删除了95%的目录。 这种方法在索引过程中节省了大量的时间。 创建客户端数据库的副本，减少存储数量和目录。 根据您正在调试的区域，这也可能适用于其他实体（例如客户）。

### 询问更多信息

有时，在所有代码和技术工作中忘记的一个简单步骤是：要求提供更多信息。 全屏捕获、视频、与发现问题的人进行视频会议聊天、复制步骤，以及有关问题事件是否发生了其他看似不重要的事情的问题。 问问别人预料会发生什么。 这真的是一个错误还是只是对代码工作方式的误解？

### 语文和口译

问题的描述是否清晰？ 是否确定无法以多种方式解释术语或描述。 如果是这样，请确保您谈论的是同一件事。

### Internet搜索

使用与问题相关的术语进行Internet搜索。 其他人可能已经遇到了同样的问题。 搜索[Adobe Commerce GitHub问题](https://github.com/magento/magento2/issues)。

### 休息一下

如果您查看问题的时间过长，则很难找到解决方案。 放下工作，做其他工作或散步。 当您暂时忘记这个问题时，可能会找到答案。

## 工具

n98 magerun CLI工具([https://github.com/netz98/n98-magerun2](https://github.com/netz98/n98-magerun2))提供了从命令行使用Adobe Commerce的有用功能。 尤其是以下命令：

```bash
n98-magerun2.phar dev:console
n98-magerun2.phar sys:cron:run
n98-magerun2.phar db:console
n98-magerun2.phar index:trigger:recreate
```


## 代码段

以下主题提供了可用于记录或识别Commerce项目中的问题的代码片段。

### 检查Commerce是否使用XML文件

在XML文件中添加明显的语法错误以查看是否使用该文件。 打开标记但不关闭该标记（例如）：

```xml
<?xml version="1.0"?>
<test
```

如果使用此文件，则会生成错误。 如果不适用，则您的模块可能无法使用或无法用于实例，或者XML文件可能位于错误的位置。

### 记录

>[!BEGINTABS]

>[!TAB Adobe Commerce]

```php
\Magento\Framework\App\ObjectManager::getInstance()
    ->get(\Psr\Log\LoggerInterface::class)->debug('message');
```

>[!TAB 独白]

```php
$log = new \Monolog\Logger('custom', [new \Monolog\Handler\StreamHandler(BP.'/var/log/test.log')]);
$log->info('Your Logging Message', ['context' => ['email' => 'john@example.com']]);
```

>[!TAB Zend]

```php
$writer = new \Zend\Log\Writer\Stream(BP . '/var/log/test.log');
$logger = new \Zend\Log\Logger();
$logger->addWriter($writer);
$logger->info('Your text message');
$logger->info(print_r($yourArray, true));
```

>[!ENDTABS]

### 低级日志记录

始终在任何PHP文件中工作的两个示例：

```php
file_put_contents('/var/www/html/var/log/example.log', "example line\n", FILE_APPEND);
file_put_contents('/var/www/html/var/log/example.log', print_r($yourArray, true) . "\n", FILE_APPEND);
```

对于栈栈跟踪：

```php
try {
    throw new \Exception('example');
} catch (\Exception $e) {
    file_put_contents('/var/www/html/var/log/example.log', $e->getTraceAsString() . "\n", FILE_APPEND);
}
```
