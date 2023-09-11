---
title: 使用SOLIDWORKS文档管理器API获取所有装配组件
caption: 获取所有组件
description: 该示例演示了如何使用文档管理器API从文档中获取所有层级的组件
image: components-tree.png
---
![SOLIDWORKS装配树](components-tree.png){ width=200 }

该示例演示了如何使用文档管理器API从文档中获取所有层级的组件。

* 在SOLIDWORKS中打开宏
* 指定文档管理器密钥
* 指定顶层装配的路径
* 运行宏。所有组件数据将输出到VBA编辑器的立即窗口中

要仅获取顶层组件，请修改函数如下所示

~~~ vb
Call GetAllComponents(swDmDoc, "", True, comps)
~~~

> 在遍历装配层级时，请不要存储[ISwDMComponent](https://help.solidworks.com/2015/english/api/swdocmgrapi/solidworks.interop.swdocumentmgr~solidworks.interop.swdocumentmgr.iswdmcomponent.html)的指针，因为一旦文档关闭或指针被释放，它将被销毁

{% code-snippet { file-name: Macro.vba } %}