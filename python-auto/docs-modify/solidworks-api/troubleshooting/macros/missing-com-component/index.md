---
layout: sw-macro-fix
title: How to fix Missing COM (ActiveX) Component error
caption: Missing COM Component
description: How to fix Runtime error 429 in VBA macros
image: runtime-error-429.png
labels: [macro, troubleshooting]
---
## 症状

运行宏时显示*运行时错误'429'：无法创建ActiveX组件对象*错误。通常会突出显示*CreateObject*函数：

~~~ vb
Dim obj as Object
Set obj = CreateObject("ComComponentProgId")
~~~

![运行时错误'429'：无法创建ActiveX组件对象](runtime-error-429.png){ width=350 }

## 原因

目标机器上未注册所需的COM组件（ActiveX）。这通常是因为目标应用程序未安装（例如Excel、MS Access等），或者组件在x32系统中注册，而宏在x64环境中运行（自SOLIDWORKS 2012起）。

## 解决方法

将所需的COM组件安装到正确的环境中。可能需要联系组件的供应商或宏的开发人员，以获取有关所使用的ActiveX组件的更多信息。