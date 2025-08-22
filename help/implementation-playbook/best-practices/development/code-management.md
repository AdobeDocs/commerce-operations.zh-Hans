---
title: 代码管理最佳实践
description: 了解Adobe Commerce项目开发阶段的代码管理最佳实践。
feature: Best Practices
role: Developer
exl-id: 0bff4c7a-1082-4b3e-b19c-bc8ad529b131
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---

# Adobe Commerce的代码管理最佳实践

本主题旨在帮助您确定是使用Git还是使用Composer分发自定义代码，并考虑版本管理、代码复杂性和依赖关系管理。

>[!NOTE]
>
>这些最佳实践最适合迁移和实施；而对于单模块开发，则不太适合。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md)，共：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 定义

{{$include /help/_includes/gra-definitions.md}}

## 何时使用Git或编辑器

<table>
<thead>
  <tr>
    <th></th>
    <th>主要通过Git管理的代码</th>
    <th>主要通过编辑器管理的代码</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>何时用于单实例设置</td>
    <td>
      <ul>
        <li><strong>用于管理单实例设置的代码的标准方法</strong></li>
        <li>代码库将来不会成为多品牌GRA的一部分时</li>
        <li>当所有品牌作为网站在单个实例上运行时</li>
      </ul>
    </td>
    <td>
      <ul>
        <li>代码库将来可以或将成为多实例设置的一部分的时间</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>何时用于多实例设置</td>
    <td>
      <ul>
        <li>当几乎所有模块都相互链接时（不推荐）</li>
        <li>当代码由不熟悉编辑器的团队维护时</li>
      </ul>
    </td>
    <td>
      <ul>
        <li><strong>用于管理多实例设置的代码的标准方法</strong></li>
        <li>当Adobe维护代码库或维护团队熟悉编辑器时</li>
      </ul>
    </td>
  </tr>
</tbody>
</table>

## 特征矩阵

| 功能 | Git | Composer |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| 主代码存储库 | 所有代码都驻留在单个或几个Git存储库中 | 所有代码都驻留在Composer存储库中的包中<br>每个Composer包都由Git存储库表示 |
| 代码位置 | 开发发生在`app/`目录中 | 开发发生在`vendor/`目录中 |
| 核心升级管理 | 使用Composer安装和升级Adobe Commerce核心，结果在Git中提交 | 使用编辑器安装和升级Adobe Commerce核心；结果在Git中提交 |
| 第三方模块管理 | 第三方模块是通过Marketplace或packagist.org安装在`vendor/`中的。 否则，它们安装在`app/`中 | 所有第三方模块都安装在`vendor/`目录中 |
| 版本 | 正在释放的特征是`git merge`和`git pull`或`git checkout`命令 | 正在释放的特征是`composer update`和`git pull`或`git checkout`命令 |
| Git存储库的数量 | 少数 | 许多 |
| 开发复杂性 | 简单 | 复杂 |
| 拉取请求复杂性 | 简单 | 复杂 |
| 代码审查复杂性 | 简单 | 简单 |
| 开发/QA/UAT环境更新复杂性 | 简单 | 复杂 |
| GRA支持 | ![是图标](../../../assets/yes.svg) | ![是图标](../../../assets/yes.svg) |
| 模块可以自动安装外部库 | ![无图标](../../../assets/no.svg) | ![是图标](../../../assets/yes.svg) |
| GRA合成中的灵活性 | ![无图标](../../../assets/no.svg) | ![是图标](../../../assets/yes.svg) |
| 模块依赖关系管理 | ![是图标](../../../assets/yes.svg)仅通过`module.xml`，功能有限 | ![是图标](../../../assets/yes.svg)通过`composer.json`进行完全依赖关系管理 |
| 模块版本控制 | ![是](../../../assets/yes.svg)您可以定义版本，但无法安装特定版本 | ![是](../../../assets/yes.svg)图标完整版本支持 |
| 需要付费服务 | Git存储库 | Git存储库、私人打包员(每年600±元) |
| 可能与Jira集成Bitbucket | ![是图标](../../../assets/yes.svg) | ![是图标](../../../assets/yes.svg) |
| 对可立即安装的代码的更改 | ![是图标](../../../assets/yes.svg) | ![是图标](../../../assets/yes.svg) |

## 要避免的解决方案

1. 针对您的模块&#x200B;**组合编辑器和`app/code`**

   从而导致在项目中同时使用这两种代码管理样式的所有缺点。 它增加了不必要的复杂性、不稳定和缺乏灵活性。

   例如：
   - 向开发团队解释Git和编辑器工作流（而不是其中的一个）。
   - 在`app/code`中安装不兼容的模块，因为没有任何内容可阻止发生这种情况。
   - 将模块从`app/code`移动到编辑器（或反之）比较麻烦，尤其是对于正在进行的开发。

1. **Satis包管理器**

   私人包客每年±600欧元。 这一成本是整个GRA的总和，而不是每个品牌。 不要尝试使用免费解决方案Satis来避免这些成本。 每当您将提交推送到Git时，Satis都不会自动更新您的包。 此外，Satis没有内置授权。 必须维护Web服务器才能运行Satis。 最终，您将花费大量的Private Packagist订阅费用来维护Satis。

1. **从Git开始，然后移至编辑器**

   在项目开始时选择代码管理方法。 在持续开发的情况下从Git切换到编辑器或反之，过程非常繁琐，可能会导致代码丢失和或修订历史记录丢失。

<!-- Last updated from includes: 2023-08-23 15:56:59 -->
