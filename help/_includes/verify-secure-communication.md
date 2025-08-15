---
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 1%

---
# 验证通信是否安全

本节将讨论验证HTTP基本身份验证是否正常工作的两种方法：

* 使用`curl`命令验证必须输入用户名和密码才能获取群集状态
* 在管理员中配置HTTP基本身份验证

## 使用`curl`命令验证群集状态

输入以下命令：

```bash
curl -i http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

例如，如果在搜索引擎服务器上输入命令，而您的代理使用的是端口8080：

```bash
curl -i http://localhost:8080/_cluster/health
```

将显示以下消息来指示验证失败：

```
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

```
HTTP/1.1 200 OK
Date: Tue, 23 Feb 2016 20:38:03 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 389
Connection: keep-alive
{"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
```

## 在管理员中配置HTTP基本身份验证

执行[搜索引擎配置](../configuration/search/configure-search-engine.md) *中讨论的相同任务，但*&#x200B;除外，请单击&#x200B;**[!UICONTROL Yes]**&#x200B;列表中的&#x200B;**[!UICONTROL Enable HTTP Auth]**，然后在提供的字段中输入用户名和密码。

单击&#x200B;**[!UICONTROL Test Connection]**&#x200B;以确保它正常工作，然后单击&#x200B;**[!UICONTROL Save Config]**。

在继续之前，必须刷新缓存并重新索引。
