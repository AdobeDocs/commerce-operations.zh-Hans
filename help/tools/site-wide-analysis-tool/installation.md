---
title: 安装指南
description: 使用本指南安装 [!DNL Site-Wide Analysis Tool] （适用于您的网站）
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
source-git-commit: 4210746509be99bb3c943906c99f70ea420ba74a
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 0%

---

# 安装指南

此 [!DNL Site-Wide Analysis Tool] 提供全天候的实时性能监控、报告和建议，以确保Adobe Commerce在云基础架构安装中的安全性和可操作性。 它还提供有关可用和已安装的修补程序、第三方扩展以及Adobe Commerce安装的详细信息。

>[!INFO]
>
>了解 [如何启用](../site-wide-analysis-tool/access.md) 此 [!DNL Site-Wide Analysis Tool] 并生成报表。

如果您内部安装了Adobe Commerce，请在您的基础架构上安装代理以使用该工具。 您无需在云基础架构项目上在Adobe Commerce上安装代理。

## 代理

此 [!DNL Site-Wide Analysis Tool] Agent允许您使用 [!DNL Site-Wide Analysis Tool] 用于Adobe Commerce的内部安装。

此 [!DNL Site-Wide Analysis Tool] 代理会收集应用程序和业务数据，对其进行分析，并提供有关安装运行状况的其他见解，以便您改善客户体验。 它监视您的应用程序，并帮助您识别性能、安全性、可用性和应用程序问题。

安装代理程序需要以下步骤：

1. 验证系统要求。

1. 在中配置API密钥 [!UICONTROL Commerce Services Connector] 扩展。

1. 安装代理。

1. 运行代理。

>[!INFO]
>
>代理支持多节点Adobe Commerce安装。 在每个节点上安装和配置代理。

## 系统要求

安装代理之前，您的内部部署基础架构必须满足以下要求：

- 操作系统

   - [!DNL Linux x86-64] 分发，例如 [!DNL Red Hat® Enterprise Linux (RHEL)]， [!DNL CentOS]， [!DNL Ubuntu]， [!DNL Debian]，和类似项
   >[!IMPORTANT]
   >
   >Adobe Commerce在上不受支持 [!DNL Microsoft Windows] 或 [!DNL macOS].

- Adobe Commerce 2.4.1或更高版本

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

