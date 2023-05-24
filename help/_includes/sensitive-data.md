---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---
# 敏感数据

Adobe Commerce和Magento Open Source使用您的加密密钥加密以下内容：

* 信用卡信息
* 管理员配置中指定的用户名和密码（例如，登录到付款网关）
* 通过网络发送的验证码值

Adobe Commerce和Magento Open Source do *非* 加密：

* 管理用户名和客户用户名和密码（这些密码经过哈希处理）
* 地址
* 电话号码
* 除信用卡号之外的其他类型的个人身份信息
