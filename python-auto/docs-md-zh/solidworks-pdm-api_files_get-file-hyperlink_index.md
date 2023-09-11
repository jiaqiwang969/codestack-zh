---
title: 获取SOLIDWORKS PDM vault（conisio url）中文件的超链接
caption: 获取文件超链接
description: 使用PDM Professional API，这个PowerShell脚本可以获取指定文件的一致超链接（conisio url）
image: hyperlink-email.png
labels: [conisio, 超链接]
---

这个PowerShell脚本允许提取保险柜中指定文件的conisio url。这个链接可以用于获取一个持久的文件链接，可以被任何SOLIDWORKS PDM用户使用。

使用SOLIDWORKS PDM API提取所需数据以形成conisio url：文件ID、文件夹ID等。

创建2个脚本文件并粘贴以下代码：

## get-url.ps1
{% code-snippet { file-name: get-url.ps1 } %}

## get-url.cmd
{% code-snippet { file-name: get-url.cmd } %}

使用以下参数调用命令行：

* 保险柜名称
* 文件的完整路径
* 超链接的操作。选择以下之一：
    * 打开
    * 查看
    * 浏览
    * 获取
    * 锁定
    * 属性
    * 历史记录

例如：

~~~ cmd
get-url myvault "D:\myvault\part.sldprt" 浏览
~~~

超链接将输出到控制台：

![Conisio url输出到控制台窗口](conisio-url.png){ width=450 }

现在可以使用这个超链接来访问文件。

![Conisio url插入到电子邮件中的链接](hyperlink-email.png){ width=450 }