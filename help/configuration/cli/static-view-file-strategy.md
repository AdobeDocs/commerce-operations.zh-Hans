---
title: 静态视图文件的部署策略
description: 了解Adobe Commerce应用程序中静态视图文件的部署策略。 探索不同用例的最佳部署方法。
feature: Configuration, Deploy, Extensions
exl-id: 12ebbd36-f813-494f-9515-54ce697ca2e4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# 静态视图文件的部署策略

部署静态视图文件时，可以选择三种可用策略之一。 其中每个选项都可为不同用例提供最佳部署结果：

- [标准](#standard-strategy)：常规部署过程。
- [快速](#quick-strategy) （_默认_）：在部署多个区域设置的文件时，最大程度地缩短部署所需的时间。
- [紧凑](#compact-strategy)：最小化已发布视图文件占用的空间。

以下各节描述了每个策略的实施详细信息和功能。

## 标准策略

使用标准策略时，将部署所有包的所有静态视图文件，即[`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php)处理的文件。

有关详细信息，请参阅[部署静态视图文件](../cli/static-view-file-deployment.md)。

## 快速策略

快速策略执行以下操作：

1. 对于每个主题，选择一个任意区域设置，并部署此区域设置的所有文件，例如在标准策略中。
1. 对于主题的所有其他区域设置：

   1. 定义并部署覆盖已部署区域设置的文件。
   1. 对于所有区域设置，所有其他文件都被视为相似，并从已部署的区域设置中复制。

>[!INFO]
>
>按&#x200B;_similar_，我们是指与区域设置、主题或区域无关的文件。 这些文件可能包含CSS、图像和字体。

虽然复制了大量文件，但此方法可最大限度地缩短多个区域设置所需的部署时间。

## 紧凑策略

压缩策略通过将相似文件存储在`base`子目录中来避免文件重复。

为了得到最优化的结果，分配了三种可能的相似性范围：区域、主题和区域设置。 为这些范围的所有组合创建`base`子目录。

文件将按照以下模式部署到这些子目录中。

| 图案 | 描述 |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | 特定区域、主题和区域设置的特定文件 |
| `<area>/<theme>/default` | 与特定区域的特定主题的所有区域设置类似的文件。 |
| `<area>/Magento/base/<locale>` | 特定于特定区域和区域设置的文件，但所有主题均类似。 |
| `<area>/Magento/base/default` | 特定于特定区域的文件，但对于所有主题和区域设置相似。 |
| `base/Magento/base/<locale>` | 所有区域和主题的文件都类似，但特定于特定区域设置。 |
| `base/Magento/base/default` | 所有区域、主题和区域设置都类似。 |

### 映射已部署的文件

紧凑策略中使用的部署方法意味着文件从基本主题和区域设置继承。 这些继承关系存储在区域、主题和区域设置的每个组合的映射文件中。 PHP和JS有单独的映射文件：

- `map.php`
- `requirejs-map.js`

`map.php`[`Magento\Framework\View\Asset\Repository`使用](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php)文件生成正确的URL。

`requirejs-map.js`由`baseUrlResolver`插件用于RequireJS。

`map.php`示例：

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

`requirejs-map.js`示例：

```js
require.config({
    "config": {
       "baseUrlInterceptor": {
            "jquery.js": "../../../../base/Magento/base/en_US/"
        }
    }
});
```

## 扩展开发人员提示

若要生成静态视图文件的URL，请使用[`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244)。

请勿使用URL拼接来避免在页面渲染期间未找到或未显示静态文件的问题。
