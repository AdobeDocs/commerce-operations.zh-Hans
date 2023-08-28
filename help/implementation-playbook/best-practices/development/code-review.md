---
title: 代码审查最佳实践
description: 了解Adobe Commerce项目开发阶段的代码审查最佳实践。
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 0%

---


# Adobe Commerce的代码审查最佳实践

代码审查的主要目标是验证所实施的功能是否从性能、架构和安全角度以最佳方式满足了要求。

此外，代码审查旨在确保代码符合Adobe Commerce开发最佳实践、易于理解和维护，并遵循编码标准。 大多数编码标准应该由适当的工具自动检查。

## 推荐的代码审查流程

从较高层面来看，代码审查过程应包含以下步骤：

1. 在本地开发环境中签出功能分支。
1. 如果从提交代码以供审阅起已有一段时间，则合并来自目标分支（通常是QA分支）的最新更改，并将更新推送到远程功能分支（如果有）。
1. 进行高级审查，以验证代码是否实现了所有要求。 如果存在重大差异，请联系开发人员寻求说明。
1. 运行代码是可选的，但如果您怀疑代码是否按预期运行，或者怀疑它有利于提高流程的效率，则测试实施的功能是否按预期方式用于主要使用方案。 如果存在重大问题，请停止审阅过程，然后使用相应的注释重新打开票证。
1. 仔细检查以验证代码是否实现了所有要求。 如果有任何问题，请向拉取请求添加相应的注释并重新打开票证。
1. 如果一切看起来正常，请合并拉取请求(或者将拉取请求传递到下一个代码审核级别（如果已建立）。

此外，在实施代码审查流程时，请考虑以下几点：

- 代码审查是团队内进行沟通和知识传授的主要工具。 即使拉取请求不包含重大问题并实施所需的业务逻辑，您仍可以将其用作在合并后提出更多改进建议的机会。

- 平均而言，代码审查耗费的开发工作不应超过10%到20%。 这假定开发团队由能够很好地协同工作的高级工程师组成。 如果代码审阅需要较长时间，可能会影响项目预算和时间线。

- 通过确定根本原因来解决代码审查所需的工作量过大的问题。 通常，这是因为需求未很好地转换为开发票证（由于沟通问题、用户故事不佳）或它是一个指导问题。 对于第一种情况，建议的缓解措施是确保票证具有足够的信息供团队成员高效地满足要求。 对于第二种情况，您可能需要调整团队结构以包括更多资深工程师，或者获得外部指导和指导方面的批准。

## 受影响的产品和版本

[所有受支持的版本](../../../release/versions.md) 之：

- 云基础架构上的Adobe Commerce
- Adobe Commerce内部部署

## 在代码审阅中查找什么

### 样式

通过运行PhpStorm检查，可以自动测试样式（见下文）。

确保配置 [PHPMD和PHPC](https://developer.adobe.com/commerce/php/best-practices/phpstorm/code-inspection/) 并运行 [编码标准](https://github.com/magento/magento-coding-standard) CLI中的工具（也位于下方）。 虽然有一些重叠，但两者都有独特的测试。

### 惯例和结构

对惯例和结构的审查是手动进行的。

- 班级功能是否仅限于单个责任？
- 目录结构是否合理？
- 功能在正确的级别（服务器、客户端、CSS、JS、数据库、框架、基础架构）执行。
- 版本控制是否正确？
- 代码看起来是否不同寻常，或者是否像它试图以错误的方式绕过问题？
- 是否正确应用模块名称、包名称和存储库名称的命名约定？
- 验证全局CSS样式是否得到了周密应用并且未被过度使用。

### 完整性

完整性审查是手动完成的。

- 配置是否可以启用或禁用代码，以及所有必需代码是否均可按预期运行？
- 票证中提到的所有配置是否都存在？ 检查范围、数据类型、验证、转换和默认值。
- 是否始终在尽可能最低的级别（商店视图级别、网站级别或全局级别）检索配置？ 配置检索必须与中范围的定义匹配 `system.xml` 文件。
- 是否涵盖了技术规范流程图中的所有路径？ 是否涵盖所有其他技术规范？
- 是否为新功能定义了ACL？
- PhpDocs是否清楚？ 提交消息是否清晰？
- 是否有任何代码被注释掉，或者您是否看到调试代码？

### 性能

性能审查是手动完成的，如有疑问，可通过代码执行提供帮助。

- 查询是否在循环中执行？ 此循环可以位于已编辑文件之外。
- 你能发现任何 `cachable="false"` 属性？ 它们是否正确应用？

### 安全性

安全性审查是手动完成的，可通过文本搜索来辅助。 部分安全检查由自动测试处理。

- 是否根据需要记录异常？ 是否使用了正确的例外类型？
- 可以 `around` 应避免使用插件？
- 插件是否返回正确的数据类型？
- 您能否找到应使用数据库抽象层构建的任何原始SQL查询？
- 向任何类型的用户、管理员或前端公开任何新类型的数据吗？ 这种暴露是否构成安全风险？
- 是否验证用户生成的数据？ 来自浏览器的所有内容都被视为用户生成，包括Cookie值和服务器标头。

### 隐私和GDPR

隐私和审查 [GDPR](../../../security-and-compliance/privacy/gdpr.md) 手动完成。

- 该代码处理客户数据还是电子邮件？ 请特别注意。
- 如果此代码可以在循环中执行，它是否可以将客户数据从一个循环泄露到另一个循环中？
- 风险指标包括导入、cron作业、事务性电子邮件和批处理队列处理程序。
- 确保在循环中隔离用户数据。 Adobe建议使用工厂或存储库在循环中创建模型，这些模型无法在循环外部访问。

### 指导

对指导的审查是手动完成的。

- 寻找地方以分享知识，从而培养团队。
- 如果您的评论仅具有教育意义，但对满足标准不重要，则表明作者并非必须解决该问题。
- 如果您看到一些不错的内容，请告诉开发人员，尤其是当他们以非常好的方式处理您的某个评论时。 代码审查通常侧重于错误，但它们也应该鼓励和赞赏良好实践。 在指导方面，有时候告诉开发者他们做了什么比告诉他们做了什么错更有价值。

## 自动化

开发人员可以使用自动化检查DI编译、数据库架构、编辑器验证以及是否符合编码标准：

- DI编译 — 运行以下CLI命令以查看是否可以编译代码而不会出现任何问题。

  ```bash
  bin/magento module:disable -n -q --all || exit;
  bin/magento module:enable -n -q --all || exit;
  bin/magento cache:enable -n -q || exit;
  bin/magento cache:flush -n -q || exit;
  rm -rf generated/*
  rm -rf var/view_preprocessed/*
  rm -rf pub/static/*
  rm -rf var/cache/*
  bin/magento deploy:mode:set --skip-compilation production || exit;
  bin/magento setup:di:compile -vv || exit;
  bin/magento setup:static-content:deploy en_US || exit;
  bin/magento deploy:mode:set developer || exit;
  ```

- 数据库模式 `whitelist.json` — 运行以下CLI命令并验证 `db_schema_whitelist.json` 未添加或更改文件。

  ```bash
  bin/magento setup:db-declaration:generate-whitelist --module-name[=MODULE-NAME]
  ```

- Composer验证 — 验证 `composer.json` 文件，方法是在包含 `composer.json` 文件。

  ```bash
  composer validate
  ```

- 编码标准 — 安装和运行编码标准工具，并针对您的模块运行该工具。 以下文件说明如何通过键入命令使其在任意位置运行 `mcs ./app/code/Vendor/Module/`.

  ```bash
  #!/usr/bin/env bash
  $HOME/web/magento/magento-coding-standard/vendor/bin/phpcs --standard=Magento2 "$@"
  ```

- Phpstan

  ```bash
  ./vendor/bin/phpstan analyze app/code/Vendor/Module
  ```

- PhpStorm检查

- PhpStorm PHP复制/粘贴检测器
