---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---
# 10月安全修补程序中包含的修补程序（2.4.4除外）

此版本包含用于解决Braintree支付网关问题的修补程序。

在使用Braintree作为支付网关时，该系统现在包括满足3DS VISA要求所需的字段。 这可确保所有交易都符合VISA设置的最新安全标准。 以前，这些附加字段未包含在发送的支付信息中，这可能导致不遵守新的VISA要求。

<!--
BUNDLE-3360
-->