---
title: Creating C# add-in for SOLIDWORKS automation using API
caption: Creating C# Add-In For SOLIDWORKS
description: Detailed guide of creating SOLIDWORKS add-in from scratch using C#
image: new-project-class-library.png
labels: [add-in, c#]
---
* 在Microsoft Visual Studio中创建新项目
* 在*Visual C#*模板下选择*类库*模板。指定项目的位置和名称

![在Visual Studio中创建新的类型库项目](new-project-class-library.png){ width=450 }

* 添加对SolidWorks Interop库的引用：SolidWorks.Interop.sldworks.dll、SolidWorks.Interop.swconst.dll、SolidWorks.Interop.swpublished.dll。Interop库位于**SOLIDWORKS安装文件夹**\api\redist，用于针对Framework 4.0及更高版本的项目，以及**SOLIDWORKS安装文件夹**\api\redist\CLR2，用于针对Framework 2.0和3.5的项目。

对于针对Framework 4.0的项目，我建议将**[嵌入互操作类型](https://docs.microsoft.com/zh-cn/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)**选项设置为false。
否则，在调用SOLIDWORKS API时可能会由于类型转换问题导致应用程序的行为不可预测。

![嵌入SOLIDWORKS互操作类型](embed-interops-false.png){ width=350 }

> 在一些教程中，添加了对solidworkstools.dll库的引用。该库是可选的，在本教程中不会使用到它。

* 添加一个公共类，使用一个用户友好的名称。这将是插件的主类。该类必须是公共的和COM可见的。我建议使用[ComVisibleAttribute](https://docs.microsoft.com/zh-cn/dotnet/api/system.runtime.interopservices.comvisibleattribute?view=netframework-4.7.2)将类标记为COM可见对象，并使用[GuidAttribute](https://docs.microsoft.com/zh-cn/dotnet/api/system.runtime.interopservices.guidattribute?view=netframework-4.7.2)为插件类显式分配COM GUID：

~~~ cs
[ComVisible(true)]
[Guid("31B803E0-7A01-4841-A0DE-895B726625C9")]
public class MySampleAddin : ISwAddin
{
    ...
}
~~~

我建议在项目设置中不选择*使程序集COM可见*选项，而只将需要的类标记为COM可见，如上所述。

![使程序集COM可见标志](make-assembly-com-visible.png){ width=400 }

* 插件dll必须使用/codebase标志进行注册。项目设置中的*注册COM互操作性*选项在注册时不使用此选项，因此在这种情况下不适用。而是添加以下后期构建操作：

~~~ bat
"%windir%\Microsoft.NET\Framework64\v4.0.30319\regasm" /codebase "$(TargetPath)"
~~~

![后期构建事件将dll注册为COM对象](post-build-event.png){ width=400 }

这将确保在每次构建插件项目时进行正确的注册。

* 为了获得更好的调试体验，我建议在项目设置中设置SOLIDWORKS的完整路径作为外部应用程序。

![在调试插件时将SOLIDWORKS作为外部程序启动](start-external-program.png){ width=400 }

这将允许通过按下绿色运行按钮或F5键从Visual Studio启动SOLIDWORKS，并自动附加调试器。

* 需要向SOLIDWORKS注册表分支添加注册信息，以使其对应用程序可见。为了简化这个过程，可以在注册和取消注册dll作为COM对象时自动添加和删除此信息，方法是定义函数并使用[ComRegisterFunctionAttribute](https://docs.microsoft.com/zh-cn/dotnet/api/system.runtime.interopservices.comregisterfunctionattribute?view=netframework-4.7.2)和[ComUnregisterFunctionAttribute](https://docs.microsoft.com/zh-cn/dotnet/api/system.runtime.interopservices.comunregisterfunctionattribute?view=netframework-4.7.2)属性进行修饰。

* 复制以下代码作为插件的代码，并编译项目

{% code-snippet { file-name: add-in.cs } %}

* 编译后可能会显示以下警告。

![未签名程序集的编译警告](compile-warning-unsigned.png){ width=450 }

可以忽略此警告。

* 运行SOLIDWORKS，将显示*Hello World*消息框。

使用[xCAD.NET Framework](https://xcad.net/)框架可以简化上述代码，如下所示：

~~~ cs
[Title("示例插件")]
[Description("示例'Hello World' SOLIDWORKS插件")]
[ComVisible(true), Guid("31B803E0-7A01-4841-A0DE-895B726625C9")]
public class MySampleAddIn : SwAddInEx
{
    public override void OnConnect()
    {
        Application.ShowMessageBox("Hello World!");
    }
}
~~~