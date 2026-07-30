---
title: 安全策略：所需操作和截止日期
description: 了解云版本和软件依赖项上不支持的Adobe Commerce的安全实施，包括截止日期、所需操作和风险。
TQID: 'https://experienceleague.adobe.com/0JX-Z-dRjsiQk5jO-LLRi-J4GWdylTh4pOfXRPOabxs'
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
badgePaas: label="仅限Adobe Commerce on Cloud" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="仅适用于Adobe Commerce on Cloud版本2.4.4 - 2.4.9"
nudge: true
source-git-commit: 7512d5cd3fa1917c87b53e25ca69a3dc3c813727
workflow-type: tm+mt
source-wordcount: 1985
ht-degree: 0%

---

# 安全策略：必需的操作和截止日期

Adobe在云环境中实施Adobe Commerce的安全要求，包括支持的软件依赖项版本和支持的Adobe Commerce版本。 此页面描述了所需的内容、实施日期以及在不满足要求时会发生什么情况。

## 发生了什么？

Adobe公司安全策略要求Adobe上为Adobe Commerce托管的所有Cloud环境都在安全且兼容的软件上运行，其中包括：

1. 所有第三方软件依赖项(PHP、MariaDB、Elasticsearch/OpenSearch、Redis、RabbitMQ)的支持版本

1. 云上的Adobe Commerce的安全且合规的版本（版本2.4.8、2.4.9或最新版本）

