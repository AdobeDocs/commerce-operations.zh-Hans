---
title: 安装指南
description: 使用此指南为您的网站安装 [!DNL Site-Wide Analysis Tool]
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
feature: Configuration, Install
source-git-commit: f72316b3baee52ef6b000afa281a2e146f560ead
workflow-type: tm+mt
source-wordcount: '1136'
ht-degree: 0%

---

# 安装指南

>[!IMPORTANT]
>
>自2024年4月23日起，所有Adobe Commerce本地客户都将停用[!DNL Site-Wide Analysis Tool]。

[!DNL Site-Wide Analysis Tool]提供全天候的实时性能监控、报告和建议，以确保Adobe Commerce在云基础架构安装上的安全性和可操作性。 它还提供有关可用和已安装的修补程序、第三方扩展以及Adobe Commerce安装的详细信息。

>[!INFO]
>
>了解[如何启用](../site-wide-analysis-tool/access.md) [!DNL Site-Wide Analysis Tool]并生成报告。

如果您内部安装了Adobe Commerce，请在您的基础架构上安装代理以使用该工具。 您不需要在云基础架构项目上的Adobe Commerce上安装代理。

## 代理

[!DNL Site-Wide Analysis Tool]代理允许您将[!DNL Site-Wide Analysis Tool]用于Adobe Commerce的内部安装。

[!DNL Site-Wide Analysis Tool]代理收集应用程序和业务数据，对其进行分析并提供有关安装运行状况的更多见解，以便您改善客户体验。 它可以监视您的应用程序，并帮助您识别性能、安全性、可用性和应用程序问题。

安装代理程序需要以下步骤：

1. 验证系统要求。

1. 在[!UICONTROL Commerce Services Connector]扩展中配置API密钥。

1. 安装代理。

1. 运行代理。

>[!INFO]
>
>代理支持多节点Adobe Commerce安装。 在每个节点上安装和配置代理。

## 系统要求

安装代理之前，您的内部部署基础架构必须满足以下要求：

- 操作系统

   - [!DNL Linux x86-64]分配，如[!DNL Red Hat® Enterprise Linux (RHEL)]、[!DNL CentOS]、[!DNL Ubuntu]、[!DNL Debian]等

  >[!IMPORTANT]
  >
  >[!DNL Microsoft Windows]或[!DNL macOS]不支持Adobe Commerce。

- Adobe Commerce 2.4.5-p1或更高版本（由于依赖于Service Connector）

- [!DNL Commerce Services Connector extension]

- PHP CLI

- Bash/shell实用程序

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

