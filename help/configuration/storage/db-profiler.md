---
title: 設定資料庫分析工具
description: 請參閱如何設定資料庫效能分析工具輸出的範例。
feature: Configuration, Storage
badge: label="Contributed by Atish Goswami" type="Informational" url="https://github.com/atishgoswami" tooltip="Atish Goswami"
exl-id: 87780db5-6e50-4ebb-9591-0cf22ab39af5
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# 設定資料庫分析工具

Commerce資料庫分析工具會顯示頁面上實作的所有查詢，包括每個查詢的時間以及套用的引數。

## 步驟1：修改部署組態

修改 `<magento_root>/app/etc/env.php` 將下列參照新增至 [資料庫效能分析工具類別](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php)：

```php?start_inline=1
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
```

範例如下：

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

## 步驟2：設定輸出

在Commerce應用程式啟動程式檔案中設定輸出；這可能是 `<magento_root>/pub/index.php` 或者，它可以位於Web伺服器虛擬主機設定中。

下列範例會在三欄表格中顯示結果：

- 總時間（顯示頁面上執行所有查詢的總時間）
- SQL （顯示所有SQL查詢；列標題顯示查詢計數）
- 查詢引數（顯示每個SQL查詢的引數）

若要設定輸出，請在 `$bootstrap->run($app);` 在您的bootstrap檔案中的行：

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

## 步驟3：檢視結果

前往店面或管理員中的任何頁面檢視結果。 範例如下：

![範例資料庫效能分析工具結果](../../assets/configuration/db-profiler-results.png)
