---
layout: sw-pdm-addin-fix
title: Fix 'Please select at least one DLL implementing the IEdmAddIn5 interface' error
caption: Please select at least one DLL implementing the IEdmAddIn5 interface
description: Troubleshooting the 'Please select at least one DLL implementing the IEdmAddIn5 interface' error when registering SOLIDWORKS PDM add-in
image: no-addin-dll.png
labels: [pdm add-in, error]
---
## 症状

在使用SOLIDWORKS PDM管理工具添加插件时，会显示以下错误信息：*请选择至少一个实现IEdmAddIn5接口的DLL*

![添加插件时的错误](no-addin-dll.png){ width=450 }

## 原因

当SOLIDWORKS PDM无法找到实现[IEdmAddIn5](https://help.solidworks.com/2019/English/api/epdmapi/EPDM.Interop.epdm~EPDM.Interop.epdm.IEdmAddIn5.html)接口的类时，就会出现此错误。

为了使插件类对SOLIDWORKS PDM可见，它必须是公共的并且可通过COM访问。

以下是一些错误的插件声明示例：

### 类没有标记为COM可见

~~~cs
public class PdmAddIn : IEdmAddIn5
{
}
~~~

### 类没有访问修饰符（默认为私有）

~~~cs
[ComVisible(true)]
class PdmAddIn : IEdmAddIn5
{
}
~~~

### 类标记为internal

~~~cs
[ComVisible(true)]
internal class PdmAddIn : IEdmAddIn5
{
}
~~~

## 解决方法

确保插件类是公共的，并且使用[ComVisible](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.interopservices.comvisibleattribute)属性进行修饰，值设置为*True*

~~~cs
[ComVisible(true)]
public class PdmAddIn : IEdmAddIn5
{
}
~~~