---
title: 例外处理最佳实践
description: 了解在开发Adobe Commerce项目时记录异常的推荐方法。
feature: Best Practices
role: Developer
exl-id: e7ad685b-3eaf-485b-8ab1-702f2e7ab89e
source-git-commit: 4bf8dd5c5320cc9a34cfaa552ec5e91d517d3617
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# 例外处理最佳实践

如果异常未写入到`exception.log`文件，并且异常模型作为上下文，则无法在New Relic或其他与PSR-3单色兼容的日志存储中正确识别和分析异常。 如果忽略异常，则仅记录部分异常（或将其记录到错误的文件）会导致生产中出现错误。

## 正确的异常处理

以下核对清单提供了用于演示正确的异常处理的示例。

### ![正确](../../../assets/yes.svg)写入异常日志

使用以下模式写入异常日志，而不考虑进一步的操作，除非有令人信服的理由不这样做。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

此方法按照[PSR-3上下文标准](https://www.php-fig.org/psr/psr-3/#13-context)，自动将`$e->getMessage`保存到日志消息，将`$e`对象保存到上下文。 此操作在`\Magento\Framework\Logger\Monolog::addRecord`内完成。

### ![正确](../../../assets/yes.svg)静音信号

不记录作为预期操作流程一部分的异常，将信号静音。 如果遇到异常，则无需执行任何后续操作，因此无需在异常发生时对其进行记录和分析。 添加注释，指明静音信号的原因以及它是有意为之。 与`phpcs:ignore`合并。

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![更正](../../../assets/yes.svg)降级异常

按照[PSR-3上下文标准](https://www.php-fig.org/psr/psr-3/#13-context)降级异常。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![正确](../../../assets/yes.svg)日志记录始终排在首位

作为最佳实践，日志记录始终优先于代码中，以防止在写入日志之前引发其他异常或致命错误的情况。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![更正](../../../assets/yes.svg)日志消息和整个异常跟踪

按照[PSR-3上下文标准](https://www.php-fig.org/psr/psr-3/#13-context)记录消息和整个异常跟踪。

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## 异常处理不正确

以下示例演示了错误的异常处理。

### ![逻辑不正确](../../../assets/no.svg)日志记录前

记录之前的逻辑可能会导致另一个异常或致命错误，这会阻止记录该异常，应替换为[正确的示例](#logging-always-comes-first)。

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![不正确](../../../assets/no.svg)空`catch`

空`catch`块可能是无意静音的标志，应替换为[正确的示例](#mute-signals)。

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![不正确](../../../assets/no.svg)双重本地化

如果捕获的本地化异常尚未转换，请在首次引发该异常的位置解决该问题。

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![不正确](../../../assets/no.svg)日志消息并跟踪到不同的日志文件

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

通过替换[写入异常日志](#write-to-the-exception-log)或[降级异常](#downgrade-exceptions)中显示的正确示例后面的代码来解决此问题。

### ![不正确](../../../assets/no.svg)没有上下文的降级异常

该异常已降级为错误，不允许传递对象，只允许传递字符串，因此`getMessage()`。 这会导致跟踪丢失，应以[写入异常日志](#write-to-the-exception-log)或[降级异常](#downgrade-exceptions)中显示的正确示例替换。

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![不正确](../../../assets/no.svg)仅将消息记录到异常日志

只传递`$e->getMessage()`，而不是传递对象`$e`。 这会导致跟踪丢失，应被显示为[写入异常日志](#write-to-the-exception-log)或[降级异常](#downgrade-exceptions)的正确示例替换。

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![不正确](../../../assets/no.svg)缺少`// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

省略`phpcs:ignore`行会在PHPCS中触发警告，并且不应传递您的CI。 应使用[静音信号](#mute-signals)中所示的正确示例替换此项。

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
