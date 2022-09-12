---
title: 本地安装安全
description: 了解如何改进Adobe Commerce或Magento Open Source本地安装的安全态势。
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# 本地安装安全

[安全增强型Linux(SELinux)](https://selinuxproject.org/page/Main_Page) 使CentOS和Ubuntu管理员能够更好地控制其服务器的访问权限。 如果您使用的是SELinux *和* Apache必须启动到另一台主机的连接，您必须运行本节中讨论的命令。

>[!NOTE]
>
>Adobe没有关于使用SELinux的建议；如果需要，可以将其用于增强安全性。 如果使用SELinux，则必须正确配置它，否则Adobe Commerce和Magento Open Source可能无法预测地运行。 如果选择使用SELinux，请查阅资源，如 [CentOS维基](https://wiki.centos.org/HowTos/SELinux) 设置规则以启用通信。

## 关于使用Apache进行安装的建议

如果选择启用SELinux，则运行安装程序时可能会出现问题，除非更改 *安全上下文* 下面列出的一些目录：

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/app/etc
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/var
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/media
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/static
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/generated
```

上述命令仅适用于Apache Web服务器。 由于配置和安全要求的多样性，我们不能保证这些命令在所有情况下都能正常工作。 有关更多信息，请参阅：

* [手册页](https://linux.die.net/man/8/httpd_selinux)
* [服务器实验室](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## 启用服务器间通信

如果Apache和数据库服务器位于同一主机上，则如果您计划使用使用 `curl` (例如 Paypal和USPS)。
要启用Apache以启动与启用了SELinux的其他主机的连接，请执行以下操作：

1. 要确定是否启用了SELinux，请使用以下命令：

   ```bash
   getenforce
   ```

   `Enforcing` 显示，以确认SELinux正在运行。

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * 乌本图： `setsebool -P apache2_can_network_connect=1`

## 在防火墙中打开端口

根据您的安全要求，您可能会发现有必要在防火墙中打开端口80和其他端口。 由于网络安全的敏感性，Adobe强烈建议您在继续操作之前先咨询IT部门。 以下是一些建议的参考：

* 乌本图： [Ubuntu文档页面](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [CentOS操作方法](https://wiki.centos.org/HowTos/Network/IPTables).
