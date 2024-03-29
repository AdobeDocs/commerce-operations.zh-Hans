---
title: 适用于GraphQL API的应用程序服务器
description: 按照以下说明在Adobe Commerce部署中为GraphQL API启用应用程序服务器。
badgeCoreBeta: label="2.4.7（测试版）" type="informative"
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: 9d5795400880a65947b1b90c8806b9dcb14aba23
workflow-type: tm+mt
source-wordcount: '1897'
ht-degree: 0%

---

# 适用于GraphQL API的应用程序服务器

Commerce Application Server for GraphQL API使Adobe Commerce能够维护Commerce GraphQL API请求中的状态。 应用程序服务器基于Swoole扩展构建，它作为进程运行，通过工作线程处理请求。 Application Server通过在GraphQL API请求中保留引导的应用程序状态，增强了请求处理和总体产品性能。 API请求变得非常高效。

仅云基础架构Starter和Pro项目上的Adobe Commerce支持应用程序服务器。 它不适用于Magento Open Source项目。 Adobe不提供对Application Server的内部部署的支持。

## 应用程序服务器体系结构概述

应用程序服务器维护Commerce GraphQL API请求之间的状态，并且无需引导。 通过跨进程共享应用程序状态，GraphQL请求可以显着提升效率，将响应时间最多减少30%。

无共享PHP执行模型从延迟的角度提供了一个挑战，因为每个请求都需要框架的引导。 此引导过程包括一些耗时的任务，如读取配置、设置引导过程和创建服务类对象。

将请求处理逻辑转换为应用程序级事件循环似乎解决了在企业级简化请求处理的难题。 此方法消除了在请求执行生命周期期间进行引导的需要。

## 使用应用程序服务器的好处

应用程序服务器允许Adobe Commerce在连续的Commerce GraphQL API请求之间保持状态。 跨请求共享应用程序状态通过最大限度地减少处理开销和优化请求处理而增强了API请求效率。 因此，GraphQL请求响应时间最多可以减少30%。

## 系统要求

运行应用程序服务器需要满足以下条件：

* PHP 8.2或更高版本
* 已安装Swoole PHP扩展v5+
* 根据预期负载提供足够的RAM和CPU

## 启用应用程序服务器

此 `ApplicationServer` 模块(`Magento/ApplicationServer/`)为GraphQL API启用应用程序服务器。 本地和云部署支持应用程序服务器。

## 在Cloud Pro上启用应用程序服务器

在Cloud Pro上部署应用程序服务器之前，请完成以下任务：

