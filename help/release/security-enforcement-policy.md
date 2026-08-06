---
title: 保护Commerce环境所需的操作和截止日期
description: 了解云版本和软件依赖项上不支持的Adobe Commerce的安全实施，包括截止日期、所需操作和风险。
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2:
  - id: f2261633-201d-46c5-8a66-999e70527a83
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
badgePaas: label="Adobe Commerce on Cloud 2.4.4 — 仅限2.4.9" type="Informative" url="https://experienceleague.adobe.com/zh-hans/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Cloud 2.4.4到2.4.9版本的Adobe Commerce"
nudge: true
source-git-commit: c3ea400087a14aa1021ab6998b9de48c33787cc9
workflow-type: tm+mt
source-wordcount: 2174
ht-degree: 0%

---


# 保护Commerce环境所需的操作和截止日期

>[!NOTE]
>
> **适用于：**&#x200B;运行Adobe Commerce 2.4.4到2.4.9版本的Adobe Commerce on Cloud (PaaS)环境。

网络安全格局正在发生根本性变化，企业已建立的防御机制需要迅速演变。 安全对于电子商务企业至关重要，因为在线交易要求他们处理敏感的个人和业务数据，在出现违规时使他们面临财务和身份风险。 PaaS电子商务环境采用了一种分担责任的模式，客户负责应用层依赖项的安全性和维护工作、与第三方软件的集成以及部署管道。

在Adobe，我们仍致力于应对不断变化的风险，并确保在云上客户设置符合最高安全标准的Adobe Commerce。 这包括：

1. 每月进行隔离的安全修复，以针对关键漏洞提供更快、更可预测的保护

2. Commerce的云修补程序包，用于确保交付Adobe修补程序和修补程序，以改进与云环境的集成并允许快速解决关键问题

3. 生命周期实施策略

4. 周期外的修补程序（如有必要）

5. 年度补丁发布，提供长期支持


虽然Adobe会采取必要步骤来帮助确保客户的安全，但Adobe Commerce on Cloud的共享责任模型要求我们的客户始终使用Adobe Commerce on Cloud的支持版本和第三方软件、应用应用程序修补程序、审核第三方扩展和安全自定义代码。 供应商支持终止的软件不再接收安全修补程序，软件中的安全问题得不到解决。继续在不支持的软件上运行电子商务店面会产生真实且不断增加的安全风险。

本页概述了Adobe Commerce（版本2.4.4到2.4.9）上所有客户为确保其电子商务环境的安全而需要采取的操作，以及实施日期和不满足安全要求时的预期情况。

## 维护安全和合规的环境所需的操作

要确保电子商务环境的安全并减轻风险，Adobe Commerce on Cloud（版本2.4.4到2.4.9）上的所有客户都需要使用：

1. 所有第三方软件依赖项(PHP、MariaDB、Elasticsearch、OpenSearch、Redis、RabbitMQ)的支持版本

1. 云上受支持的安全版本的Adobe Commerce。 完全支持的版本包括2.4.8、2.4.9或最新发布的版本。 请参阅[生命周期策略](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/release/planning/lifecycle-policy)文档。

