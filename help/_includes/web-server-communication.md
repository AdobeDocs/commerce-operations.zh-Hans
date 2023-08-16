---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---
# 安全的Web服务器通信

本主题将讨论使用传输层安全性(TLS)加密和以下内容的组合来保护Web服务器和搜索引擎(Elasticsearch或OpenSearch)之间通信的示例 [HTTP基本身份验证](https://datatracker.ietf.org/doc/html/rfc2617). 您也可以选择配置其他类型的身份验证；我们会提供该信息的参考。

(旧称安全套接字层(SSL)经常与TLS互换使用。 在本主题中，我们称为 *TLS*.)

>[!WARNING]
>
>除非另有说明，否则本主题中的所有命令必须以用户身份输入， `root` 权限。

## Recommendations

我们建议执行以下操作：

* 您的Web服务器使用TLS。

  TLS超出了本主题的范围；但是，我们强烈建议您在生产中使用真正的证书，而不是自签名证书。

* 您的搜索引擎与Web服务器在同一主机上运行。 在不同主机上运行搜索引擎和Web服务器超出了本主题的范围。

  将搜索引擎和Web服务器放在同一台主机上的优点是，它使得拦截加密通信变得不可能。 搜索引擎Web服务器不必与Adobe Commerce或Magento Open SourceWeb服务器相同；例如，Adobe Commerce可以运行Apache，Elasticsearch/OpenSearch可以运行nginx。

  如果搜索引擎向公共Web公开，则应当配置身份验证。 如果您的搜索引擎实例在网络内受到保护，则可能没有必要。 与您的托管提供商合作，确定您应当实施哪些安全措施来保护实例。

## 有关TLS的更多信息

请参阅以下资源之一：

* Apache

   * [Apache 2.4高度加密操作说明](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [如何在Apache for Ubuntu 14.04上创建SSL证书（数字海洋教程）](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [使用CentOS (CentOS wiki)设置SSL安全Web服务器](https://wiki.centos.org/HowTos/Https)

* 恩金克斯

   * [Nginx SSL终止](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [如何在Nginx上为Ubuntu 14.04创建SSL证书（数字海洋教程）](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Nginx SSL证书安装(digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
