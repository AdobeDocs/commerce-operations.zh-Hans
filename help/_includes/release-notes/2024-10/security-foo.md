---
source-git-commit: cb4f388c90902c2fe1df4a5d84841280fa740104
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---
# 2024年10月安全修补程序要点

此版本包括以下功能亮点：

* **TinyMCE升级** — 管理员中的[WYSIWYG编辑器](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/wysiwyg/editor)现在使用最新版本的TinyMCE依赖项(7.3&#x200B;)。

   * TinyMCE 7.3提供了增强的用户体验、更好的协作和更高的效率。 TinyMCE 5已在2.4.8发行版中移除&#x200B;。

   * 由于TinyMCE 5.10中报告存在安全漏洞([CVE-2024-38357](https://nvd.nist.gov/vuln/detail/CVE-2024-38357))，因此当前支持的所有版本行均已升级依赖项，并包含在所有2024年10月的安全修补程序中：

      * 2.4.7 - p3
      * 2.4.6-p8
      * 2.4.5-p10
      * 2.4.4-p11

* **Require.js升级**—Adobe Commerce现在使用最新版本的Require.js (2.3.7)。

   * 由于Require.js 2.3.6中报告存在安全漏洞([CVE-2024-38999](https://nvd.nist.gov/vuln/detail/CVE-2024-38999))，因此当前支持的所有版本行的依赖项均已升级，并包含在所有2024年10月的安全修补程序中：

      * 2.4.7 - p3
      * 2.4.6-p8
      * 2.4.5-p10
      * 2.4.4-p11

>[!NOTE]
>
>这些更新向后兼容，并且不会影响自定义项和扩展&#x200B;。
