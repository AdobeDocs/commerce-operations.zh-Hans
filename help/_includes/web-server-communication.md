---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---
# 安全Web服务器通信

本主题讨论了使用传输层安全(TLS)加密和 [HTTP基本身份验证](https://datatracker.ietf.org/doc/html/rfc2617). 您也可以选择配置其他类型的身份验证；我们提供资料。

(旧术语“安全套接字层(SSL)”经常与TLS交替使用。 在本主题中，我们参考 *TLS*.)

>[!WARNING]
>
>除非另有说明，否则本主题中的所有命令都必须以用户身份输入， `root` 权限。

## Recommendations

我们建议执行以下操作：

* 您的Web服务器使用TLS。

   TLS不在本主题的范围之内；但是，我们强烈建议您在生产中使用实际证书，而不是自签名证书。

* 您的搜索引擎在与Web服务器相同的主机上运行。 在不同主机上运行搜索引擎和Web服务器不在本主题的涵盖范围内。

   将搜索引擎和Web服务器放在同一台主机上的好处是它使得拦截加密通信成为不可能。 搜索引擎Web服务器不必与Adobe Commerce或Magento Open SourceWeb服务器相同；例如，Adobe Commerce可以运行Apache，而Elasticsearch/OpenSearch可以运行nginx。

   如果搜索引擎公开到公共Web，则应配置身份验证。 如果您的搜索引擎实例在您的网络中受到保护，则可能不必这样做。 与您的托管提供商合作，确定您应该实施哪些安全措施来保护您的实例。

## 有关TLS的更多信息

请参阅以下资源之一：

* Apache

   * [Apache 2.4强加密操作方法](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [如何在Apache for Ubuntu 14.04上创建SSL证书（Digitalocean教程）](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [使用CentOS(CentOS Wiki)设置SSL安全Web服务器](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [初始SSL终止](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [如何在Nginx上为Ubuntu 14.04创建SSL证书（Digitalocean教程）](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Nginx SSL证书安装(digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
