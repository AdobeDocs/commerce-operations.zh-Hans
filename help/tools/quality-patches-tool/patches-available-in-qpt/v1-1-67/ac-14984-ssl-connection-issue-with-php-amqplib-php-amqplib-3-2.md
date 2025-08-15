---
title: AC-14984：php-amqplib/php-amqplib ^3.2.0的SSL连接问题
description: 应用AC-14984修补程序，以修复在使用php-amqplib/php-amqplib版本^3.2.0时SSL连接失败并出现错误的Adobe Commerce问题。
feature: System
role: Admin, Developer
type: Troubleshooting
exl-id: cf46cd16-ef09-406a-835a-e5973887248f
source-git-commit: a934b02d42a5b9d2de722ebb6ef379ccca54649c
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# AC-14984：php-amqplib/php-amqplib ^3.2.0的SSL连接问题

AC-14984修补程序修复了在使用`php-amqplib/php-amqplib`版本`^3.2.0`时SSL连接失败并出现错误的问题。 安装[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67时，此修补程序可用。 修补程序ID为AC-14984。 请注意，此问题计划在Adobe Commerce 2.4.9中修复。

## 受影响的产品和版本

**为Adobe Commerce版本创建了修补程序：**

* Adobe Commerce（所有部署方法） 2.4.6-p10

**与Adobe Commerce版本兼容：**

* Adobe Commerce（所有部署方法） 2.4.6-p10 - 2.4.6-p11

>[!NOTE]
>
>该修补程序可能适用于具有新[!DNL Quality Patches Tool]发行版本的其他版本。 要检查修补程序是否与您的Adobe Commerce版本兼容，请将`magento/quality-patches`包更新到最新版本，并在[[!DNL Quality Patches Tool]：搜索修补程序页面](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=zh-Hans)上检查兼容性。 使用修补程序ID作为搜索关键字来查找修补程序。

## 问题

使用`php-amqplib/php-amqplib`版本`^3.2.0`时，SSL连接失败并出现错误。

<u>重现步骤</u>：

1. 在`app/env.php`中配置SSL连接：

```
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/',
      'ssl' => 'true',
      'ssl_options' => [
        'verify_peer' => true,
        'verify_peer_name' => false
      ],
    ),
  ),
```

1. 如果这是您第一次配置队列，请运行`bin/magento setup:upgrade`。
1. 运行任何队列使用者，例如： `bin/magento queue:consumers:start async.operations.all`

<u>预期的结果</u>：

队列使用者启动和处理消息时没有出现错误。

<u>实际结果</u>：

日志中会显示一条错误消息：

```
{
  "message": "Invalid frame type 21",
  "context": {},
  "level": "error",
  "level_name": "ERROR",
  "channel": "report",
  "datetime": "2025-05-14T07:00:00.000000+00:00",
  "extra": {},
  "@timestamp": "2025-05-14T07:00:00.000000X",
  "severity": "ERROR",
  "original_level": 400,
  "full_message": "Invalid frame type 21\n#0 /app/vendor/php-amqplib/php-amqplib/PhpAmqpLib/Connection/AbstractConnection.php(651): PhpAmqpLib\\Connection\\AbstractConnection->wait_frame(3.0)\n#1 /app/vendor/php-amqplib/php-amqplib/PhpAmqpLib/Channel/AbstractChannel.php(235): PhpAmqpLib\\Connection\\AbstractConnection->wait_channel(0, 3.0)\n#2 /app/vendor/php-amqplib/php-amqplib/PhpAmqpLib/Channel/AbstractChannel.php(352): PhpAmqpLib\\Channel\\AbstractChannel->next_frame(3.0)\n#3 /app/vendor/php-amqplib/php-amqplib/PhpAmqpLib/Connection/AbstractConnection.php(264): PhpAmqpLib\\Channel\\AbstractChannel->..."
}
```

## 应用修补程序

要应用单独的修补程序，请根据您的部署方法使用以下链接：

* Adobe Commerce或Magento Open Source内部部署： [[!DNL Quality Patches Tool] 指南中的](/help/tools/quality-patches-tool/usage.md)>使用情况[!DNL Quality Patches Tool]。
* 云基础架构上的Adobe Commerce：云基础架构上的Commerce指南中的[升级和修补程序>应用修补程序](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=zh-Hans)。

## 相关阅读

要了解有关[!DNL Quality Patches Tool]的更多信息，请参阅：

* [[!DNL Quality Patches Tool]： “工具”指南中用于高质量修补程序的](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)的自助服务工具。
