---
title: 获取您的身份验证密钥
description: 请按照以下步骤检索凭据，以访问repo.magento.com上的Adobe Commerce和Magento Open Source编辑器包。
source-git-commit: d209d3f7fde55f7495488f2cbeeebf21024875ed
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---


# 获取您的身份验证密钥

的 `repo.magento.com` 存储库是存储Adobe Commerce和Magento Open Source及第三方编辑器包的位置，需要进行身份验证。 使用Commerce Marketplace帐户生成一对32个字符的 *身份验证密钥* 访问存储库。

要获得对Adobe Commerce和Magento Open Source包的访问权限，您必须使用与已获得这些包访问权限的MAGEID关联的密钥。 MAGEID通常是Adobe Commerce帐户上的主要联系人，并且可能并非总是云基础架构项目上Adobe Commerce的项目所有者。

>[!TIP]
>
>如果您遇到 [错误](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html)，则您可能无权访问该包，或者由于您帐户上的未清发票而导致访问权利已过期。
>
>* 如果您是帐户上的主要联系人，请确保帐户上没有列出未清发票。
>* 如果主要联系人提供的密钥无效，且帐户上没有未清发票，请联系 [Adobe Commerce支持](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 以获取有关使用主要联系人的MAGEID的帮助。


要创建身份验证密钥，请执行以下操作：

1. 登录到 [Commerce Marketplace](https://marketplace.magento.com). 如果您没有帐户，请单击 **注册**.
1. 单击页面右上方的帐户名称，然后选择 **我的个人资料**.

1. 单击 **访问密钥** （在Marketplace选项卡中）。

   ![在Commerce Marketplace上获取安全访问密钥](../../assets/installation/cloud_access-key.png)

1. 单击 **创建新访问密钥**. 输入键的特定名称（例如，接收键的开发人员的名称），然后单击 **确定**.

1. 新的公钥和私钥现已与您的帐户关联，您可以单击以复制这些帐户。 使用项目时，请保存此信息或保持页面打开状态。 使用 **公钥** 作为您的用户名和 **私钥** 作为密码。

## 管理您的身份验证密钥

您还可以禁用或删除身份验证密钥。 例如，出于安全原因，您可以在某人离开您的组织后禁用或删除密钥。

* 要禁用键，请执行以下操作：单击 **禁用**. 如果要暂停密钥的使用，可以执行此操作。
* 要启用以前禁用的键，请执行以下操作：单击 **启用**.
* 要删除键，请执行以下操作：单击 **删除**.

### 管理SSH访问令牌

要使用SSH下载Adobe Commerce版本，您必须生成下载访问令牌。 要生成令牌，请执行以下操作：

1. 登录到 [magento.com帐户](https://account.magento.com/customer/account/login).
1. 单击 **我的帐户** 的双曲余切值。
1. 单击 **帐户设置** > **下载访问令牌**.

   ![访问您的密钥](../../assets/installation/connect_keys1.png)

1. 单击 **生成新令牌** 替换和禁用现有令牌。

您必须使用MAGEID和令牌来下载版本。 您的MAGEID显示在帐户页面的左上角。

例如：

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

使用您的身份验证密钥可以：

* [获取元数据包（集成商、打包商）](../composer.md)
* [克隆GitHub存储库](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) （仅供开发人员参与）
* [升级和管理模块](../../upgrade/modules/upgrade.md)
