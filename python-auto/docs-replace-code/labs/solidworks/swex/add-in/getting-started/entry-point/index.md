---
title: Entry Point of SwEx.AddIn framework
caption: Entry Point
description: Instructions on starting the coding with the SwEx.AddIn framework for SOLIDWORKS
toc-group-name: labs-solidworks-swex
order: 2
---
## 注册插件

为了将SOLIDWORKS插件与SwEx框架注册，需要执行以下步骤：

* 创建一个公共类，该类继承[SwAddInEx](https://docs.codestack.net/swex/add-in/html/T_CodeStack_SwEx_AddIn_SwAddInEx.htm)类
* 通过添加*System.Runtime.InteropServices.ComVisibleAttribute*属性，使该类可见
* 添加[AutoRegisterAttribute](https://docs.codestack.net/swex/add-in/html/T_CodeStack_SwEx_AddIn_Attributes_AutoRegisterAttribute.htm)属性，将所需信息添加到注册表中。

### C\#

~~~ cs
using CodeStack.SwEx.AddIn;
using CodeStack.SwEx.AddIn.Attributes;
using System;
using System.Runtime.InteropServices;

namespace CodeStack.SwEx
{
    [AutoRegister("MyAddIn title", "MyAddIn description", true)]
    [ComVisible(true), Guid("025F9A68-F2FE-46CF-8BA2-8E19FBCDE9A0")]
    public class MyAddIn : SwAddInEx
    {
        public override bool OnConnect()
        {
            // Initialize the add-in, create menu, load data etc.
            return true;
        }

        public override bool OnDisconnect()
        {
            // Dispose the add-in's resources
            return true;
        }
    }
}

~~~



### VB.NET

~~~ vb
Imports CodeStack.SwEx.AddIn
Imports CodeStack.SwEx.AddIn.Attributes
Imports System.Runtime.InteropServices

<AutoRegister("MyAddIn title", "MyAddIn description", True)>
<ComVisible(True), Guid("025F9A68-F2FE-46CF-8BA2-8E19FBCDE9A0")>
Public Class MyAddIn
    Inherits SwAddInEx

    Public Overrides Function OnConnect() As Boolean
        'Initialize the add-in, create menu, load data etc.
        Return True
    End Function

    Public Overrides Function OnDisconnect() As Boolean
        'Dispose the add-in's resources
        Return True
    End Function

End Class

~~~



## OnConnect

此函数在ConnectToSw入口点中调用。重写此函数以初始化插件。

返回初始化的结果。返回*true*表示初始化成功。返回'false'表示取消加载插件。

应使用此重写来验证许可证（如果验证失败，则返回false），添加命令管理器、任务窗格视图、初始化事件管理器等。

## OnDisconnect

此函数在DisconnectFromSw函数中调用。使用此函数释放所有资源。您不需要释放指向SOLIDWORKS或命令管理器的com指针，因为SwEx框架会自动释放它们。

## 访问SOLIDWORKS应用程序对象

SwEx框架提供对以下由框架预分配的对象的访问：

### App属性
指向SOLIDWORKS应用程序的指针

### AddInCookie属性
插件ID

### CmdMgr属性
指向命令管理器的指针

## 注销插件
在Visual Studio中清理项目时，插件将自动删除并取消注册所有COM对象。