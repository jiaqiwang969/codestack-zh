---
title: 使用SOLIDWORKS API在文档中等待用户选择
caption: 等待用户选择
description: 使用SOLIDWORKS API和VBA宏在SOLIDWORKS文档中等待对象选择的两种方法
image: selected-edge.png
labels: [选择,事件,通知]
---
本文介绍了使用SOLIDWORKS API和VBA宏在SOLIDWORKS文档中等待对象选择的两种方法。

对于这两种方法，在宏的开头指定要等待选择的过滤器。可用的过滤器值在[swSelectType_e](https://help.solidworks.com/2014/english/api/swconst/SolidWorks.Interop.swconst~SolidWorks.Interop.swconst.swSelectType_e.html)枚举中定义。

~~~ vb
Const FILTER As Integer = swSelectType_e.swSelEDGES
~~~

## 阻塞线程等待选择

这种方法循环遍历所选对象，并阻塞当前线程，直到完成所需的选择。在每次迭代中调用*DoEvents*函数以继续消息队列，以便SOLIDWORKS窗口不会被锁定。

* 运行宏
* 选择边缘（或在过滤器中指定的对象）

![选择的边缘](selected-edge.png){ width=250 }

* 宏停止执行，并将*swObject*的引用设置为所选元素

![一旦选择了指定的对象，VBA宏停止执行](selection-stop-execution.png){ width=550 }

{% code-snippet { file-name: MacroBlocking.vba } %}

## 处理选择事件

这种方法使用SOLIDWORKS通知来处理选择。这是更可取的选项，因为它不会阻塞主线程，但是该选项需要添加类模块和额外的同步（根据要求），因为事件是异步处理的。

* 创建宏模块和类模块，如下所示

![宏解决方案树](macro-solution-tree.png)

* 运行宏并选择边缘（或在过滤器中指定的对象）
* 与前一种方法类似，代码在选择后停止执行，并将*swObject*的引用设置为所选元素

![一旦通过通知选择了指定的对象，VBA宏停止执行](selection-event-stop-execution.png){ width=550 }

### 宏模块

{% code-snippet { file-name: MacroEvent.vba } %}

### EventsListener类模块

{% code-snippet { file-name: EventsListener.vba } %}