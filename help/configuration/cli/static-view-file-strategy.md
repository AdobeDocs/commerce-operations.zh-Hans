---
title: 静态视图文件的部署策略
description: 请阅读有关商务应用程序的部署策略。
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---


# 静态视图文件的部署策略

部署静态视图文件时，您可以选择三种可用策略之一。 其中每个组件可为不同用例提供最佳部署结果：

- [标准](#standard-strategy):常规部署过程。
- [快速](#quick-strategy) (_默认_):在部署多个区域设置的文件时，最大限度地缩短部署所需的时间。
- [紧凑](#compact-strategy):最大限度地减少已发布视图文件占用的空间。

以下各节介绍了每个策略的实施详细信息和功能。

## 标准策略

使用标准策略时，将部署所有包的所有静态视图文件，即，由 [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php).

有关更多信息，请参阅 [部署静态视图文件](../cli/static-view-file-deployment.md).

## 快速策略

快速策略会执行以下操作：

1. 对于每个主题，都会选择一个任意区域设置，并部署此区域设置的所有文件，如在标准策略中。
1. 对于主题的所有其他区域设置：

   1. 定义并部署覆盖已部署区域设置的文件。
   1. 所有其他文件在所有区域设置中都被视为相似文件，并从已部署的区域设置复制。

>[!INFO]
>
>按 _相似_，是指与区域设置、主题或区域无关的文件。 这些文件可能包含CSS、图像和字体。

虽然大量文件都是重复的，但这种方法可以最大限度地缩短多个区域设置所需的部署时间。

## 紧凑策略

该紧凑策略通过在 `base` 子目录。

对于最优化的结果，会分配三个可能的相似范围：区域、主题和区域设置。 的 `base` 将为这些作用域的所有组合创建子目录。

这些文件将按照以下模式部署到这些子目录。

| 图案 | 描述 |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | 特定于特定区域、主题和区域设置的文件 |
| `<area>/<theme>/default` | 特定区域特定主题的所有区域设置都类似的文件。 |
| `<area>/Magento/base/<locale>` | 特定于特定区域和区域设置的文件，但所有主题都类似。 |
| `<area>/Magento/base/default` | 特定于特定区域的文件，但所有主题和区域设置都类似。 |
| `base/Magento/base/<locale>` | 所有区域和主题的文件都相似，但特定于特定区域设置。 |
| `base/Magento/base/default` | 所有区域、主题和区域设置都类似。 |

### 映射已部署的文件

紧凑策略中使用的部署方法意味着文件继承自基本主题和区域设置。 这些继承关系存储在区域、主题和区域设置的每个组合的映射文件中。 PHP和JS有单独的映射文件：

- `map.php`
- `requirejs-map.js`

的 `map.php` 文件使用者 [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) 以生成正确的URL。

的 `requirejs-map.js` 的 `baseUrlResolver` 插件。

示例 `map.php`:

```php?start_inline=1
return [
    'Magento_Checkout::cvv.png' => [
        'area' => 'frontend',
        'theme' => 'Magento/luma',
        'locale' => 'en_US',
    ],
    '...' => [
        'area' => '...',
        'theme' => '...',
        'locale' => '...'
    ]
];
```

示例 `requirejs-map.js`:

```js
require.config({
    "config": {
       "baseUrlInterceptor": {
            "jquery.js": "../../../../base/Magento/base/en_US/"
        }
    }
});
```

## 面向扩展开发人员的提示

要生成静态视图文件的URL，请使用 [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244).

请勿使用URL连接来避免在页面渲染期间找不到或未显示静态文件的问题。
