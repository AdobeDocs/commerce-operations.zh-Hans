---
title: 启动步骤
description: 使用我们的Launch核对清单确保Adobe Commerce站点实施顺畅。
exl-id: d7807b2f-85c0-4e3e-a473-c65dbec44d28
feature: Configuration, Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# 启动步骤

测试并完成启动前核对清单后，我们可以在进行转换时开始启动的最后步骤。 这些步骤包括输入站点启动（上线）票证、切换访问权限，最后在商店上线时对其进行测试。

Adobe Commerce支持人员将与您一起完成该过程，检查状态并帮助解决出现的任何问题。 应使用票证跟踪所有问题，以便最好地捕获所发生的情况及其解决方式。 在将更新的不断迭代部署到启动的存储区时，可能会再次出现类似问题。 这些工单有助于查明问题并帮助调整部署任务。

- 将应用程序配置为基本URL
   - 将DNS切换到新站点
   - 访问您的DNS服务
   - 更新域和主机名的A和CNAME记录
   - 等待TTL时间传递并访问您的商店

- 完全在生产环境中测试
   - 验证网站的所有功能
   - 验证CDN缓存
   - 验证所有集成的第三方服务
   - 验证所有第三方系统

- 如果有任何问题阻止上线，请联系Adobe Commerce热线

![显示启动进程阶段3的图表](../../assets/playbooks/launch-steps-3.svg)
