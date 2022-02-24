---
title: '"[!DNL Upgrade Compatibility Tool] 开发人员信息”'
description: 自定义 [!DNL Upgrade Compatibility Tool] 使用API索引集成。
source-git-commit: 97295df89fda393c8cf8675f8f4be92ac6f38a6a
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] 开发人员信息

本主题包含的信息适用于与Adobe Commerce代码密切合作并希望了解 [!DNL Upgrade Compatibility Tool]. 您可以使用此知识自定义工具的组件。

## Adobe Commerce API索引集成

Adobe Commerce API索引集成是一个内部集成解决方案，它包含一组工具，用于探索由Adobe、Adobe Commerce合作伙伴和基于静态代码分析的第三方供应商开发的Adobe Commerce扩展。

与Adobe Commerce API索引的集成可通过以下方式完成：

`sut\Domain\MRay\MRayInterface`

它通过 `config/services.yaml` 文件。 其值决定方法的响应位置 `api()` 和 `modules()` 来自。

编辑此文件以根据您的安装自定义响应。 替换分配给的值 `sut\Domain\MRay\MRayInterface`:

### 自定义值的示例

`sut\Domain\MRay\MRayInterface : "@sut_mray_mock"`

在上一个示例中， [!DNL Upgrade Compatibility Tool] 使用 `@sut_mray_mock` 作为 `MRayInterface` 实施。 来自 `api()` 和 `modules()` 方法来自以下文件：

- `dev/mray_mock_files/api.json`
- `dev/mray_mock_files/modules.json`

>[!NOTE]
>
>当您更改 `services.yaml` 文件，删除 `var/cache/` 文件夹来正确应用更改。

## 单元测试

要运行单元测试，请执行以下命令之一：

- `vendor/bin/phpunit tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist --testsuite=unit-tests`

## 集成测试

要运行集成测试，请执行以下命令之一：

- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist tests/integration`
- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist --testsuite=integration-tests`

## 验收测试

1. 在执行接受测试之前，必须在 `phpunit` 配置文件。
1. 复制默认 `tests/acceptance/phpunit.xml` 文件（不带.dist后缀）。
1. 更改 `TESTS_BASE_URL` 值指向要测试的Adobe Commerce URL。
1. 要运行验收测试，请执行以下命令之一：

   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml tests/acceptance`
   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml --testsuite=acceptance-tests`

## GraphQL单元测试和ESLint代码分析

### 要求

>[!NOTE]
>
>您的系统上必须具有Node.js，请参阅 [Node.js文档](https://nodejs.dev/learn/how-to-install-nodejs).

以下说明适用于MacOS系统：

1. 打开终端，然后导航到项目的根目录。
1. 安装项目依赖项：

   ```bash
   npm install
   ```

### GraphQL单元测试

的 [Jest](https://jestjs.io/docs/getting-started) 框架用于创建以下JS单元测试：

测试在内 `dev/tests/Js`.

测试的字符串架构位于内部 `dev/tests/Acceptance/_files/graphql_schemas`.

运行单位测试或 `jest` 如下所示：

```bash
./node_modules/.bin/jest --verbose --rootDir=dev/tests/Js/
```

### ESLint代码分析

[ESLint](https://eslint.org/docs/user-guide/getting-started) 是一种静态代码分析工具，用于识别在JavaScript代码中发现的问题模式，旨在使代码更加一致并避免错误。

运行 `eslint` 代码分析如下：

```bash
./node_modules/.bin/eslint -c dev/tests/Static/.eslintrc --rulesdir vendor/magento/magento-coding-standard/eslint/rules path/to/analyse
```

## 复杂性分数

的 **复杂性分数** 是一个图，用于指示从当前版本升级到新版本的难度。 数量越少，升级越容易。

>[!NOTE]
>
>复杂性得分介于0到∞之间。

此分数基于从分析中提取的结果：

- 已识别的问题数
- 已识别问题的严重性

的 [!DNL Upgrade Compatibility Tool] 根据下面的复杂度得分公式计算此得分。

### 复杂度分数公式

`Complexity Score = (Critical issues * 3) + (Errors *2) + Warnings`

>[!WARNING]
>
>这些是绝对值。
