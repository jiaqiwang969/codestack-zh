---
title: 使用SOLIDWORKS API处理关闭前和关闭后的通知
caption: 处理关闭前和关闭后的通知
description: 本示例演示了如何使用SOLIDWORKS API处理文件关闭的前后通知。
image: file-lock-output.png
labels: [事件, 关闭, PDM]
---
在关闭文件（销毁）时，会触发部件、装配体和图纸的关闭通知（例如[DestroyNotify2](https://help.solidworks.com/2017/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.DAssemblyDocEvents_DestroyNotify2EventHandler.html)），这意味着文件仍未从内存中释放。

对于产品数据管理（PDM）等应用程序来说，这可能是一个阻塞因素，因为关闭文件应该解锁它，可能需要执行一些附加操作（例如从本地缓存中删除文件、移动到存档、对流进行后处理、清除资源）。

本示例演示了如何使用SOLIDWORKS API处理关闭前和关闭后的通知。

* 打开任何SOLIDWORKS文件
* 从宏模块的主方法中运行宏。将显示临时窗体
* 关闭SOLIDWORKS文件
* 在VBA的即时窗口中查看输出。将打印两行：
    * 第一行 - 当文件即将关闭时
    * 第二行 - 当文件完全关闭时

在两个处理程序中，宏都会检查文件是否解锁（即从内存中释放）。结果是在第一个处理程序中，文件被锁定，在第二个处理程序中解锁，正如预期的那样。

![文件关闭的输出结果](file-lock-output.png)

**注意：IsFileUnlocked函数会以读写模式打开流，可能会损坏文件。强烈建议仅在示例模型上使用此宏**

要创建一个宏，请将2个模块添加到VBA编辑器中：

* 名为*FileWatcher*的类模块
* 名为*UserForm1*的用户窗体

![VBA宏解决方案树](macro-solution.png){ width=250 }

将代码粘贴到相应的模块中，如下所示：

**FileWatcher类模块**
{% code-snippet { file-name: FileWatcher.vba } %}

**UserForm1窗体**
{% code-snippet { file-name: UserForm1.vba } %}

**宏模块**
{% code-snippet { file-name: Macro.vba } %}