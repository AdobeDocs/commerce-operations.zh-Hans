---
title: 使用Apache设置多个网站
description: 按照本教程中的说明，使用Apache设置多个网站。
exl-id: 4c6890b3-f15a-46f2-a3e8-6f2a9b57a6ad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# 使用Apache设置多个网站

我们假定：

如有必要，复制现有 `index.php` 网站或商店视图的入口点脚本，并添加到该脚本中：

- 您正在使用开发计算机（笔记本电脑、虚拟机等）

  在托管环境中部署多个网站可能需要执行其他任务；有关更多信息，请咨询您的托管提供商。

  在云基础架构上设置Adobe Commerce需要执行其他任务。 完成本主题中讨论的任务后，请参见 [设置多个网站或商店](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 在 _云基础架构上的Commerce指南_.

- 每个网站使用一个虚拟主机；虚拟主机配置文件为 `/etc/httpd/httpd.conf`

  不同操作系统上的不同版本Apache对虚拟主机的设置有所不同。 请参阅 [Apache文档](https://httpd.apache.org/docs/2.4/vhosts) 或网络管理员（如果您不确定如何设置虚拟主机）。

- Commerce软件安装在 `/var/www/html/magento2`
- 您拥有默认网站以外的两个网站：

   - `french.mysite.mg` 带有网站代码 `french` 和存储视图代码 `fr`
   - `german.mysite.mg` 带有网站代码 `german` 和存储视图代码 `de`

## 使用Apache设置多个网站的路线图

设置多个存储由以下任务组成：

1. [设置网站、商店和商店视图](ms-admin.md) 在“管理员”中。
1. 创建一个 [Apache虚拟主机](#step-2-create-apache-virtual-hosts) 每个Commerce网站。

## 步骤1：在“管理员”中创建网站、商店和存储视图

请参阅 [在“管理员”中设置多个网站、商店和商店视图](ms-admin.md).

## 步骤2：创建Apache虚拟主机

本节讨论如何设置以下项目的值： `MAGE_RUN_TYPE` 和 `MAGE_RUN_CODE` 使用Apache Server变量 `SetEnvIf` 在虚拟主机中。

有关详情 `SetEnvIf`，请参见：

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**创建Apache虚拟主机**：

1. 作为用户，具有 `root` 权限，在文本编辑器中打开虚拟主机配置文件。

   例如，打开 `/etc/httpd/conf/httpd.conf`

1. 找到部分，其开头为 `<VirtualHost *:80>`.
1. 在任何现有虚拟主机之后创建以下虚拟主机：

   ```conf
   <VirtualHost *:80>
      ServerName          mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          french.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "french"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          german.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "german"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   ```

1. 将更改保存到 `httpd.conf` 并退出文本编辑器。
1. 重新启动Apache：

   - CentOS： `service httpd restart`
   - Ubuntu： `service apache2 restart`

## 验证您的站点

除非您已经为商店的URL设置了DNS，否则您必须在的 `hosts` 文件：

1. 找到您的操作系统 `hosts` 文件。
1. 采用以下格式添加静态路由：

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. 在浏览器中转到以下URL之一：

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- 在托管环境中部署多个网站可能需要执行其他任务；有关更多信息，请咨询您的托管提供商。
>- 在云基础架构上设置Adobe Commerce需要执行其他任务；请参阅 [设置多个云网站或商店](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) 在 _云基础架构上的Commerce指南_.

### 故障排除

- 如果法语和德语网站返回404但您的管理员已加载，请确保您已完成 [步骤6：将存储代码添加到基本URL](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- 如果所有URL都返回404，请确保已重新启动Web服务器。
- 如果管理员无法正常运行，请确保正确设置虚拟主机。