遵循以下准则以检查您是否需要采取措施来保护云环境上的Adobe Commerce。 如果在表1中列出的截止日期前未满足安全要求的环境，将会暂停入站流量，从而使店面离线。 如果您担心要达到截止日期，请尽快联系您的帐户团队或[Adobe支持](https://experienceleague.adobe.com/zh-hans/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket)。

>[!NOTE]
>
> 此指南不适用于[!DNL Adobe Commerce as a Cloud Service] (SaaS)环境或Adobe Commerce内部部署。

**表1：安全要求和截止日期**

| 云上的Adobe Commerce版本 | 升级到支持的第三方软件依赖项 | 升级到Cloud版本上的最新Adobe Commerce，或迁移到[!DNL Adobe Commerce as a Cloud Service] |
| --- | --- | --- |
| 2.4.4或2.4.5 | 要求在2026年10月30日之前完成。 | 在2027年6月1日之前要求 |
| 2.4.6或2.4.7 | 在2026年10月30日或2027年5月31日之前需要，具体取决于软件。 | 在2028年6月1日之前要求 |
| 2.4.8或2.4.9 | 在2026年10月30日或2027年5月31日之前需要，具体取决于软件。 | 当前非必需 |

## 保护环境的详细步骤

请联系您的Commerce管理员以完成以下步骤。

### 操作1：验证和升级第三方软件依赖项

检查您的环境是否运行供应商支持的以下第三方软件依赖项版本：PHP、MariaDB、Elasticsearch、OpenSearch、Redis、RabbitMQ。 如果没有，请将软件依赖项升级到支持的版本。

#### 步骤1：检查您的第三方软件依赖项版本

1. 登录到[Cloud Console](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/start/cloud-console)，您可以在其中查看所有环境。
2. 打开相关项目，然后选择要查看的环境。
3. 在`.magento/services.yaml`文件中检查该环境的服务配置，该文件定义了Adobe Commerce on Cloud支持的服务名称和版本。
4. 使用[配置服务](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)中的说明检查每个环境正在运行的依赖项版本。

所有不支持的软件依赖项都必须升级到下表2中共享的时间表所列的版本。

**表2：所需的依赖项升级**

| 依赖关系 | 版本 | 必须升级到 | 截止日期 |
| --- | --- | --- | --- |
| PHP | 8.1及以下 | 8.2或更高版本 | 2027年5月31日 |
| MariaDB/Galera | 10.5及以下 | 10.6或更高版本 | 2026年10月30日 |
| MariaDB/Galera | 大于10.5但小于10.11 | 10.11或更高版本 | 2027年5月31日 |
| Elasticsearch | 任何版本 | OpenSearch：适用于2.4.4和2.4.5客户的版本2.19。 适用于2.4.6及更高版本的客户的版本3 。 | 2026年10月30日 |
| OpenSearch | 1.x | 适用于2.4.4和2.4.5客户的版本2.19。 适用于2.4.6及更高版本的客户的版本3 。 | 2027年5月31日 |
| Redis | 5及以下 | Valkey版本8或更高版本 | 2027年5月31日 |
| RabbitMQ | 3.9及以下 | 版本3.13或更高版本 | 2026年10月30日 |
| RabbitMQ | 大于3.9但小于3.13 | 4.3或更高版本 | 2027年5月31日 |

#### 步骤2：为第三方软件依赖项升级做准备

Adobe将帮助您直接升级这些软件依赖项。

* **开始：**&#x200B;打开[支持票证](https://experienceleague.adobe.com/zh-hans/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case)，其中列出需要升级的环境和涉及的依赖项。 在执行日期之前至少打开30天工单，以便Adobe能够安排工作。

* **停机时间：** Adobe将在计划时与您确认预期的窗口。

* **测试：**&#x200B;在生产之前升级并验证非生产环境。 至少需要验证结帐、搜索、购物车以及任何自定义集成。 要求适用于您的所有环境，因此请计划升级每个环境，而不是单独进行生产。

* **兼容性：**&#x200B;这些更改大多是同一软件中的版本升级，风险较低。 以下变化值得密切关注：

  * **Elasticsearch到OpenSearch**&#x200B;和&#x200B;**Redis到Valkey**&#x200B;正在迁移到其他软件，而不是版本升级。 引用原始服务的自定义代码、扩展或配置可能需要更新。
  * 从&#x200B;**PHP 8.1升级到8.2**&#x200B;可能会在自定义代码和第三方扩展中显示弃用。

如果您使用第三方扩展，请与供应商确认其当前版本支持您的目标版本。 如果您与解决方案集成商合作，请让他们参与规划和验证。

### 操作2：检查您的Adobe Commerce on Cloud版本并升级到支持的版本

#### 步骤1：检查您的Adobe Commerce on Cloud版本和所需操作

1. 登录到Adobe Commerce管理面板。

   当前版本将显示在任何Admin页面的右下角。

1. 如果版本在“管理”面板中处于隐藏状态，请使用Adobe Commerce [命令行工具](../configuration/cli/config-cli.md)通过运行以下命令来查看版本：

   ```shell
   bin/magento --version
   ```

在下表中，查看Adobe Commerce版本所需的操作。

**表3： Adobe Commerce on Cloud版本升级要求**

| 云上的Adobe Commerce的当前版本 | 必需操作 | 截止日期 |
| --- |--- |--- |
| 版本2.4.4或2.4.5 | 升级到Cloud上的Adobe Commerce版本2.4.9（或最新版本）或迁移到[!DNL Adobe Commerce as a Cloud Service]。<br>原因：在2027年5月31日之前，版本2.4.4和2.4.5将仅接收核心应用程序的有限且独立的安全修复。 这不包括质量修复、对应用程序依赖项（例如，PHP）的兼容性支持或平台依赖项更新。 请参阅Adobe的[生命周期策略](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/release/planning/lifecycle-policy)。 | 2027年6月1日 |
| 版本2.4.6或2.4.7 | 升级到Cloud上的Adobe Commerce版本2.4.9（或最新版本）或迁移到[!DNL Adobe Commerce as a Cloud Service]。<br>原因：在2027年8月30日之前，版本2.4.6将获得扩展支持，并且在2028年5月31日之前，将仅获得核心应用程序的有限且独立的安全修复。 版本2.4.7将在2027年5月31日之前获得标准支持，并在2028年5月31日之前获得扩展支持。 请参阅Adobe的[生命周期策略](https://experienceleague.adobe.com/zh-hans/docs/commerce-operations/release/planning/lifecycle-policy)。 | 2028年6月1日 |
| 版本2.4.8或2.4.9 | 无需Adobe Commerce on Cloud版本升级操作。 操作1中的第三方软件依赖项截止日期仍然适用。<br>原因：未设置截止日期。 | 不适用 |

#### 步骤2：确定升级或迁移路径

如果您需要升级Adobe Commerce on Cloud版本，则有两个选项：

1. 升级到支持的云版Adobe Commerce
1. 迁移到[!DNL Adobe Commerce as a Cloud Service] (SaaS)

下表可帮助您比较各种选项并确定最适合您的路径。

**表4：云端上的Adobe Commerce与[!DNL Adobe Commerce as a Cloud Service]**&#x200B;的比较

| | Cloud上的Adobe Commerce版本2.4.9 | [!DNL Adobe Commerce as a Cloud Service] |
|---|---|---|
| **它是什么** | 最新的Adobe Commerce版本，包含全面的安全保护、质量修复和平台依赖关系更新。 | Adobe完全托管的commerce平台，为持续创新而构建，无需升级开销。 [了解详情](https://experienceleague.adobe.com/zh-hans/docs/commerce/cloud-service/overview)。 |
| **如果您愿意** | 您希望继续管理自己的基础架构、升级和修补程序。 | 您想要永久推迟升级周期，降低总拥有成本，并自动获得Adobe的最新功能，而无需额外付费。 |
| **关键优势** | 满足安全要求，同时保留现有设置。 | 闪电般快速的边缘交付店面、高度可扩展的目录、原生数字资产管理以及内置的创意AI，所有这些都基于Adobe管理的基础架构。 |

## 如果在截止日期前没有采取任何操作，会发生什么情况？

Adobe将一如既往地支持您执行必要的步骤，以便采用受支持的第三方软件版本、升级到Adobe Commerce on Cloud的最新版本或迁移到Adobe Commerce as a Cloud Service。  如果您担心难以在截止日期前完成任务并需要短期延期，请尽快联系您的客户团队或[Adobe支持](https://experienceleague.adobe.com/zh-hans/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket)。

如果到上述共享的实施日期时环境尚未满足安全要求，Adobe将强制采取适当的措施来维护Adobe Commerce平台及其客户的安全。 这包括暂停流向受影响的基础结构的流量，因此，您的Commerce店面将脱机。

如果环境在流量暂停后继续保持不合规状态，Adobe可以终止云服务，启动停用过程。 由于停用，托管商业环境中的所有数据和资产（包括所有实例、环境和分支）都将永久删除并且无法恢复。

## 支持升级或迁移的资源

**如果您选择升级到Cloud版本2.4.9上的Adobe Commerce：**

* **升级兼容性报告：** Adobe提供了一个详细的报告，该报告准确地识别了升级到Adobe Commerce版本2.4.9所需的内容，包括识别哪些模块和文件需要更新、严重问题的数量等。 [生成升级兼容性报告](https://supportinsights.adobe.com/commerce/tab/main)。

* **软件依赖项升级：**&#x200B;由于您无法直接升级软件依赖项，请为Adobe打开[支持票证](https://experienceleague.adobe.com/zh-hans/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case)为您处理升级。 有关详细信息，请参阅[配置服务](https://experienceleague.adobe.com/zh-hans/docs/commerce-on-cloud/user-guide/configure/service/services-yaml)。

**如果您选择迁移到[!DNL Adobe Commerce as a Cloud Service]：**

Adobe提供的工具减少了迁移到[!DNL Adobe Commerce as a Cloud Service]的成本和时间。 您无需支付任何费用即可获得它们。 这些工具仅适用于迁移。 它们不用于Adobe Commerce on Cloud版本升级。 有关完整的迁移指南（包括迁移路径和阶段），请参阅[迁移概述](https://experienceleague.adobe.com/zh-hans/docs/commerce/cloud-service/migration/overview)。

* **迁移评估：**&#x200B;对自定义设置的迁移复杂性进行评级。 请参阅[迁移评估工具概述](https://experienceleague.adobe.com/zh-hans/docs/commerce/cloud-service/migration/migration-tools/assessment)。

* **数据迁移：** [批量与增量数据迁移工具](https://experienceleague.adobe.com/zh-hans/docs/commerce/cloud-service/migration/migration-tools/bulk-data/migration-tool)可将您的数据移动到新的[!DNL Adobe Commerce as a Cloud Service]环境。 如需访问权限，请联系[Adobe支持](https://experienceleague.adobe.com/zh-hans/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket)。

* **AI辅助迁移和开发人员工具：**&#x200B;由Edge Delivery Services提供支持的Adobe Developer App Builder和Commerce店面可帮助加快店面现代化和扩展重新平台。

如果您有任何问题，请与帐户团队联系或联系[支持服务](https://experienceleague.adobe.com/zh-hans/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket)。

>[!MORELIKETHIS]
>
>* [生命周期策略](lifecycle-policy.md)
>* 云中Adobe Commerce的[版本升级实施策略](version-upgrade-enforcement-policy.md)
>* [共享责任安全和运营模型](../security-and-compliance/shared-responsibility.md)
