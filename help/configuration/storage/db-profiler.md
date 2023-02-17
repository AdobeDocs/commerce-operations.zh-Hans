---
title: 配置数据库探查器
description: 请参阅如何为数据库探查器配置输出的示例。
badge: label="Contributed by Atish Goswami" type="Informative" url="https://github.com/atishgoswami" tooltip="Atish Goswami"
source-git-commit: bcb995ea417423b0cbc59c035ba5fdedbce3310e
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# 配置数据库探查器

商务数据库探查器显示页面上实现的所有查询，包括每个查询的时间和应用的参数。

## 步骤1:修改部署配置

修改 `<magento_root>/app/etc/env.php` 将以下引用添加到 [数据库探查器类](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php):

```php?start_inline=1
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
```

示例如下：

```php?start_inline=1
 'db' =>
  array (
    'table_prefix' => '',
    'connection' =>
    array (
      'default' =>
      array (
        'host' => 'localhost',
        'dbname' => 'magento',
        'username' => 'magento',
        'password' => 'magento',
        'model' => 'mysql4',
        'engine' => 'innodb',
        'initStatements' => 'SET NAMES utf8;',
        'active' => '1',
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
      ),
    ),
  ),
```

## 步骤2:配置输出

在商务应用程序引导文件中配置输出；这可能 `<magento_root>/pub/index.php` 或者，它可以位于web服务器虚拟主机配置中。

以下示例在三列表中显示结果：

- 总时间（显示在页面上运行所有查询的总时间）
- SQL(显示所有SQL查询；行标题显示查询计数)
- 查询参数（显示每个SQL查询的参数）

要配置输出，请在 `$bootstrap->run($app);` 引导文件中的行：

```php?start_inline=1
/** @var \Magento\Framework\App\ResourceConnection $res */
$res = \Magento\Framework\App\ObjectManager::getInstance()->get('Magento\Framework\App\ResourceConnection');
/** @var Magento\Framework\DB\Profiler $profiler */
$profiler = $res->getConnection('read')->getProfiler();
echo "<table cellpadding='0' cellspacing='0' border='1'>";
echo "<tr>";
echo "<th>Time <br/>[Total Time: ".$profiler->getTotalElapsedSecs()." secs]</th>";
echo "<th>SQL [Total: ".$profiler->getTotalNumQueries()." queries]</th>";
echo "<th>Query Params</th>";
echo "</tr>";
foreach ($profiler->getQueryProfiles() as $query) {
    /** @var Zend_Db_Profiler_Query $query*/
    echo '<tr>';
    echo '<td>', number_format(1000 * $query->getElapsedSecs(), 2), 'ms', '</td>';
    echo '<td>', $query->getQuery(), '</td>';
    echo '<td>', json_encode($query->getQueryParams()), '</td>';
    echo '</tr>';
}
echo "</table>";
```

## 步骤3:查看结果

转到店面或管理员中的任意页面以查看结果。 示例如下：

![数据库探查器结果示例](../../assets/configuration/db-profiler-results.png)
