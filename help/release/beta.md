---
title: 测试版
description: 了解Adobe Commerce测试版发布以及如何参与。
source-git-commit: 1ce0ff87291c5c3f0fd130aa351bc975f42501e3
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# Adobe Commerce测试版

从2023年6月开始，Adobe将发布补丁版本的公共Beta（“测试版”）。 在正式发布(GA)之前，所有Adobe Commerce客户和合作伙伴都可以使用测试版，其中包括安全性、合规性、性能和高优先级的质量修复。

>[!IMPORTANT]
>
>Beta版可能包含缺陷，并“按原样”提供，不提供任何形式的担保。 Adobe没有义务维护、更正、更新、更改、修改或以其他方式支持(通过Adobe支持服务或其他方式)测试版。 建议客户谨慎使用，并且不要以任何方式依赖测试版和/或任何随附文档或材料的正确功能或性能。 因此，任何使用测试版都是由客户自行承担风险。

## 版本内容

每个Adobe Commerce测试版都包括在计划发行日期之前交付给Adobe Commerce核心代码的所有更改，包括但不限于以下功能领域：

- 最新的安全修复
- 性能改进
- GraphQL改进
- 一般质量错误修复
- 社区投稿
- 支持与的兼容性所需的更改 [Adobe Commerce服务](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

## 命名约定和调度

Adobe将每年发布两次Beta版修补程序。 第一个测试版修补程序通常在新的核心应用程序修补程序版本正式发布三个月后发布。

测试版发行包具有 `-betaX` 后缀。 例如，Adobe Commerce 2.4.7测试版发行包使用以下命名约定：

- `2.4.7-beta1`
- `2.4.7-beta2`

请参阅 [发布计划](schedule.md) 以获取即将发布的公共测试版发布日期的列表。

## 参与的优势

您越早看到我们正在开发的代码，您就越早地为即将到来的升级准备技术和商家。

虽然情况可能发生变化，但通过参与Beta版，您能够开始了解代码库更改的具体发生位置，并开始在GA发行日期之前进行准备。

## Beta版访问权限

Adobe Commerce测试版的发布方式与任何其他Adobe Commerce补丁版本相同： `https://repo.magento.com`. 源代码位于 [GitHub](https://github.com/magento/magento2).

参见 [编辑器安装快速入门](../installation/composer.md) 了解更多详细信息。

## 问题报告

Adobe不提供测试版的标准Adobe支持服务。

要提交与测试版相关的反馈，请遵循我们的 [常规问题报告流程](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) 日期 [GitHub](https://github.com/magento/magento2).

我们的内部团队将监控针对最新测试版报告的所有严重问题，并排定在GA发布日期之前解决这些问题的优先级。
