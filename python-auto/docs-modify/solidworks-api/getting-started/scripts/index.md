---
title: How to utilize SOLIDWORKS API methods within the scripts
caption: Scripts
description: Article provides examples of calling SOLIDWORKS APIs from different scripts, including vbScript, PowerShell, JavaScript
labels: [Script, html, JavaScript, PowerShell, cmd]
order: 5
---
本节提供了从不同脚本（包括vbScript、PowerShell和JavaScript）调用SOLIDWORKS API的示例和解释。

{% youtube { id: 9akSYcyjQQc } %}

在SOLIDWORKS自动化中使用脚本的主要优点是简化的部署和维护过程。脚本是开源的，不需要特殊的IDE，并且可以轻松集成到自动化工作流程中。

脚本通常接受参数，这使得自动化过程可以以交互的方式进行。

脚本可以利用专门用于OLE自动化的SOLIDWORKS的特殊“automation”版本。这意味着SOLIDWORKS可以在后台以轻量级方式启动，从而大大提高了进程的性能。