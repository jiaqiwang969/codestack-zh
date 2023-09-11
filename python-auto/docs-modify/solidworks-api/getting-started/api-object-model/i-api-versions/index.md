---
title: Difference between SOLIDWORKS API methods with and without I
caption: I-Versions Of Methods And Interfaces
description: Explanation of the differences between method names and interfaces containing the I at the beginning (e.g. IModelDoc2 vs ModelDoc2)
image: intellisense-events.png
labels: [events,i-methods,i-interfaces]
---
SOLIDWORKS API中的方法、属性和对象（接口）有两个版本可供使用：

* 带有**I**开头（例如ISldWorks、IModelDoc2、IAnnotation、ISldWorks::IActiveDoc）
* 不带有**I**开头（例如SldWorks、ModelDoc2、Annotation、SldWorks::ActiveDoc）

这两种选择都对应同一个对象或方法。主要区别如下：

* I版本的方法不公开事件

下面是以*SldWorks*声明的变量的可用成员的快照。可用的事件：

![以SldWorks声明的变量的可用事件列表](intellisense-events.png){ width=250 }

下面是以*ISldWorks*声明的变量的可用成员的快照。没有可用的事件：

![以ISldWorks声明的变量没有可用事件](intellisense-no-events.png){ width=250 }

* I版本的方法通常返回类型安全的接口版本，而不是对象或IDispatch。这意味着在编译时强制执行类型安全的语言（如C#）中不需要显式转换：

~~~ cs
ISldWorks app;
...
IModelDoc2 model = app.IActiveDoc; //正确
IModelDoc2 model = app.ActiveDoc; //编译错误
IModelDoc2 model = app.ActiveDoc as IModelDoc2; //正确
~~~