1. 确认已使用Adobe Commerce模板版本2.4.7或更高版本在Commerce Cloud上安装Cloud Template。
1. 确保您的所有Commerce自定义项和扩展均 [兼容](https://developer.adobe.com/commerce/php/development/components/app-server/) 与应用程序服务器。
1. 克隆Commerce Cloud项目。
1. 如有必要，调整“application-server/nginx.conf.sample”文件中的设置。
1. 注释掉中的活动“Web”部分 `project_root/.magento.app.yaml` 个文件。
1. 取消注释中的以下“web”部分配置 `project_root/.magento.app.yaml` 包含应用程序服务器启动命令的文件。

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. 使用以下命令将更新的文件添加到Git索引：

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. 使用以下命令提交更改：

   ```bash
   git commit -m "AppServer Enabled"
   ```

### 在Cloud Pro上部署应用程序服务器

执行先决任务后，使用以下命令部署应用程序服务器：

```bash
git push
```

### 在开始Cloud Starter部署之前

在Cloud Starter上部署应用程序服务器之前，请完成以下任务：

1. 确认已使用Adobe Commerce模板版本2.4.7或更高版本在Commerce Cloud上安装Cloud Template。
1. 确保您的所有Commerce自定义项和扩展都与应用程序服务器兼容。
1. 确认 `CRYPT_KEY` 已为实例设置了环境变量。 您可以在云项目门户（载入UI）上检查此变量的状态。
1. 克隆Commerce Cloud项目。
1. 重命名 `application-server/.magento/.magento.app.yaml.sample` 到 `application-server/.magento/.magento.app.yaml` 并根据需要调整.magento.app.yaml中的设置。
1. 取消注释以下路由在 `project_root/.magento/routes.yaml` 要重定向的文件 `/graphql` 应用程序服务器的通信量。

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. 使用以下命令将更新的文件添加到Git索引：

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. 使用以下命令提交更改：

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
> 确保您在根目录中的所有自定义设置 `.magento.app.yaml` 文件已相应地迁移到 `application-server/.magento/.magento.app.yaml` 文件。 一旦 `application-server/.magento/.magento.app.yaml` 文件添加到项目中，除了根以外，您应该维护它 `.magento.app.yaml` 文件。
> 例如，如果您需要 [配置rabbitmq](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) 或 [管理Web资产](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property) 您应该将相同的配置添加到 `application-server/.magento/.magento.app.yaml` 也一样。

### 在云启动器上部署应用程序服务器

完成 [先决条件](#before-you-begin-a-cloud-starter-deployment)，使用以下命令部署应用程序服务器：

```bash
git push
```

### 验证云启动程序上的应用程序服务器是否启用

1. 对实例执行GraphQL查询或突变，以确认 `graphql` 端点可访问。 例如：

   ```
   mutation {  
    createEmptyCart
   }
   ```

   预期的响应应与以下示例类似：

   ```terminal
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. 使用SSH访问您的云实例。 此 `project_root/var/log/application-server.log` 应该包含每个GraphQL请求的新日志记录。

1. 还可以通过执行以下命令来检查应用程序服务器是否正在运行：

   ```bash
   ps aux|grep php
   ```

   您应该会看到 `bin/magento server:run` 使用多个线程的进程。

如果这些验证步骤成功，则表示应用程序服务器正在运行并提供服务 `/graphql` 请求。


## 启用应用程序服务器内部部署

此 `ApplicationServer` 模块(`Magento/ApplicationServer/`)为GraphQL API启用应用程序服务器。

在本地运行应用程序服务器需要安装Swoole扩展并对部署的NGINX配置文件进行细微更改。

### 在开始内部部署之前

在启用 `ApplicationServer` 模块：

* 配置Nginx

* 安装和配置Swoole v5+扩展

### 配置Nginx

您的特定Commerce部署决定了如何配置Nginx。 通常，Nginx配置文件默认名为 `nginx.conf` 和位于以下目录之一： `/usr/local/nginx/conf`， `/etc/nginx`，或 `/usr/local/etc/nginx`. 请参阅 [初学者指南](https://nginx.org/en/docs/beginners_guide.html) 有关配置Nginx的详细信息。

示例Nginx配置：

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

### 安装和配置Swool

要在本地运行应用程序服务器，请安装Swoole扩展（v5.0或更高版本）。 有多种方法可以安装此扩展。

## 运行应用程序服务器

启动应用程序服务器：

```bash
bin/magento server:run
```

此命令在9501上启动HTTP端口。 应用程序服务器启动后，端口9501就会成为所有GraphQL查询的HTTP代理服务器。

## 示例：安装Swoole (OSX)

此过程说明如何在基于OSX的系统的PHP 8.2上安装Swoole扩展。 这是安装Swoole扩展的多个方法之一。

### 安装Swool

输入：

```bash
pecl install swoole
```

在安装期间，Adobe Commerce显示提示以启用对 `openssl`， `mysqlnd`， `sockets`， `http2`、和 `postgres`. 输入 `yes` 适用于所有选项，但 `postgres`.

### 确认Swoole的安装

运行 `php -m | grep swoole` 以确认已成功启用该扩展。

### Swoole安装的常见错误

在Swoole安装过程中发生的任何错误通常发生在 `pecl` 安装阶段。 典型错误包括缺失 `openssl.h` 和 `pcre2.h` 文件。 要解决这些错误，请确保在本地系统中安装了这两个软件包。

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
pecl install swoole
```

#### 解决pcre2.h中的问题

解决与相关的问题 `pcre2.h`，符号链接 `pcre2.h` 已安装PHP扩展目录的路径。 您安装的特定版本的PHP和 `pcr2.h` 确定应使用的命令的特定版本。

### 确认应用程序服务器正在运行

要确认您的部署中正在运行应用程序服务器，请执行以下命令：

```bash
ps aux | grep php
```

确认应用程序服务器正在运行的其他方法包括：

* 查看 `/var/log/application-server.log` 与已处理的GraphQL请求相关的条目的文件。
* 尝试连接到Application Server所运行的HTTP端口。 例如： `curl -g 'http://localhost:9501/graph`.

### 确认应用程序服务器正在处理GraphQL请求

应用程序服务器添加 `X-Backend` 具有值的响应标头 `graphql_server` 处理的所有请求。 要检查某个请求是否已由应用程序服务器处理，请检查此响应标头。

### 确认扩展和自定义与应用程序服务器的兼容性

扩展开发人员和商家应该首先验证其扩展和自定义代码是否遵守中描述的技术准则。 [技术准则](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

在代码评估过程中请考虑以下准则：

* 服务类(即提供行为但不提供数据的类，例如 `EventManager`)不应具有可变状态。
* 避免时间耦合。

## 禁用应用程序服务器

禁用应用程序服务器的过程因服务器是在内部部署还是云部署中运行而异。

### 在云启动器上禁用应用程序服务器

1. 删除中包括的所有新文件和任何其他代码更改 `AppServer Enabled` 在准备部署期间提交。

1. 使用以下命令提交更改：

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. 使用此命令部署这些更改：

   ```bash
   git push
   ```

### 禁用应用程序服务器

1. 注释掉 `/graphql` 部分 `nginx.conf` 启用应用程序服务器时添加的文件。
1. 重新启动nginx。

这种禁用应用程序服务器的方法对于快速测试或比较性能很有用。

### 确认应用程序服务器已禁用

确认GraphQL请求正在由处理 `php-fpm` 输入以下命令，而不是Application Server： `ps aux | grep php`.

禁用应用程序服务器后：

* `bin/magento server:run` 处于不活动状态。
* `var/log/application-server.log` 在GraphQL请求之后不包含条目。

## PHP应用程序服务器的集成和功能测试

扩展开发人员可以运行两个集成测试，以验证与应用程序服务器的扩展兼容性： `GraphQlStateTest` 和 `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` 检测不应为多个请求重用的共享对象中的状态。

此测试旨在检测由生成的服务对象的状态变化。 `ObjectManager`. 该测试执行两次相同的GraphQL查询，并比较第二次查询之前和之后的服务对象状态。

#### GraphQlStateTest失败和可能的修复

* **无法添加、跳过或筛选列表**. 如果遇到错误，表明添加、跳过或过滤列表是不安全的，请考虑是否能够以向后兼容的方式重构类，以使用具有可变状态的服务类的工厂。

* **类呈现可变状态**. 如果类本身表现出可变状态，请尝试重写您的代码以规避此状态。 如果出于性能原因需要可变状态，则实施 `ResetAfterRequestInterface` 和使用 `_resetState()` 将对象重置为其初始构造状态。

* **在初始化消息之前不能访问键入的属性$x**. 此类型的消息失败表明指定的属性尚未被构造函数初始化。 这是一种时间耦合的形式，发生这种耦合的原因是，对象在初始构建后无法使用。 即使属性是私有的，也会发生这种耦合，因为从属性中检索数据的收集器正在使用PHP反射特征。 在这种情况下，尝试重构类以避免时间耦合和避免可变状态。 如果该重构不能解决故障，您可以将属性类型更改为可空类型，以便将其初始化为null。  如果属性是一个数组，请尝试将该属性初始化为空数组。

运行 `GraphQlStateTest` 通过执行 `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

`ResetAfterRequestTest` 查找所有实现的类 `ResetAfterRequestInterface` 并验证 `_resetState()` 方法将对象的状态返回到由构造后保持的状态 `ObjectManager`.  此测试创建服务对象，其中 `ObjectManager`，然后克隆该对象，调用 `_resetState()`，然后比较两个对象。 该测试不会在对象实例化和之间调用任何方法 `_resetState()`，因此它不会确认重置任何可变状态。 它确实会发现以下问题：出现错误或打字错误 `_resetState()` 可能会将政府设定为与最初不同的状态。

#### ResetAfterRequestTest失败和可能的修正

* **类的属性值不一致**. 如果此测试失败，请检查类是否已更改，结果是在构造后的对象具有与构造后的对象不同的属性值 `_resetState()` 方法被调用。 如果您正在处理的类不包含 `_resetState()` 方法本身，然后检查实现它的超类的类层次结构。

* **在初始化消息之前不能访问键入的属性$x**. 此问题也会出现在 `GraphQlStateTest`.

  运行 `ResetAfterRequestTest` 通过执行： `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### 功能测试

扩展开发人员在部署应用程序服务器时，应该执行GraphQL的WebAPI功能测试，以及GraphQL的任何自定义自动或手动功能测试。 这些功能测试可帮助开发人员识别潜在的错误或兼容性问题。
