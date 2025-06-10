---
source-git-commit: f9cc5ab0cb1b64455e12081ffbf719e0f2a791ad
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---
# 2025年6月安全修补程序亮点

此版本包括以下功能亮点：

* **API性能增强** — 解决在上一个安全修补程序之后引入的批量异步Web API端点中的性能降级。<!-- AC-14078 -->

* **CMS阻止访问修复** — 解决具有受限权限（例如仅限促销访问）的管理员用户无法查看[!UICONTROL CMS Blocks]列表页的问题。

  以前，这些用户在安装以前的安全修补程序后由于缺少配置参数而遇到错误。<!-- AC-14087 -->

* **Cookie限制兼容性** — 解决涉及框架中`MAX_NUM_COOKIES`常量的向后不兼容的更改。 此更新将恢复预期行为，并确保与Cookie限制交互的扩展或自定义设置的兼容性。<!-- AC-14475 -->

* **修复CVE-2024-34104** — 解决不正确的授权漏洞。<!-- AC-13917 -->

* **修复了CVE-2025-47110** — 解决了电子邮件模板漏洞。<!-- AC-14695 -->

* **修复VULN-31547** — 解决类别规范链接漏洞。<!-- AC-14713 -->

>[!BEGINSHADEBOX]

CVE-2025-47110 VULN-31547的修复程序也作为独立修补程序提供。 有关详细信息，请参阅[知识库文章](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50)。

>[!ENDSHADEBOX]
