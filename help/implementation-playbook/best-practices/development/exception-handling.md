---
title: 例外处理最佳实践
description: 了解在开发Adobe Commerce项目时记录异常的推荐方法。
feature: Best Practices
role: Developer
exl-id: e7ad685b-3eaf-485b-8ab1-702f2e7ab89e
source-git-commit: 4bf8dd5c5320cc9a34cfaa552ec5e91d517d3617
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# 例外处理最佳实践

如果异常未写入 `exception.log` 文件将异常模型作为上下文，在New Relic或其他与PSR-3单色兼容的日志存储中，无法正确识别和分析异常模型。 如果忽略异常，则仅记录部分异常（或将其记录到错误的文件）会导致生产中出现错误。

## 正确的异常处理

以下核对清单提供了用于演示正确的异常处理的示例。

### ![正确](../../../assets/yes.svg) 写入异常日志

使用以下模式写入异常日志，而不考虑进一步的操作，除非有令人信服的理由不这样做。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

此方法会自动保存 `$e->getMessage` 日志消息和 `$e` 对象到上下文，请遵循 [PSR-3上下文标准](https://www.php-fig.org/psr/psr-3/#13-context). 这是在中完成的 `\Magento\Framework\Logger\Monolog::addRecord`.

### ![正确](../../../assets/yes.svg) 将信号静音

不记录作为预期操作流程一部分的异常，将信号静音。 如果遇到异常，则无需执行任何后续操作，因此无需在异常发生时对其进行记录和分析。 添加注释，指明静音信号的原因以及它是有意为之。 与 `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![正确](../../../assets/yes.svg) 降级异常

按以下方式降级例外 [PSR-3上下文标准](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![正确](../../../assets/yes.svg) 日志记录始终排在首位

作为最佳实践，日志记录始终优先于代码中，以防止在写入日志之前引发其他异常或致命错误的情况。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![正确](../../../assets/yes.svg) 记录消息和整个异常跟踪

通过执行以下操作来记录消息和整个异常跟踪 [PSR-3上下文标准](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## 异常处理不正确

以下示例演示了错误的异常处理。

### ![不正确](../../../assets/no.svg) 日志记录前的逻辑

记录之前的逻辑可能会导致其他异常或致命错误，这会导致无法记录异常，应替换为 [正确示例](#logging-always-comes-first).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![不正确](../../../assets/no.svg) 空 `catch`

空 `catch` 块可能是无意静音的标志，应替换为 [正确示例](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![不正确](../../../assets/no.svg) 双重本地化

如果捕获的本地化异常尚未转换，请在首次引发该异常的位置解决该问题。

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![不正确](../../../assets/no.svg) 日志消息并跟踪到不同的日志文件

以下代码将异常的栈栈跟踪错误地作为字符串记录到日志文件中。

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
    $this->logger->debug($e->getTraceAsString());
}
```

这种方法在消息中引入了与PSR-3不兼容的换行符。 异常（包括栈栈跟踪）必须是消息上下文的一部分，以确保该异常与消息一起正确地保存在New Relic或其他与PSR-3单色兼容的日志存储中。

通过按照中显示的正确示例替换代码来解决此问题 [写入异常日志](#write-to-the-exception-log) 或 [降级异常](#downgrade-exceptions).

### ![不正确](../../../assets/no.svg) 无上下文的降级异常

异常将降级为错误，该错误不允许传递对象，而只允许传递字符串，因此 `getMessage()`. 这会导致跟踪丢失，应使用中显示的正确示例替换 [写入异常日志](#write-to-the-exception-log) 或 [降级异常](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![不正确](../../../assets/no.svg) 仅将消息记录到异常日志

而不是传递对象 `$e`，仅限 `$e->getMessage()` 通过。 这会导致跟踪丢失，应使用所示的正确示例替换 [写入异常日志](#write-to-the-exception-log) 或 [降级异常](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![不正确](../../../assets/no.svg) 缺失 `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

省略 `phpcs:ignore` line会在PHPCS中触发警告，因此不应传递您的CI。 此内容应替换为中显示的正确示例 [将信号静音](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
