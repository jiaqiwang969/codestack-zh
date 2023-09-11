---
title: 在SOLIDWORKS PDM vault中签入所有已签出的文件
caption: 签入所有已签出的文件
description: 用于在SOLIDWORKS PDM vault中签入所有已签出的文件的命令行实用程序
image: console-output.png
labels: [签入,签出,PDM]
---
这个VB.NET命令行实用程序会搜索指定的SOLIDWORKS PDM Professional vault中的所有已签出文件，并将它们签入。

该实用程序可以从命令行调用，并可以作为自动化过程的一部分（例如Windows任务计划程序）。

实用程序需要指定3个参数：

* Vault名称
* 用户名
* 用户密码

文件列表、ID和被锁定的用户信息将显示在命令行中。脚本执行完成后，所有文件将被签入。执行过程中发生的任何错误都会打印到控制台窗口中。

![命令行输出](console-output.png){ width=450 }

{% code-snippet { file-name: Module1.vb } %}