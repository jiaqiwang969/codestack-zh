---
title: 使用SOLIDWORKS eDrawings API入门
caption: 入门指南
description: 开发使用eDrawings API的应用程序的入门指南
image: edrawings.png
labels: [edrawings,入门指南]
order: 1
---
![eDrawings应用程序](edrawings.png){ width=350 }

可以通过托管eDrawings ActiveX控件并调用其方法来利用eDrawings API。

该控件实现了[IEModelViewControl](https://help.solidworks.com/2016/english/api/emodelapi/eDrawings.Interop.EModelViewControl~eDrawings.Interop.EModelViewControl.IEModelViewControl.html)接口，代表API对象模型中的最顶层对象。

[IEModelMarkupControl](https://help.solidworks.com/2016/english/api/emodelapi/eDrawings.Interop.EModelMarkupControl~eDrawings.Interop.EModelMarkupControl.IEModelMarkupControl.html)使得可以通过API访问eDrawings的标记功能。有关eDrawings标记API的更多信息，请参阅[使用SOLIDWORKS eDrawings API利用标记功能](/edrawings-api/markup/)。

eDrawings控件可以作为ActiveX控件托管在非托管应用程序中，也可以作为.NET应用程序的用户窗体（[User Forms](winforms)）、WPF应用程序（[WPF application](wpf)）和HTML页面中的控件。

Interop dll可以在eDrawings的安装文件夹中找到。通常位于*%commonprogramfiles%\eDrawings[Version]\eDrawings.Interop.EModelViewControl.dll*

在.NET应用程序中，可以通过实现[AxHost](https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.axhost)来创建eDrawings宿主控件。

~~~ cs
public class EDrawingHost : AxHost
{
    public EDrawingHost() : base("22945A69-1191-4DCF-9E6F-409BDE94D101")
    {
        m_IsLoaded = false;
    }
}
~~~

控件的GUID可以在注册表中找到。

版本无关的GUID可以在注册表键*HKEY_CLASSES_ROOT\EModelView.EModelNonVersionSpecificViewControl\CLSID*中找到，其值为*{22945A69-1191-4DCF-9E6F-409BDE94D101}*

![eDrawings控件的版本无关GUID](non-version-specific-guid.png)

如果安装了多个版本的eDrawings控件，则版本无关的GUID将对应于在注册表键*HKEY_CLASSES_ROOT\EModelView.EModelViewControl\CurVer*中设置的当前版本：

![eDrawings控件的当前版本](edrawings-control-current-version.png)

为了启用特定版本的eDrawings，需要使用特定的GUID。例如，对于eDrawings 2018，GUID可以在注册表键*HKEY_CLASSES_ROOT\EModelView.EModelViewControl.18\CLSID*中找到，其值为*{a338ddd7-0c6c-43c9-8d1c-c2825ca9ac7c}*。

![eDrawings控件的特定版本GUID](edrawings-2018-specific-version.png)

*eDrawings.Interop.EModelViewControl.dll*中的eDrawings接口既不向后兼容也不向前兼容。这意味着OCX控件只能转换为相应的Interop版本，因为不同版本的所有接口在GUID上都有所不同。作为一种解决方法，可以使用后期绑定和[ComEventsHelper](https://docs.microsoft.com/en-us/dotnet/api/system.runtime.interopservices.comeventshelper?view=netcore-3.1)来访问eDrawings API。请参阅[此实现](https://github.com/xarial/cad-plus/blob/master/src/SwEDrawingsHost/EDrawingsControl.cs)。