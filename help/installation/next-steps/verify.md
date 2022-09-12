---
title: 验证安装
description: 按照以下步骤确认您的本地Adobe Commerce或Magento Open Source安装成功。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# 验证安装

转到 [店面](https://glossary.magento.com/storefront) 在Web浏览器中。 例如，如果您的安装基础 [URL](https://glossary.magento.com/url) is `http://www.example.com`，请在浏览器的地址或位置栏中输入。

下图显示了一个示例店面页面。 如果按如下方式显示，则表明安装成功！

![有鲁玛主题的店面](../../assets/installation/install-success_store-luma.png)

## 验证店面（无示例数据）

在Web浏览器中转到店面。 例如，如果您的安装基本URL为 `http://www.example.com`，请在浏览器的地址或位置栏中输入。

下图显示了一个示例店面页面。 如果按如下方式显示，则表明安装成功！

![用于验证安装是否成功的店面](../../assets/installation/install-success_store.png)

如果页面显示 `404 (Not Found)` 错误或未显示样式，请参阅 [故障诊断](https://support.magento.com/hc/en-us/articles/360032994352).

## 验证管理员

转到 [管理员](https://glossary.magento.com/magento-admin) 在Web浏览器中。 例如，如果您的安装基本URL为 `http://www.example.com`，且管理员URI为 `admin_au1nT`，输入 `http://www.example.com/admin_au1nT` 地址栏或位置栏。

( [管理员](https://glossary.magento.com/admin) URI由 `backend-frontname` 安装参数。)

出现提示时，以管理员身份登录。

下图显示了一个“管理员”页面示例。 如果按如下方式显示，则表明安装成功！

![验证安装成功的管理员](../../assets/installation/install_success_admin.png)

如果页面未显示样式，请参阅 [疑难解答](https://support.magento.com/hc/en-us/articles/360032994352).

如果您收到与以下内容类似的404（未找到）错误，请参阅 [PHP版本错误或在浏览器中访问Adobe Commerce时出现404错误](https://support.magento.com/hc/en-us/articles/360033117152).

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
