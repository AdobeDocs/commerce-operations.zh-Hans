---
title: 适用于GraphQL API的应用程序服务器
description: 按照以下说明在Adobe Commerce部署中为GraphQL API启用应用程序服务器。
badgeCoreBeta: label="2.4.7-beta1" type="informative"
exl-id: 346cc722-131e-4ed0-bc8c-23c3a1e58258
source-git-commit: f085c0a77fe59ff3b2d76abbd6965b6bc8ee69db
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# 适用于GraphQL API的应用程序服务器

Commerce Application Server for GraphQL API使Adobe Commerce能够维护Commerce GraphQL API请求之间的状态，并缩短每个请求的引导时间。 通过在进程之间共享应用程序状态，API请求可以显着提升效率。

此Application Server Beta版本仅适用于运行PHP 8.1或8.2的内部部署。 它不支持基于云的部署。 它尚不支持B2B GraphQL功能。 当配置此版本的PHP应用程序服务器时，GraphQL请求在内部部署中可能无法按预期工作。

## 谁可以使用应用程序服务器？

应用程序服务器仅适用于本地Commerce部署。

## 为GraphQL API启用应用程序服务器

此 `ApplicationServer` 模块(`Magento/ApplicationServer/`)为GraphQL API启用应用程序服务器。

运行应用程序服务器需要安装Open Swool扩展并对部署的Nginx配置文件进行细微更改，才能在本地运行此应用程序服务器。

### 开始之前

在启用 `ApplicationServer` 模块：

* 配置Nginx

* 安装和配置Open Swoole v22扩展

### 配置Nginx

您的特定Commerce部署决定了如何配置Nginx。 通常，Nginx配置文件默认名为 `nginx.conf` 和位于以下目录之一： `/usr/local/nginx/conf`， `/etc/nginx`，或 `/usr/local/etc/nginx`. 请参阅 [初学者指南](http://nginx.org/en/docs/beginners_guide.html) 有关配置Nginx的详细信息。

示例Nginx配置：

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

### 安装和配置Open Swool

若要在本地运行应用程序服务器，请安装Open Swoole v22扩展。 有多种方法可以安装此扩展。

## 运行应用程序服务器

启动应用程序服务器：

```bash
bin/magento server:run
```

此命令在9501上启动HTTP端口。 应用程序服务器启动后，端口9501就会成为所有GraphQL查询的HTTP代理服务器。

## 示例：安装Open Swool (OSX)

此过程说明如何在基于OSX的系统的PHP 8.2上安装Open Swoole扩展。 这是安装Open Swoole扩展的多个方法之一。

您可以通过一个命令同时安装PHP (v22)的Open Swoole扩展和此扩展所需的Composer包。

### 安装Open Swool

输入：

```bash
pecl install openswoole-22.0.0 | composer require openswoole/core:22.1.1
```

在安装期间，Adobe Commerce显示提示以启用对 `openssl`， `mysqlnd`， `sockets`， `http2`、和 `postgres`. 输入 `yes` 适用于所有选项，但 `postgres`.

### 确认安装Open Swool

运行 `php -m | grep openswoole` 以确认已成功启用该扩展。

### Open Swool安装的常见错误

在Open Swool安装过程中发生的任何错误通常发生在 `pecl` 安装阶段。 典型错误包括缺失 `openssl.h` 和 `pcre2.h` 文件。 要解决这些错误，请确保在本地系统中安装了这两个软件包。

* 检查位置 `openssl` 通过运行：

```bash
openssl version -d
```

此命令显示以下位置的路径： `openssl` 已安装。

* 检查位置 `pcre2` 通过运行：

```bash
pcre2-config --prefix 
```

如果命令输出指示缺少文件，请使用Homebrew安装缺少的包：

```bash
brew install openssl
```

```bash
brew install pcre2
```

#### 解决openssl的问题

解决与相关的问题 `openssl`，运行：

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

确认您使用的是本地的路径 `dev` 环境。

#### 确认解决与openssl相关的问题

您可以再次运行以下命令以检查是否已解决与openssl相关的问题：

```bash
pecl install openswoole-22.0.0
```

#### 解决pcre2.h中的问题

解决与相关的问题 `pcre2.h`，符号链接 `pcre2.h` 已安装PHP扩展目录的路径。 您安装的特定版本的PHP和 `pcr2.h` 确定应使用的命令的特定版本。
