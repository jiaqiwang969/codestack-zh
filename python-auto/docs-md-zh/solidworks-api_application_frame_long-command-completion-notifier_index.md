---
layout: sw-tool
title: 使用SOLIDWORKS API通知长时间运行的SOLIDWORKS命令完成
caption: 通知长时间运行命令完成
description: 使用VBA宏处理SOLIDWORKS中的长时间运行命令（打开、重建、抑制等），并发出蜂鸣声通知其完成
image: command-progress.svg
labels: [事件,性能,通知,命令]
group: 性能
---
![在SOLIDWORKS中打开大型装配文档](opening-file-progressbar.png){ width=450 }

这个VBA宏将使用SOLIDWORKS API监听SOLIDWORKS命令（例如打开、重建、抑制、解析等），并通过将执行时间与用户指定的延迟时间进行匹配来识别长时间运行的命令。如果命令运行时间超过此时间段，则会播放蜂鸣信号，通知用户命令已完成。如果命令执行速度较快，则不会播放声音。

当处理大型模型时，这可能非常有用，因为在执行命令时可以切换屏幕或执行其他活动，并在操作完成后得到通知，而无需不断监视进度。

## 运行说明

* 创建新的宏并添加以下代码

{% code-snippet { file-name: Macro.vba } %}

* 通过更改*MIN_DELAY*常量的值来指定命令的最小延迟时间（以秒为单位）
* 创建新的类模块并将其命名为*CommandsListener*。将以下代码粘贴到类模块中：
* 启动宏。要在每次SOLIDWORKS会话中自动启动宏，请参阅[在SOLIDWORKS启动时自动运行宏](/solidworks-api/getting-started/macros/run-macro-on-solidworks-start/)文章。