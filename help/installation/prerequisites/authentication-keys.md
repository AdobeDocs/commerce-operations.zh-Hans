---
title: 获取您的身份验证密钥
description: 请按照以下步骤检索凭据，以访问repo.magento.com上的Adobe Commerce Composer包。
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: fc63ca58cd2ff7c5ec597751980a39bfbe68aa5f
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# 获取您的身份验证密钥

`repo.magento.com`存储库是存储Adobe Commerce和第三方编辑器包的位置，需要身份验证。 使用您的Commerce Marketplace帐户生成一对32字符的&#x200B;*身份验证密钥*&#x200B;以访问存储库。

要获得对Adobe Commerce包的访问权限，您必须使用与有权访问这些包的MAGEID关联的密钥。 MAGEID通常是Adobe Commerce帐户的主要联系人，可能并不总是云基础架构项目Adobe Commerce的项目所有者。

>[!TIP]
>
>如果您遇到[错误](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html?lang=zh-Hans)，则可能没有访问包的授权，或者由于您帐户上的未结发票而导致访问权利已过期。
>
>* 如果您是该帐户的主要联系人，请确保该帐户中不存在未结发票。
>* 如果主要联系人提供的密钥不起作用，且帐户中没有未结发票，则主要联系人应联系[Adobe Commerce支持](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=zh-Hans#submit-ticket)寻求帮助。

要创建身份验证密钥，请执行以下操作：

1. 登录到[Commerce Marketplace](https://commercemarketplace.adobe.com/)。 如果没有帐户，请单击&#x200B;**注册**。

1. 单击页面右上角的帐户名称，然后选择&#x200B;**我的个人资料**。

1. 在“市场”选项卡中单击&#x200B;**访问密钥**。

   ![在Commerce Marketplace上获取安全访问密钥](../../assets/installation/cloud_access-key.png)

1. 单击&#x200B;**新建访问密钥**。 输入密钥的特定名称（例如，接收密钥的开发人员姓名），然后单击&#x200B;**确定**。

1. 新的公钥和私钥现在与您的帐户关联，您可以单击以复制这些帐户。 保存此信息或在使用项目时保持页面打开。 使用&#x200B;**公钥**&#x200B;作为用户名，使用&#x200B;**私钥**&#x200B;作为密码。

## 管理您的身份验证密钥

您还可以禁用或删除身份验证密钥。 例如，在有人离开您的组织后，出于安全原因，您可以禁用或删除密钥。

* 要禁用密钥：单击&#x200B;**禁用**。 如果要暂停使用密钥，可以执行此操作。
* 要启用以前禁用的键：请单击&#x200B;**启用**。
* 要删除密钥：单击&#x200B;**删除**。

### 管理SSH访问令牌

要使用SSH下载Adobe Commerce版本，您必须生成下载访问令牌。 要生成令牌，请执行以下操作：

1. 登录到您的[magento.com帐户](https://account.magento.com/customer/account/login)。
1. 单击页面顶部的&#x200B;**我的帐户**。
1. 单击&#x200B;**帐户设置** > **下载访问令牌**。

   ![访问您的密钥](../../assets/installation/connect_keys1.png)

1. 单击&#x200B;**生成新令牌**&#x200B;以替换和禁用现有令牌。

您必须使用MAGEID和令牌来下载版本。 您的MAGEID将显示在帐户页面的左上方。

例如：

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

使用您的身份验证密钥可以：

* [获取中继包（集成商、打包商）](../composer.md)
* [克隆GitHub存储库](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)（仅参与开发人员）
* [升级和管理模块](../../upgrade/modules/upgrade.md)
