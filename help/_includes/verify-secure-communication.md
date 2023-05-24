---
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---
# 验证通信是否安全

本节将讨论验证HTTP基本身份验证是否正常工作的两种方法：

* 使用 `curl` 命令来验证必须输入用户名和密码才能获取群集状态
* 在管理员中配置HTTP基本身份验证

## 使用 `curl` 用于验证群集状态的命令

输入以下命令：

```bash
curl -i http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

例如，如果在搜索引擎服务器上输入命令，而您的代理使用的是端口8080：

```bash
curl -i http://localhost:8080/_cluster/health
```

将显示以下消息以指示身份验证失败：

```terminal
HTTP/1.1 401 Unauthorized
Date: Tue, 23 Feb 2016 20:35:29 GMT
Content-Type: text/html
Content-Length: 194
Connection: keep-alive
WWW-Authenticate: Basic realm="Restricted"
<html>
<head><title>401 Authorization Required</title></head>
<body bgcolor="white">
  <center><h1>401 Authorization Required</h1></center>
</body>
</html>
```

现在尝试以下命令：

```bash
curl -i -u <username>:<password> http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

例如：

```bash
curl -i -u magento_elasticsearch:mypassword http://localhost:8080/_cluster/health
```

此时，该命令会成功，并显示一条类似于以下内容的消息：

```terminal
HTTP/1.1 200 OK
Date: Tue, 23 Feb 2016 20:38:03 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 389
Connection: keep-alive
{"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
```

## 在Admin中配置HTTP基本身份验证

执行中讨论的相同任务 [搜索引擎配置](../configuration/search/configure-search-engine.md) *排除* 点击 **[!UICONTROL Yes]** 从 **[!UICONTROL Enable HTTP Auth]** 在提供的字段中列出并输入用户名和密码。

单击 **[!UICONTROL Test Connection]** 以确保它正常工作，然后单击 **[!UICONTROL Save Config]**.

您必须刷新缓存并重新编入索引，然后才能继续。
