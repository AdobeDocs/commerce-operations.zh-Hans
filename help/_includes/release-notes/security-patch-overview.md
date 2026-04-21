---
source-git-commit: 52c330f62d722a4cae7f7f360ca61eca0f04b961
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---
# 关于Adobe Commerce安全修补程序版本

**安全错误修复**：解决已识别的安全问题并在受影响的产品区域提供预期结果的软件代码更改。 这些修复通常向后兼容。

**安全增强**：软件改进或配置更改以主动提高应用程序中的安全性。 这些安全增强功能可帮助解决会影响Adobe Commerce应用程序的安全状态但可能向后不兼容的安全风险。

使用安全修补程序版本，您可以使站点更加安全，而无需应用完整修补程序版本中包含的其他质量修复和增强功能。 安全修补程序版本后附有“ — pN”，其中N是以1开头的增量修补程序版本（例如2.3.5-p1）。 安全修补程序版本还可以包含解决影响Adobe Commerce应用程序的严重问题所需的修补程序。

安全修补程序版本还可以包含与合规性相关的更改，这些更改是确保Adobe Commerce应用程序满足合规性要求所必需的。 这些更改可能会引入向后不兼容的更改，为确保所有受支持的版本行保持合规性需要这些更改。

每个安全补丁发行版本都基于以前的完整补丁发行版本。 它包含先前修补程序版本的质量和安全修复，以及在先前完整修补程序版本和安全修补程序版本之间创建的安全修复。

有关下载和应用安全修补程序的说明，请参阅[Adobe Commerce知识库](https://experienceleague.adobe.com/zh-hans/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches)中的&#x200B;_如何获取和应用安全修补程序_。

>[!NOTE]
>
>扩展支持安全修补程序仅适用于Adobe Commerce客户，不适用于Magento Open Source代码库。 请参阅[扩展支持](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/release/planning/lifecycle-policy#extended-support)。

## 隔离的安全修补程序文件

独立的安全修补程序文件是非累积性的独立修补程序文件，仅包含针对一个或多个安全漏洞的修补程序，不提供任何额外的功能更新或非安全更改。 这些修补程序单独发布以实现更快的修复，并整合到下一个完整的安全修补程序中。 有关漏洞的详细信息在相关安全公告中提供，该公告链接到知识库(KB)文章，其中包含应用补丁程序的说明和其他信息。

要应用独立的安全修补程序文件，客户必须在其受支持的发行版中安装最新的仅安全修补程序发行版（最新的 — p版本），因为独立的安全修补程序文件将专门针对该版本进行测试。

请参阅[安全中心](https://helpx.adobe.com/cn/security/products/magento.html)以查找Adobe Commerce的最新安全更新。

