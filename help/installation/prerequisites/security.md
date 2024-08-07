---
title: 内部部署安装安全
description: 了解改进Adobe Commerce本地安装的安全状态的方法。
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# 内部部署安装安全

[Security Enhanced Linux (SELinux)](https://selinuxproject.org/page/Main_Page)使CentOS和Ubuntu管理员能够更好地控制其服务器。 如果您使用的是SELinux *和* Apache必须启动与另一台主机的连接，则必须运行本节中讨论的命令。

>[!NOTE]
>
>Adobe没有关于使用SELinux的建议；如果需要，可以将其用于增强安全性。 如果您使用SELinux，则必须对其进行正确配置，否则Adobe Commerce会无法预测地正常运行。 如果选择使用SELinux，请查阅[CentOS wiki](https://wiki.centos.org/HowTos/SELinux)之类的资源以设置规则来启用通信。

## 有关使用Apache安装的建议

如果选择启用SELinux，则在运行安装程序时可能会遇到问题，除非按如下方式更改某些目录的&#x200B;*安全上下文*：

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

上述命令仅适用于Apache Web Server。 由于配置和安全要求的多样性，我们并不保证这些命令在任何情况下都有效。 有关更多信息，请参阅：

* [手册页](https://linux.die.net/man/8/httpd_selinux)
* [服务器实验室](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## 启用服务器间通信

如果Apache和数据库服务器位于同一主机上，则如果您计划使用使用`curl`的集成，请使用以下命令(例如 Paypal和USPS)。
要使Apache能够在启用SELinux的情况下启动与另一台主机的连接：

1. 要确定是否启用了SELinux，请使用以下命令：

   ```bash
   getenforce
   ```

   将显示`Enforcing`以确认SELinux正在运行。

   * CentOS： `setsebool -P httpd_can_network_connect=1`
   * Ubuntu： `setsebool -P apache2_can_network_connect=1`

## 在防火墙中打开端口

根据您的安全要求，您可能会发现有必要打开防火墙中的端口80和其他端口。 由于网络安全的敏感性质，Adobe强烈建议您在继续操作之前先咨询IT部门。 以下是一些建议的参考资料：

* Ubuntu： [Ubuntu文档页面](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS： [CentOS操作方法](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)。
