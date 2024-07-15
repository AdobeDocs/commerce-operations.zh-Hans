---
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 1%

---
# 敏感数据

Adobe Commerce使用您的加密密钥加密以下内容：

* 信用卡信息
* 在管理员配置中指定的用户名和密码（例如，登录到付款网关）
* 通过网络发送的验证码值

Adobe Commerce *不*&#x200B;加密：

* 管理用户名和客户用户名和密码（这些密码经过哈希处理）
* 地址
* 电话号码
* 除信用卡号之外的其他类型的个人身份信息
