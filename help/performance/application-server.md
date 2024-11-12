---
title: GraphQL应用程序服务器
description: 按照以下说明在Adobe Commerce部署中启用GraphQL应用程序服务器。
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: c5446f0273705b158297c0a253054742ec95b44e
workflow-type: tm+mt
source-wordcount: '2082'
ht-degree: 0%

---


# GraphQL应用程序服务器

Commerce GraphQL Application Server使Adobe Commerce能够维护Commerce GraphQL API请求中的状态。 GraphQL Application Server基于Swoole扩展构建，作为具有工作线程的进程运行，这些工作线程处理请求。 GraphQL Application Server通过在GraphQL API请求中保留引导的应用程序状态，来增强请求处理和整体产品性能。 API请求变得非常高效。

GraphQL Application Server仅适用于Adobe Commerce。 它不适用于Magento Open Source。 对于Cloud Pro项目，您必须[提交Adobe Commerce支持](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)票证以启用GraphQL应用程序服务器。

>[!NOTE]
>
>GraphQL Application Server当前与[[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/)不兼容。 在Adobe于2024年晚些时候发布修补程序之前，当前在[远程存储](../configuration/remote-storage/cloud-support.md)上使用[!DNL AWS S3]的Adobe Commerce基础架构客户无法使用GraphQL Application Server。

## 架构

GraphQL Application Server可维护Commerce GraphQL API请求之间的状态，并且无需引导。 通过跨进程共享应用程序状态，GraphQL请求可以显着提升效率，将响应时间最多减少30%。

无共享PHP执行模型从延迟的角度提供了一个挑战，因为每个请求都需要框架的引导。 此引导过程包括一些耗时的任务，如读取配置、设置引导过程和创建服务类对象。

将请求处理逻辑转换为应用程序级事件循环似乎解决了在企业级简化请求处理的难题。 此方法消除了在请求执行生命周期期间进行引导的需要。

## 优点

GraphQL Application Server允许Adobe Commerce在连续的Commerce GraphQL API请求之间保持状态。 跨请求共享应用程序状态通过最大限度地减少处理开销和优化请求处理而增强了API请求效率。 因此，GraphQL请求响应时间最多可缩短30%。

## 系统要求

运行GraphQL Application Server需要满足以下条件：

* Commerce版本2.4.7+
* PHP 8.2或更高版本
* 已安装Swoole PHP扩展v5+
* 根据预期负载提供足够的RAM和CPU

## 在云基础架构上启用和部署

`ApplicationServer`模块(`Magento/ApplicationServer/`)启用GraphQL应用程序服务器。

### 启用Pro项目

>[!NOTE]
>
>应用程序服务器是Cloud Pro实例上的选择加入功能。 要启用该功能，请提交支持请求。

在Pro项目上启用应用程序服务器功能后，请先完成以下步骤，然后再部署GraphQL Application Server：

1. 使用[2.4.7-appserver分支](https://github.com/magento/magento-cloud/tree/2.4.7-appserver)中的云模板在云基础架构上部署Adobe Commerce。
1. 确保您的所有Commerce自定义项和扩展都与GraphQL Application Server [兼容](https://developer.adobe.com/commerce/php/development/components/app-server/)。
1. 克隆Commerce Cloud项目。
1. 如有必要，调整“application-server/nginx.conf.sample”文件中的设置。
1. 完全注释掉`project_root/.magento.app.yaml`文件中的活动“web”部分。
1. 在包含GraphQL应用程序服务器`start`命令的`project_root/.magento.app.yaml`文件中取消注释以下“Web”节配置。

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. 通过运行以下命令确保`/application-server/start.sh`可执行：

   ```bash
   chmod +x application-server/start.sh
   ```

1. 使用以下命令将更新的文件添加到Git索引：

   ```bash
   git add -f .magento.app.yaml application-server/*
   ```

1. 使用以下命令提交更改：

   ```bash
   git commit -m "AppServer Enabled"
   ```

### 部署Pro项目

完成启用步骤后，将更改推送到Git存储库以部署GraphQL Application Server：

```bash
git push
```

### 启用入门项目

在启动项目上部署GraphQL Application Server之前，请完成以下步骤：

1. 使用[2.4.7-appserver分支](https://github.com/magento/magento-cloud/tree/2.4.7-appserver)中的云模板在云基础架构上部署Adobe Commerce。
1. 确保您的所有Commerce自定义项和扩展都与GraphQL Application Server兼容。
1. 确认已为您的实例设置了`CRYPT_KEY`环境变量。 您可以在Cloud Console上检查此变量的状态。
1. 克隆Commerce Cloud项目。
1. 将`application-server/.magento/.magento.app.yaml.sample`重命名为`application-server/.magento/.magento.app.yaml`，并根据需要调整.magento.app.yaml中的设置。
1. 在`project_root/.magento/routes.yaml`文件中取消注释以下路由的配置，将`/graphql`流量重定向到GraphQL Application Server。

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. 将更新的文件添加到Git索引：

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. 提交更改：

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
>确保将根`.magento.app.yaml`文件中的所有自定义设置正确迁移到`application-server/.magento/.magento.app.yaml`文件中。 将`application-server/.magento/.magento.app.yaml`文件添加到您的项目后，除了根`.magento.app.yaml`文件之外，您还应维护它。 例如，如果您需要[配置RabbitMQ服务](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq)或[管理Web属性](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property)，则还应该将相同的配置添加到`application-server/.magento/.magento.app.yaml`。

### 部署入门项目

完成启用[步骤](#before-you-begin-a-cloud-starter-deployment)后，将更改推送到您的Git存储库以部署GraphQL Application Server：

```bash
git push
```

### 验证云项目上的启用情况

1. 对实例执行GraphQL查询或突变，以确认`graphql`端点可访问。 例如：

   ```
   mutation {  
    createEmptyCart
   }
   ```

   预期的响应应与以下示例类似：

   ```json
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. 使用SSH访问您的云实例。 `project_root/var/log/application-server.log`应包含每个GraphQL请求的新日志记录。

1. 您还可以通过执行以下命令来检查GraphQL应用程序服务器是否正在运行：

   ```bash
   ps aux|grep php
   ```

   您应该会看到一个具有多个线程的`bin/magento server:run`进程。

如果这些验证步骤成功，则GraphQL Application Server正在运行并提供`/graphql`请求。

## 启用内部部署项目

`ApplicationServer`模块(`Magento/ApplicationServer/`)为GraphQL API启用GraphQL Application Server。

在本地运行GraphQL Application Server需要安装Swoole扩展，并对部署的Nginx配置文件进行细微更改。

### 先决条件

在启用`ApplicationServer`模块之前，请完成以下步骤：

* 配置Nginx
* 安装和配置Swoole v5+扩展

#### 配置Nginx

您的特定Commerce部署决定了如何配置Nginx。 通常，Nginx配置文件默认名为`nginx.conf`，并位于以下目录之一： `/usr/local/nginx/conf`、`/etc/nginx`或`/usr/local/etc/nginx`。 有关配置Nginx的更多信息，请参阅&#x200B;_[初学者指南](https://nginx.org/en/docs/beginners_guide.html)_。

示例Nginx配置：

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

#### 安装和配置Swool

要在本地运行GraphQL Application Server，请安装Swoole扩展（v5.0或更高版本）。 有多种方法可以安装此扩展。

以下过程介绍如何在基于OSX的系统上安装PHP 8.2的Swoole扩展。 这是安装Swoole扩展的多个方法之一。

```bash
pecl install swoole
```

在安装期间，Adobe Commerce显示提示以启用对`openssl`、`mysqlnd`、`sockets`、`http2`和`postgres`的支持。 为除`postgres`之外的所有选项输入`yes`。

### 验证Swool安装

确认已成功启用该扩展：

```bash
php -m | grep swoole
```

### Swoole安装的常见错误

在Swoole安装过程中发生的任何错误通常发生在`pecl`安装阶段。 典型错误包括缺少`openssl.h`和`pcre2.h`文件。 要解决这些错误，请确保在本地系统中安装了这两个软件包。

* 通过运行以下命令检查`openssl`的位置：

```bash
openssl version -d
```

此命令显示安装`openssl`的路径。

* 通过运行以下命令检查`pcre2`的位置：

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

若要解决与`openssl`相关的问题，请运行：

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

确认您使用的是本地`dev`环境中的路径。

#### 确认解决与openssl相关的问题

您可以再次运行以下命令以检查是否已解决与openssl相关的问题：

```bash
pecl install swoole
```

#### 解决pcre2.h中的问题

要解决与`pcre2.h`相关的问题，请将`pcre2.h`路径符号链接到已安装的PHP扩展目录。 您安装的PHP和`pcr2.h`的特定版本决定了应使用的命令的特定版本。

### 运行GraphQL应用程序服务器

启动GraphQL Application Server：

```bash
bin/magento server:run
```

此命令在9501上启动HTTP端口。 GraphQL应用程序服务器启动后，端口9501就会成为所有GraphQL查询的HTTP代理服务器。

要确认GraphQL应用程序服务器正在您的部署中运行，请执行以下操作：

```bash
ps aux | grep php
```

确认GraphQL Application Server正在运行的其他方法包括：

* 检查`/var/log/application-server.log`文件中与已处理GraphQL请求相关的条目。
* 尝试连接到GraphQL Application Server所运行的HTTP端口。 例如： `curl -g 'http://localhost:9501/graph`。

### 确认正在处理GraphQL请求

GraphQL Application Server将值为`graphql_server`的`X-Backend`响应标头添加到其处理的每个请求中。 要检查GraphQL Application Server是否已处理请求，请检查此响应标头。

### 确认扩展和自定义兼容性

扩展开发人员和商户应首先验证其扩展和自定义代码是否符合&#x200B;_[技术准则](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/)_&#x200B;中所述的准则。

在代码评估过程中请考虑以下准则：

* 服务类（即提供行为但不提供数据的类，如`EventManager`）不应具有可变状态。
* 避免时间耦合。

## 禁用GraphQL应用程序服务器

禁用GraphQL Application Server的过程因服务器是在内部部署还是云部署中运行而异。

### 禁用GraphQL应用程序服务器（云）

1. 在准备部署期间，删除`AppServer Enabled`提交中包含的所有新文件和任何其他代码更改。

1. 使用以下命令提交更改：

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. 使用此命令部署这些更改：

   ```bash
   git push
   ```

### 禁用GraphQL Application Server（本地）

1. 注释掉启用GraphQL Application Server时添加的`nginx.conf`文件的`/graphql`部分。
1. 重新启动nginx。

这种禁用GraphQL Application Server的方法对于快速测试或比较性能很有用。

### 确认已禁用GraphQL应用程序服务器

要确认`php-fpm`正在处理GraphQL请求而不是GraphQL应用程序服务器，请输入以下命令： `ps aux | grep php`。

禁用GraphQL应用程序服务器后：

* `bin/magento server:run`处于非活动状态。
* 在GraphQL请求之后，`var/log/application-server.log`不包含任何条目。

## GraphQL应用程序服务器的集成和功能测试

扩展开发人员可以运行两个集成测试来验证与GraphQL Application Server的扩展兼容性： `GraphQlStateTest`和`ResetAfterRequestTest`。

### GraphQlStateTest

`GraphQlStateTest`检测不应为多个请求重复使用的共享对象中的状态。

此测试旨在检测`ObjectManager`生成的服务对象中的状态更改。 该测试执行两次相同的GraphQL查询，并比较第二次查询之前和之后的服务对象状态。

#### GraphQlStateTest失败和可能的修复

* **无法添加、跳过或筛选列表**。 如果看到有关添加、跳过或过滤列表的错误，请考虑是否能够以向后兼容的方式重构类，以使用具有可变状态的服务类的工厂。

* **类呈现可变状态**。 如果类本身表现出可变状态，请尝试重写您的代码以规避此状态。 如果出于性能原因需要可变状态，则实现`ResetAfterRequestInterface`并使用`_resetState()`将对象重置为其初始构造状态。

* 在初始化消息&#x200B;**之前，不能访问**&#x200B;键入的属性$x。 此类型的消息失败表明指定的属性尚未被构造函数初始化。 这是一种时间耦合的形式，发生这种耦合的原因是，对象在初始构建后无法使用。 即使属性是私有的，也会发生这种耦合，因为从属性中检索数据的收集器正在使用PHP反射特征。 在这种情况下，尝试重构类以避免时间耦合和避免可变状态。 如果该重构不能解决故障，您可以将属性类型更改为可空类型，以便将其初始化为null。  如果属性是一个数组，请尝试将该属性初始化为空数组。

通过执行`vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`运行`GraphQlStateTest`。

### ResetAfterRequestTest

`ResetAfterRequestTest`将查找实现`ResetAfterRequestInterface`的所有类，并验证`_resetState()`方法是否将对象的状态返回到`ObjectManager`构造后它保持的状态。  此测试创建具有`ObjectManager`的服务对象，然后克隆该对象，调用`_resetState()`，然后比较两个对象。 该测试未在对象实例化和`_resetState()`之间调用任何方法，因此它不会确认重置任何可变状态。 它确实发现了`_resetState()`中的错误或拼写错误可能会将状态设置为与它原来的状态不同的问题。

#### ResetAfterRequestTest失败和可能的修正

* **类的属性值**&#x200B;不一致。 如果此测试失败，请检查类是否已更改，结果是在构造后的对象与调用`_resetState()`方法后的对象具有不同的属性值。 如果您正在处理的类不包含`_resetState()`方法本身，请检查实现它的超类的类层次结构。

* 在初始化消息&#x200B;**之前，不能访问**&#x200B;键入的属性$x。 `GraphQlStateTest`也存在此问题。

  通过执行`vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`运行`ResetAfterRequestTest`。

### 功能测试

在部署GraphQL Application Server时，扩展开发人员应该执行GraphQL的WebAPI功能测试和任何自定义的自动或手动功能测试。 这些功能测试可帮助开发人员识别潜在的错误或兼容性问题。

#### 状态监视器模式

在运行功能测试（或手动测试）时，GraphQL Application Server可以在启用`--state-monitor mode`的情况下运行，以帮助查找状态被无意重复使用的类。 正常启动应用程序服务器，但添加`--state-monitor`参数除外。

```
bin/magento server:run --state-monitor
```

在处理每个请求后，都会向`tmp`目录中添加一个新文件，例如： `var/tmp/StateMonitor-thread-output-50-6nmxiK`。 完成测试后，这些文件可以与`bin/magento server:state-monitor:aggregate-output`命令合并，这将创建两个合并的文件，一个在`XML`，一个在`JSON`。

示例：

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

可以使用用于查看XML或JSON的任何工具来检查这些文件，这些工具显示`GraphQlStateTest`等服务对象的修改属性。 `--state-monitor`模式使用与GraphQlStateTest相同的跳过列表和筛选器列表。

>[!NOTE]
>
>请勿在生产环境中使用`--state-monitor`模式。 它仅用于开发和测试。 它会创建许多输出文件，并且运行速度比正常速度慢。

>[!NOTE]
>
>由于PHP垃圾回收器中的错误，`--state-monitor`与PHP版本`8.3.0` - `8.3.4`不兼容。 如果您使用的是PHP 8.3，则必须升级到`8.3.5`或更高版本才能使用此功能。