代理需要 [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 要安装在系统上的扩展和 [已配置](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 使用API密钥。 要验证是否安装了扩展，请运行以下命令：

```bash
bin/magento module:status Magento_ServicesId
```

如果已安装扩展并使用其他服务的现有API密钥对其进行配置，则 **必须重新生成API密钥** 并在Adobe Commerce管理员中为代理更新它。

1. 将您的网站放入 [维护模式](../../installation/tutorials/maintenance-mode.md).

1. 登录 [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

   >[!NOTE]
   >
   > 如果您在访问帐户时遇到问题，请参阅 [无法登录Adobe Commerce支持或云帐户](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) 以获取故障排除帮助。

1. 单击 **[!UICONTROL API Portal]**.

1. 单击 **[!UICONTROL Delete]** 在现有API密钥旁边。

1. [配置](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 新的API密钥。

>[!IMPORTANT]
>
> 如果您在API门户中生成新密钥，请立即更新中的API密钥 [!DNL Admin configuration]. 如果您生成新密钥但未更新 [!DNL Admin]，您的SaaS扩展将不再有效，并且您将丢失有价值的数据。

如果未安装扩展，请按照以下说明进行安装：

1. 将扩展添加到 `composer.json` 文件并进行安装。

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

1. [配置API密钥](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 以将扩展连接到您的系统。

## 安装代理

我们已经创建了一个 [shell脚本](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) 以简化安装。 我们建议使用shell脚本，但您可以遵循 [手动安装](#manual) 方法（如有必要）。

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

1. 下载并安装代理后， [将其配置为运行](#run-the-agent) 使用以下方法之一：

   - [服务](#service) （如果您具有根访问权限，则首选）

   - [Cron](#cron)

### 手动 {#manual}

如果您不想使用我们的 [shell脚本](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) 要安装代理，则必须按照以下步骤手动安装：

1. 创建一个要下载代理的目录。

   >[!TIP]
   >
   >我们建议在根Adobe Commerce项目目录之外安装代理。

1. 下载二进制文件并将其解包。

   >[!INFO]
   >
   >要使用 [!DNL Site-Wide Analysis Tool]中，您必须首先阅读并接受在从Adobe Commerce管理员访问功能板时显示的使用条款。

   对于 **AMD64** 架构：

   1. 下载启动器存档。

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. 解压缩启动器存档。

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```
   对于 **ARM64** 架构：

   1. 下载启动器存档。

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. 解压缩启动器存档。

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```


1. *（可选）* 验证校验和文件的签名。

   ```bash
   echo -n "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQ0lqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FnOEFNSUlDQ2dLQ0FnRUE0M2FBTk1WRXR3eEZBdTd4TE91dQpacG5FTk9pV3Y2aXpLS29HendGRitMTzZXNEpOR3lRS1Jha0MxTXRsU283VnFPWnhUbHZSSFhQZWt6TG5vSHVHCmdmNEZKa3RPUEE2S3d6cjF4WFZ3RVg4MEFYU1JNYTFadzdyOThhenh0ZHdURVh3bU9GUXdDcjYramFOM3ErbUoKbkRlUWYzMThsclk0NVJxWHV1R294QzBhbWVoakRnTGxJUSs1d1kxR1NtRGRiaDFJOWZqMENVNkNzaFpsOXFtdgorelhjWGh4dlhmTUU4MUZsVUN1elRydHJFb1Bsc3dtVHN3ODNVY1lGNTFUak8zWWVlRno3RFRhRUhMUVVhUlBKClJtVzdxWE9kTGdRdGxIV0t3V2ppMFlrM0d0Ylc3NVBMQ2pGdEQzNytkVDFpTEtzYjFyR0VUYm42V3I0Nno4Z24KY1Q4cVFhS3pYRThoWjJPSDhSWjN1aFVpRHhZQUszdmdsYXJSdUFacmVYMVE2ZHdwYW9ZcERKa29XOXNjNXlkWApBTkJsYnBjVXhiYkpaWThLS0lRSURnTFdOckw3SVNxK2FnYlRXektFZEl0Ni9EZm1YUnJlUmlMbDlQMldvOFRyCnFxaHNHRlZoRHZlMFN6MjYyOU55amgwelloSmRUWXRpdldxbGl6VTdWbXBob1NrVnNqTGtwQXBiUUNtVm9vNkgKakJmdU1sY1JPeWI4TXJCMXZTNDJRU1MrNktkMytwR3JyVnh0akNWaWwyekhSSTRMRGwrVzUwR1B6LzFkeEw2TgprZktZWjVhNUdCZm00aUNlaWVNa3lBT2lKTkxNa1cvcTdwM200ejdUQjJnbWtldm1aU3Z5MnVMNGJLYlRoYXRlCm9sdlpFd253WWRxaktkcVkrOVM1UlNVQ0F3RUFBUT09Ci0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQ==" | base64 -d > release.pub
   ```

   ```bash
   openssl dgst -sha256 -verify release.pub -signature launcher.sha256 launcher.checksum
   ```

1. *（可选）* 验证校验和。

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. 创建 `config.yaml` 文件包含以下内容。

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

1. 下载并安装代理后，您必须 [将其配置为运行](#run-the-agent) 使用以下方法之一：

   - [服务](#service) （如果您具有根访问权限，则首选）

   - [Cron](#cron)

## 运行代理 {#run-the-agent}

我们建议将代理配置为作为服务运行。 如果您对基础结构的访问权限有限，并且没有root权限，则必须使用 [cron](#cron) 而是。

### 服务 {#service}

1. 创建系统单元文件 `(/etc/systemd/system/scheduler.service)` 替换为 `<filesystemowner>` 拥有代理和Adobe Commerce软件安装目录的UNIX®用户)。 如果您以root用户身份下载代理，请更改目录和嵌套文件所有者。

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

1. 停止调度程序。

   ```bash
   systemctl stop scheduler
   ```

1. 禁用调度程序。

   ```bash
   systemctl disable scheduler
   ```

1. 删除计划程序服务的 `systemd` 单位文件。

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. 重新加载 `systemd` 管理器配置。

   ```bash
   systemctl daemon-reload
   ```

1. 重置任意 `systemd` 设备处于失败状态。

   ```bash
   systemctl reset-failed
   ```

1. 删除调度程序服务目录。

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

## 疑难解答

### 访问密钥未正确解析

如果访问密钥解析不正确，您可能会看到以下错误：

```terminal
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

要解决此错误，请尝试以下步骤：

1. 执行 [脚本安装](#scripted)，保存输出，然后查看输出中是否有错误。
1. 查看生成的 `config.yaml` 文件并验证Commerce实例和PHP的路径是否正确。
1. 确保运行调度程序的用户位于 [文件系统所有者](../../installation/prerequisites/file-system/overview.md) Unix组或与文件系统所有者是同一个用户。
1. 确保 [商务服务连接器](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 密钥安装正确，请尝试更新密钥以将扩展连接到系统。
1. [卸载](#uninstall) 代理在更新密钥后使用 [安装脚本](#scripted).
1. 运行调度程序并查看是否仍收到相同的错误。
1. 如果您仍收到相同的错误，请提高 `config.yaml` 调试和打开支持票证。

### *SIGFAULT* 错误

如果您看到 *SIGFAULT* 运行二进制文件时出错，您可能没有以Adobe Commerce和Agent文件的所有者的身份运行此文件。
要解决此问题，请检查代理目录中所有与Adobe Commerce文件拥有者具有相同用户的文件，以及二进制文件是否也应该在该用户下运行。
您可以使用 `chown` 命令更改文件所有者并切换到适当的用户。
确保您的守护程序化机制（Cron或System.d）在相应的用户下运行该过程。

>[!INFO]
>
>参见 [如何访问 [!DNL Site-Wide Analysis Tool] 并生成报告](../site-wide-analysis-tool/access.md).