代理需要在您的系统上安装[[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html)扩展和[已使用API密钥配置](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html)。 要验证是否已安装扩展，请运行以下命令：

```bash
bin/magento module:status Magento_ServicesId
```

如果您已安装扩展并使用其他服务的现有API密钥对其进行配置，则&#x200B;**必须重新生成API密钥**&#x200B;并在代理的Adobe Commerce管理员中对其进行更新。

1. 将您的网站置于[维护模式](../../installation/tutorials/maintenance-mode.md)。

1. 登录[account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671)。

   >[!NOTE]
   >
   > 如果访问帐户时遇到问题，请参阅[无法登录Adobe Commerce支持或云帐户](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html)以获取疑难解答帮助。

1. 单击&#x200B;**[!UICONTROL API Portal]**。

1. 单击现有API密钥旁边的&#x200B;**[!UICONTROL Delete]**。

1. [配置](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html)新的API密钥。

>[!IMPORTANT]
>
> 如果您在API门户中生成新密钥，请立即更新[!DNL Admin configuration]中的API密钥。 如果您生成新密钥但未更新[!DNL Admin]中的密钥，则SaaS扩展将不再有效，并且您将丢失有价值的数据。

如果未安装该扩展，请按照以下说明进行安装：

1. 将扩展添加到`composer.json`文件并进行安装。

   ```bash
   composer require magento/services-id
   ```

1. 启用该扩展。

   ```bash
   bin/magento module:enable Magento_ServicesId
   ```

1. 更新数据库架构。

   ```bash
   bin/magento setup:upgrade
   ```

1. 清除缓存。

   ```bash
   bin/magento cache:clean
   ```

1. [配置API密钥](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html)以将扩展连接到您的系统。

## 安装代理

我们已创建了[shell脚本](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh)以简化安装。 我们建议使用shell脚本，但您可以根据需要遵循[手动安装](#manual)方法。

>[!INFO]
>
>安装代理后，当有新版本可用时，它会自行更新。

### 脚本

1. 下载并执行shell脚本。

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >我们建议在根Adobe Commerce项目目录之外安装代理。

1. 验证安装。

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. 下载并安装代理后，[使用以下方法之一将其配置为运行](#run-the-agent)：

   - [服务](#service)（如果您具有根访问权限，则为首选服务）

   - [Cron](#cron)

### 手动 {#manual}

如果您不想使用我们的[shell脚本](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh)来安装代理，则必须按照以下步骤手动安装：

1. 创建要下载代理的目录。

   >[!TIP]
   >
   >我们建议在根Adobe Commerce项目目录之外安装代理。

1. 下载二进制文件并将其解包。

   >[!INFO]
   >
   >要使用[!DNL Site-Wide Analysis Tool]，您必须首先阅读并接受在从Adobe Commerce管理员访问仪表板时显示的使用条款。

   对于&#x200B;**AMD64**&#x200B;体系结构：

   1. 下载启动器档案。

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. 解压缩启动器档案。

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   对于&#x200B;**ARM64**&#x200B;架构：

   1. 下载启动器档案。

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. 解压缩启动器档案。

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```

1. *（可选）*&#x200B;验证校验和文件的签名。

   ```bash
   echo -n "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQ0lqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FnOEFNSUlDQ2dLQ0FnRUE0M2FBTk1WRXR3eEZBdTd4TE91dQpacG5FTk9pV3Y2aXpLS29HendGRitMTzZXNEpOR3lRS1Jha0MxTXRsU283VnFPWnhUbHZSSFhQZWt6TG5vSHVHCmdmNEZKa3RPUEE2S3d6cjF4WFZ3RVg4MEFYU1JNYTFadzdyOThhenh0ZHdURVh3bU9GUXdDcjYramFOM3ErbUoKbkRlUWYzMThsclk0NVJxWHV1R294QzBhbWVoakRnTGxJUSs1d1kxR1NtRGRiaDFJOWZqMENVNkNzaFpsOXFtdgorelhjWGh4dlhmTUU4MUZsVUN1elRydHJFb1Bsc3dtVHN3ODNVY1lGNTFUak8zWWVlRno3RFRhRUhMUVVhUlBKClJtVzdxWE9kTGdRdGxIV0t3V2ppMFlrM0d0Ylc3NVBMQ2pGdEQzNytkVDFpTEtzYjFyR0VUYm42V3I0Nno4Z24KY1Q4cVFhS3pYRThoWjJPSDhSWjN1aFVpRHhZQUszdmdsYXJSdUFacmVYMVE2ZHdwYW9ZcERKa29XOXNjNXlkWApBTkJsYnBjVXhiYkpaWThLS0lRSURnTFdOckw3SVNxK2FnYlRXektFZEl0Ni9EZm1YUnJlUmlMbDlQMldvOFRyCnFxaHNHRlZoRHZlMFN6MjYyOU55amgwelloSmRUWXRpdldxbGl6VTdWbXBob1NrVnNqTGtwQXBiUUNtVm9vNkgKakJmdU1sY1JPeWI4TXJCMXZTNDJRU1MrNktkMytwR3JyVnh0akNWaWwyekhSSTRMRGwrVzUwR1B6LzFkeEw2TgprZktZWjVhNUdCZm00aUNlaWVNa3lBT2lKTkxNa1cvcTdwM200ejdUQjJnbWtldm1aU3Z5MnVMNGJLYlRoYXRlCm9sdlpFd253WWRxaktkcVkrOVM1UlNVQ0F3RUFBUT09Ci0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQ==" | base64 -d > release.pub
   ```

   ```bash
   openssl dgst -sha256 -verify release.pub -signature launcher.sha256 launcher.checksum
   ```

1. *（可选）*&#x200B;验证校验和。

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. 创建包含以下内容的`config.yaml`文件。

   ```yaml
   project:
     appname: "Acme Inc" # Company or site name that you provided when installing the agent
   application:
     phppath: php # Path to your PHP CLI interpreter (usually /usr/bin/php)
     magentopath: /var/www/html/example.com # Root directory where your Adobe Commerce application is installed (usually /var/www/html)
     checkregistrypath: /path/to/swat-agent/tmp # Temporary directory for the agent (usually /usr/local/swat-agent/tmp)
     issandbox: false # Enabling sandbox mode to use the agent on staging environment (true or false)
     database:
       user: your-adobe-commerce-db-username # Database user for your Adobe Commerce installation
       password: your-password # Database password for the specified user for your Adobe Commerce installation
       host: 127.0.0.1 # Database host for your Adobe Commerce installation
       dbname: your-adobe-commerce-db-name # Database name for your Adobe Commerce installation
       port: 3306 # Database port for your Adobe Commerce installation (usually 3306)
       tableprefix: # Table Prefix for your Adobe Commerce installation (default value: empty)
    enableautoupgrade: true # Enables automatic upgrade (restart required after an upgrade; agent does not check for upgrades if the option is disabled; true or false)
    runchecksonstart: true # Collect data on the first run (Usually 1)
    loglevel: error # Determines what events are logged based on severity (usually error)
   ```

1. 验证安装。

   ```bash
   scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. 下载并安装代理后，必须[将其配置为使用以下方法之一运行](#run-the-agent)：

   - [服务](#service)（如果您具有根访问权限，则为首选服务）

   - [Cron](#cron)

## 运行代理 {#run-the-agent}

我们建议将代理配置为作为服务运行。 如果您对基础结构的访问权限有限，并且没有root权限，则必须改用[cron](#cron)。

### 服务 {#service}

1. 使用以下配置创建系统单元文件`(/etc/systemd/system/scheduler.service)`(将`<filesystemowner>`替换为拥有代理和Adobe Commerce软件安装目录的UNIX®用户)。 如果以root用户身份下载代理，请更改目录和嵌套文件所有者。

   ```config
   [Unit]
   Wants=network.target
   After=network.target
   
   [Service]
   Type=simple
   User=<filesystemowner>
   ExecStart=/path/to/agent/scheduler
   Restart=always
   RestartSec=3
   
   [Install]
   WantedBy=multi-user.target
   ```

1. 启动服务。

   ```bash
   systemctl daemon-reload
   ```

   ```bash
   systemctl start scheduler
   ```

   ```bash
   systemctl enable scheduler
   ```

1. 验证服务是否已启动并正在运行。

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### Cron {#cron}

如果您没有root权限或没有将服务配置为root的权限，则可以改用cron。

更新cron计划：

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## 卸载

运行以下命令从系统中卸载服务并删除所有生成的文件：

1. 停止计划程序。

   ```bash
   systemctl stop scheduler
   ```

1. 禁用计划程序。

   ```bash
   systemctl disable scheduler
   ```

1. 删除计划程序服务的`systemd`单元文件。

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. 重新加载`systemd`管理器配置。

   ```bash
   systemctl daemon-reload
   ```

1. 从失败状态重置任何`systemd`设备。

   ```bash
   systemctl reset-failed
   ```

1. 删除计划程序服务目录。

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. 删除计划程序二进制文件。

   ```bash
   rm /usr/local/bin/scheduler
   ```

如果您将代理配置为使用cron运行，请使用以下说明：

1. 从crontab列表中删除代理。

   ```bash
   crontab -e
   ```

1. 停止正在运行的作业。

   ```bash
   ps aux | grep scheduler
   ```

1. 删除安装代理的目录。

   ```bash
   rm -rf swat-agent
   ```

## 故障排除

### 访问密钥未正确解析

如果未正确解析访问密钥，您可能会看到以下错误：

```terminal
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

要解决此错误，请尝试执行以下步骤：

1. 执行[脚本安装](#scripted)，保存输出并查看输出是否有错误。
1. 查看生成的`config.yaml`文件，并验证指向Commerce实例和PHP的路径是否正确。
1. 确保运行计划程序的用户位于[文件系统所有者](../../installation/prerequisites/file-system/overview.md) Unix组中，或者与文件系统所有者是同一个用户。
1. 确保已正确安装[Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html)密钥，并尝试更新这些密钥以将扩展连接到您的系统。
1. [在更新密钥后卸载](#uninstall)代理并使用[安装脚本](#scripted)重新安装。
1. 运行调度程序并查看您是否仍收到相同的错误。
1. 如果您仍收到相同的错误，请增加`config.yaml`中的日志级别以调试并打开支持票证。

### *SIGFAULT*&#x200B;错误

如果在运行二进制文件时看到&#x200B;*SIGFAULT*错误，则您可能不会以Adobe Commerce和代理文件的文件所有者身份运行此文件。
要解决此问题，请检查代理目录中的所有文件(这些文件的用户与Adobe Commerce文件拥有的文件所有者相同)是否也应该在该用户下运行二进制文件。
您可以使用`chown`命令更改文件所有者并切换到适当的用户。
确保您的守护程序机制（Cron或System.d）在适当的用户下运行该过程。

>[!INFO]
>
>请参阅[如何访问 [!DNL Site-Wide Analysis Tool] 和生成报告](../site-wide-analysis-tool/access.md)。