这是为了减轻电子商务环境的安全风险。 在[表1](#determine-your-required-actions)的截止日期前未满足这些要求的环境将暂停入站流量，使店面脱机。 请将此通知视为具有强制执行日期的安全性和合规性要求。

您可能需要采取两项操作。

1. 检查是否支持第三方软件依赖项。 如果没有，请升级到支持的版本。

1. 如果您需要将Adobe Commerce on Cloud版本升级到支持的版本，请选中此选项。

在下面找到您的Adobe Commerce on Cloud版本以查看您需要执行的操作，并查看以下各项的要求：

1. 第三方软件依赖项

1. Adobe Commerce on Cloud版本

| 您的版本 | 升级第三方软件依赖项<br>(PHP、MariaDB、Elasticsearch/OpenSearch、Redis、RabbitMQ)<br>*有关详细信息和后续步骤，请参阅[操作1：升级第三方软件依赖项](#action-1-upgrade-third-party-software-dependencies)。* | 升级或迁移您的Adobe Commerce版本&#x200B;<br>*请参阅[操作2：如果需要升级Cloud上的Adobe Commerce](#action-2-if-you-need-to-upgrade-your-adobe-commerce-on-cloud-version)，请了解详细信息和后续步骤。* |
| --- | --- | --- |
| 2.4.4或2.4.5 | 要求在2026年10月30日之前完成。 | 在2027年6月1日之前要求 |
| 2.4.6或2.4.7 | 在2026年10月30日或2027年5月31日之前需要，具体取决于软件。 | 在2028年6月1日之前要求 |
| 2.4.8或2.4.9 | 在2026年10月30日或2027年5月31日之前需要，具体取决于软件。 | 当前非必需 |

**表1：版本**&#x200B;必需的操作和截止日期

## 谁也不需要采取行动

本通知不适用于：

* Cloud版本2.4.8或2.4.9上的Adobe Commerce及其环境运行受支持的第三方软件版本的客户

* [!DNL Adobe Commerce as a Cloud Service]上的客户

### 如何检查您运行的版本

您需要电子商务管理员的帮助，以执行以下步骤来检查您运行的版本。

**您的Adobe Commerce on Cloud版本**

1. 登录到Adobe Commerce管理面板。

   当前版本应显示在任何Admin页面的右下角。

1. 如果版本未显示在管理员中，请使用[Adobe Commerce命令行工具](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli){target="_blank"}运行version命令：

   ```shell
   bin/magento --version
   ```

**您的软件依赖项版本**

1. 登录到[云控制台](https://console.adobecommerce.com/)。
1. 打开相关项目，然后选择要查看的环境。
1. 在`.magento/services.yaml`文件中检查该环境的服务配置，该文件定义了Adobe Commerce在云基础架构上使用的受支持服务名称和版本。
有关详细说明，请参阅[配置服务](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/services/config-services){target="_blank"}文档。

## 为什么这一安全授权很重要

已超过供应商支持终止的软件不再接收安全修补程序，这意味着无法修复该软件中的已知安全问题。 此外，根据[Adobe生命周期策略](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy)：

* **Adobe Commerce版本2.4.4和2.4.5**&#x200B;现在仅接收核心应用程序的有限且孤立的安全修复，直到2027年5月31日为止。 这种有限的支持不包括质量修复、对应用程序依赖项（例如，PHP）的兼容性支持或平台依赖项更新

* **Adobe Commerce 2.4.6**&#x200B;将在2027年8月30日之前获得扩展支持，并将在2028年5月31日之前仅接收核心应用程序的有限且独立的安全修复

* **Adobe Commerce版本2.4.7**&#x200B;将在2027年5月31日之前获得标准支持，并在2028年5月31日之前获得扩展支持

* Cloud版本2.4.8和2.4.9 **上的** Adobe Commerce仍受支持，目前不需要升级版本。

在不受支持的软件上继续运营电子商务店面会给您的企业带来真实且不断增加的安全风险，包括您维护PCI合规性和保护客户数据的能力。

>[!IMPORTANT]
>
>如果您的环境在[表1](#determine-your-required-actions)中详述的截止日期之前未满足要求，则Adobe将暂停到受影响环境的入站流量。 您的电子商务店面将下线，不再为购物者服务。 请参阅[如果不执行任何操作将发生什么情况](#what-happens-if-no-action-is-taken)。

## 有关您需要采取的操作的详细信息

### 操作1：升级第三方软件依赖项

根据软件的不同，所有不支持的软件依赖项都必须按照下表共享的时间表进行升级。 您可以在[Cloud Console](https://console.adobecommerce.com/)中查看环境，并使用这些[说明](#check-software-dependency-versions)检查运行的依赖项版本。 软件依赖项升级适用于Cloud版本2.4.4到2.4.9上的所有Adobe Commerce。

| 依赖关系 | 版本 | 必须升级到 | 执行日期 |
| --- | --- | --- | --- |
| PHP | 8.1及以下 | 8.2或更高版本 | 2027年5月31日 |
| MariaDB/Galera | 10.5及以下 | 10.6或更高版本 | 2026年10月30日 |
| MariaDB/Galera | 大于10.5但小于10.11 | 10.11或更高版本 | 2027年5月31日 |
| Elasticsearch | 任何版本 | OpenSearch：<br><br> — 适用于2.4.4和2.4.5客户的版本2.19<br> — 适用于2.4.6及更高版本客户的版本3。 | 2026年10月30日 |
| OpenSearch | 1.x | 版本2.19（适用于2.4.4和2.4.5客户）。<br>版本3（适用于2.4.6及更高版本客户）。 | 2027年5月31日 |
| Redis | 5及以下 | Valkey 8或更高版本 | 2027年5月31日 |
| RabbitMQ | 3.9及以下 | 3.13或更高版本 | 2026年10月30日 |
| RabbitMQ | 大于3.9但小于3.13 | 4.3或更高版本 | 2027年5月31日 |

**表2：软件依赖项升级要求**

#### 为第三方软件依赖项升级做准备

Adobe将帮助您直接升级这些软件依赖项。

* **快速入门：**&#x200B;打开[支持票证](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket)，其中列出需要升级的环境和涉及的依赖项。 在执行日期之前至少打开30天工单，以便我们的团队可以安排工作。

* **停机时间：** Adobe将在计划时与您确认预期的窗口。

* **测试：**&#x200B;在生产之前升级并验证非生产环境。 至少需要验证结帐、搜索、购物车以及任何自定义集成。 要求适用于您的所有环境，因此计划升级每个环境而不是单独进行生产。

* **兼容性：**&#x200B;这些更改大多是同一软件中的版本升级，风险较低。 以下内容值得密切关注：

  * **Elasticsearch到OpenSearch**&#x200B;和&#x200B;**Redis到Valkey**&#x200B;正在迁移到其他软件，而不是版本升级。 引用原始服务的自定义代码、扩展或配置可能需要更新。
  * **PHP 8.1到8.2**&#x200B;可以在自定义代码和第三方扩展中显示弃用。

如果您使用第三方扩展，请与扩展供应商确认其当前版本支持您的目标版本。 如果您与解决方案集成商合作，请让他们参与规划和验证。

### 操作2：如果您需要升级Adobe Commerce on Cloud版本，请执行以下操作：

您可以选择(i)升级到支持的云版Adobe Commerce，或(ii)迁移到Adobe Commerce as a Cloud Service（Adobe的完全托管商务平台）

无论您选择哪个选项，当前版本的强制实施日期均适用。

| 当前版本 | 操作 | 执行日期 |
| --- | --- | --- |
| 使用Cloud上的Adobe Commerce版本2.4.4或2.4.5 | 升级到Cloud版本2.4.9（或最新版本）上的Adobe Commerce或迁移到Adobe Commerce as a Cloud Service | 2027年6月1日 |
| 使用Cloud上的Adobe Commerce版本2.4.6或2.4.7 | 升级到Cloud版本2.4.9（或最新版本）上的Adobe Commerce或迁移到Adobe Commerce as a Cloud Service | 2028年6月1日 |
| 在Cloud版本2.4.8或2.4.9中使用Adobe Commerce | 此时无需Adobe Commerce on Cloud版本升级操作。 操作1中的软件依赖项截止日期仍然适用。 | 不适用 |

**表3：如果必须在云版本**&#x200B;上升级当前的Adobe Commerce，则准则和截止日期为

有关Cloud版本2.4.9上的Adobe Commerce和Adobe Commerce as a Cloud Service的更多详细信息，请参阅以下矩阵，以便您做出明智的决策。

**表4：升级到Cloud上的Adobe Commerce与迁移到Adobe Commerce as a Cloud Service**

| | Cloud上的Adobe Commerce版本2.4.9 | Adobe Commerce as a Cloud Service |
| --- | --- | --- |
| 内容 | 最新的Adobe Commerce版本，包含全面的安全保护、质量修复和平台依赖关系更新。 | Adobe完全托管的commerce平台，为持续创新而构建，无需升级开销。 [了解详情](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview)。 |
| 最适合您，如果 | 您现在希望继续管理自己的基础架构、升级和修补程序。 您可以在准备就绪后迁移到Adobe Commerce as a Cloud Service 。 | 您想要永久推迟升级周期，降低总拥有成本，并自动获得Adobe的最新功能，而无需额外付费。 |
| 主要优势 | 满足当前的安全要求，同时保留现有设置。 | 闪电般快速的边缘交付店面、高度可扩展的目录、原生数字资产管理以及内置的创意AI，所有这些都基于Adobe管理的基础架构。 |

## 如果未采取任何操作，会发生什么情况？

如果环境在[以上](#determine-your-required-actions)共享的实施日期之前未满足这些要求，Adobe将采取适当措施。 这包括暂停流向受影响的基础结构的流量，因此，您的电子商务店面将脱机。

如果环境在流量暂停后继续保持不合规状态，Adobe可以终止云服务，启动停用过程。 由于停用，托管电子商务环境中的所有数据和资产（包括所有实例、环境和分支）将被永久删除且无法恢复。

## Adobe将如何帮助您的摘要

无论您是升级还是迁移，Adobe都提供了一些工具和支持，以便让您的过渡尽可能顺利。

**如果您选择升级到Cloud版本2.4.9**&#x200B;上的Adobe Commerce

* **升级兼容性报告：** Adobe提供了一个详细的报告，该报告准确识别了升级到Adobe Commerce版本2.4.9所需的内容，包括时间和成本范围。 [生成升级兼容性报告](https://supportinsights.adobe.com/commerce/tab/main)。

* **软件依赖项升级：**&#x200B;由于您无法直接升级软件依赖项，因此[为Adobe打开支持票证](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket){target="_blank"}为您处理升级。 有关详细信息，请参阅[配置服务](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/configuration/overview){target="_blank"}。

**如果您选择迁移到Adobe Commerce as a Cloud Service**

Adobe提供了一些工具，可降低迁移到Adobe Commerce as a Cloud Service的成本和时间。 这是免费的。 这些工具仅适用于迁移；它们不用于Adobe Commerce on Cloud上的版本升级。 有关完整的迁移指南（包括迁移路径和阶段），请参阅[迁移概述](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/overview)。

* **迁移评估：**&#x200B;对自定义设置的迁移复杂性进行评级。 请参阅[迁移评估工具概述](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/assessment)。

* **数据迁移：** [批量与增量数据迁移工具](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/bulk-data/migration-tool)可将您的数据移动到新的Adobe Commerce as a Cloud Service环境。

* Adobe的[AI辅助迁移和开发人员工具](https://developer.adobe.com/commerce/extensibility/developer-agent/)（包括&#x200B;**[!DNL Adobe Developer App Builder]**&#x200B;和&#x200B;**[!DNL Commerce Storefront powered by Edge Delivery Services]**）有助于加快店面现代化和扩展重新平台。

如果您有任何问题，请联系您的客户团队、解决方案客户经理、续订专家或联系[支持服务](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket)。
