---
title: 质量控制
description: 了解与实施项目相关的Adobe商务质量控制流程。
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---


# 质量控制过程和工具

![质量控制流程图](../../assets/playbooks/quality-control-diagram.svg)

上图中的质量控制过程可简要描述如下。

<table>
<thead>
  <tr>
    <th>软件开发过程</th>
    <th>QC工作流</th>
    <th>QC</th>
    <th>QC领导</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>开发</td>
    <td>规划</td>
    <td></td>
    <td>审核并参与测试计划</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>创建测试规范（测试用例/测试方案）</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>准备和获取测试数据</td>
  </tr>
  <tr>
    <td></td>
    <td>测试分析与设计</td>
    <td>审核并参与测试计划</td>
    <td>开始准备，规范</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>创建测试规范（测试用例/测试方案）</td>
    <td>为项目编写或查看测试策略</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>准备和获取测试数据</td>
    <td> 指导、指导和监控分析、设计</td>
  </tr>
  <tr>
    <td>内部测试</td>
    <td>测试实施和执行</td>
    <td>实施测试、执行和记录测试</td>
    <td>监控测试的实施和执行</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>检查性能和扫描安全性 — 评估结果和与预期结果的偏差</td>
    <td>确保测试的可跟踪性至测试基础，并跟踪Bug跟踪系统上的错误</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>将错误发布到错误跟踪系统(Jira/Redmine/Trello)</td>
    <td>排定测试的优先级/计划，以便与PM定义的项目计划保持一致</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>修复错误后进行重新测试（确认测试）</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>评估和报告</td>
    <td>向QC潜在客户和PM报告测试进度</td>
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
    <td>随访</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>在更改源代码后执行重新测试和回归测试</td>
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
    <td>审核并参与任务</td>
    <td>检查和评估任务的时间</td>
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
    <td>为这些任务执行测试</td>
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

与我们为开发过程确定的[工具](project-management-tools.md)类似，我们选择了一些我们经常用于质量控制测试的选择解决方案和平台。

| 用途 | 工具 |
|---------------------------|---------------------------------------------------|
| 网站性能索引 | Google PageSpeed、Webpagetest、JMeter |
| 安全性 | Adobe商务安全扫描工具、SonarQube、ZAP |
| 问题管理系统 | 吉拉 |
| UI测试 | 完美像素， BrowserStack |
| API测试 | Postman， SoapUI |
| 自动测试 | 硒 |


## 网站性能索引

GooglePageSpeed会报告移动设备和桌面设备上页面的性能，并提供有关如何改进该页面的建议。

WebPageTest是一款Web性能工具，它使用真正的浏览器访问网页并收集时间量度。

JMeter是一个Apache项目，可用作负载测试工具，用于分析和测量各种服务的性能，重点关注Web应用程序。

## 安全性

SonarQube和ZAP在开发过程中引入，但我们也在这里介绍它如何参与QC过程。

SonarQube还用于持续检查代码质量，以通过对代码的静态分析来进行自动审查，以检测错误、代码气味和安全漏洞。

OWASPZAP(Zed Attack Proxy)既适用于应用程序安全性方面的新用户，也适用于专业的渗透测试人员。 某些内置功能包括拦截代理服务器、传统和AJAX Web爬网程序、自动扫描程序、被动扫描程序、强制浏览、模糊器、WebSocket支持、脚本语言和Plug-n-Hack支持。

## UI测试

Perfect Pixel允许开发人员和标记设计人员在开发的HTML的顶部放置半透明的图像叠加，并在它们之间执行像素级完美比较。

BrowserStack是一个云Web和移动测试平台，它允许开发人员跨按需浏览器、操作系统和真正的移动设备测试其网站和移动应用程序。

## API测试

Postman是用于API开发的协作平台。 Postman简化了构建API的每个步骤并简化了协作，以便您能够创建更好的API。

SoapUI是用于简单对象访问协议(SOAP)和表示状态传输(REST)的开源Web服务测试应用程序。 其功能包括Web服务检查；调用、开发、模拟和嘲弄；功能测试；负载和合规性测试。

## 自动测试

Selenium由多个组件（Selenium客户端API、Selenium WebDriver）组成，每个组件在帮助开发Web应用程序测试自动化方面起着特定的作用。
