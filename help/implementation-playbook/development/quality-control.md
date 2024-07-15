---
title: 质量控制
description: 了解与实施项目相关的Adobe Commerce质量控制流程。
exl-id: 0eb62b24-21f6-4cec-8ef9-eeaa1ee6ae52
feature: Build
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# 质量控制过程和工具

![质量控制流程图](../../assets/playbooks/quality-control-diagram.svg)

上图中的质量控制过程可简述如下。

<table>
<thead>
  <tr>
    <th>软件开发过程</th>
    <th>QC工作流</th>
    <th>QC</th>
    <th>QC负责人</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>开发</td>
    <td>规划</td>
    <td></td>
    <td>查看并贡献测试计划</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>创建测试规范（测试案例/测试场景）</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>准备和获取测试数据</td>
  </tr>
  <tr>
    <td></td>
    <td>测试分析和设计</td>
    <td>查看并贡献测试计划</td>
    <td>启动准备工作，规范</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>创建测试规范（测试案例/测试场景）</td>
    <td>编写或审查项目的测试策略</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>准备和获取测试数据</td>
    <td> 领导、指导和监控分析、设计</td>
  </tr>
  <tr>
    <td>内部测试</td>
    <td>测试实施和执行</td>
    <td>实施测试、执行并记录测试</td>
    <td>监控测试的实施和执行</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>检查性能和扫描安全性 — 评估结果和预期结果的偏差</td>
    <td>确保测试对测试基础的可跟踪性并跟踪Bug跟踪系统上的错误</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Post错误到错误跟踪系统(Jira/Redmine/Trello)</td>
    <td>排定测试优先级/计划测试时间，以符合PM定义的项目计划</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>修复错误后重新测试（确认测试）</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>评估和报告</td>
    <td>向QC销售线索和PM报告测试进度</td>
    <td>评估测试结果和进度</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>根据测试期间收集的信息编写测试摘要报告</td>
  </tr>
  <tr>
    <td>UAT</td>
    <td>UAT</td>
    <td>验证客户反馈或更改请求(CR)</td>
    <td>跟进</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>更改源代码后执行重新测试和回归测试</td>
    <td>控制</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>更新测试规范</td>
    <td></td>
  </tr>
  <tr>
    <td>维护</td>
    <td>维护</td>
    <td>查看任务并向其投稿</td>
    <td>审查和估计任务所需时间</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>创建/更新测试规范</td>
    <td>后续测试进度</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>执行这些任务的测试</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>执行回归测试</td>
    <td></td>
  </tr>
</tbody>
</table>

与我们在开发过程中确定的[工具](project-management-tools.md)类似，我们选择了几个我们经常用于质量控制测试的解决方案和平台。

| 用途 | 工具 |
|---------------------------|---------------------------------------------------|
| 网站绩效指数 | Google PageSpeed， Webpagetest， JMeter |
| 安全性 | Adobe Commerce安全扫描工具， SonarQube， ZAP |
| 问题管理系统 | JIRA |
| UI测试 | 完美像素，BrowserStack |
| API测试 | Postman、SoapUI |
| 自动化测试 | 硒 |


## 网站绩效指数

GooglePageSpeed报告页面在移动设备和桌面设备上的性能，并提供有关如何改进该页面的建议。

WebPageTest是一种Web性能工具，它使用真正的浏览器来访问网页并收集时间量度。

JMeter是一个Apache项目，可用作负载测试工具，用于分析和测量各种服务的性能，重点是Web应用程序。

## 安全性

在开发过程中引入了SonarQube和ZAP，但我们在此处也包含它，了解有关它如何参与QC过程的更多信息。

SonarQube还用于持续检查代码质量，通过静态分析代码来执行自动审查，以检测错误、代码异味和安全漏洞。

OWASPZAP (Zed Attack Proxy)旨在供应用程序安全新手和专业渗透测试人员使用。 一些内置功能包括拦截代理服务器、传统和AJAX Web爬网程序、自动扫描仪、被动扫描仪、强制浏览、Fuzzer、WebSocket支持、脚本语言和插件黑客支持。

## UI测试

Perfect Pixel允许开发人员和标记设计人员将半透明图像叠加放在所开发HTML的顶部，并在它们之间执行像素完美比较。

BrowserStack是一个云Web和移动测试平台，允许开发人员跨按需浏览器、操作系统和实际移动设备测试其网站和移动应用程序。

## API测试

Postman是API开发的协作平台。 Postman简化了构建API的每个步骤，并简化了协作，以便您可以创建更好的API。

SoapUI是一个用于Simple Object Access Protocol (SOAP)和呈现状态传输(REST)的开源Web服务测试应用程序。 其功能包括Web服务检查；调用、开发、模拟和模拟；功能测试；加载和合规性测试。

## 自动化测试

Selenium由若干组件（Selenium客户端API、Selenium WebDriver）组成，每个组件在帮助开发Web应用程序测试自动化方面承担特定角色。
