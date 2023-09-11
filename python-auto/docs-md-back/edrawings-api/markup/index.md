---
title: Utilizing markup functionality using SOLIDWORKS eDrawings API
caption: Markup
description: Guide on using the markup functionality (measurements, stamps, comments) using eDrawings API
labels: [edrawings,markup,getting started]
---
可以通过[IEModelMarkupControl](https://help.solidworks.com/2016/english/api/emodelapi/eDrawings.Interop.EModelMarkupControl~eDrawings.Interop.EModelMarkupControl.IEModelMarkupControl.html)接口访问eDrawings标记API（如评论、图章、测量）。

Interop可以在eDrawings安装文件夹中找到：*%commonprogramfiles%\eDrawings[版本]\eDrawings.Interop.EModelMarkupControl.dll*

可以通过调用[IEModelViewControl::CoCreateInstance](https://help.solidworks.com/2018/english/api/emodelapi/eDrawings.Interop.EModelViewControl~eDrawings.Interop.EModelViewControl.IEModelViewControl~CoCreateInstance.html) eDrawings API方法来访问标记接口。

可以传递标记控件的特定版本和版本无关的GUID或ProgId。

版本无关的GUID可以在注册表*HKEY_CLASSES_ROOT\EModelViewMarkup.EModelNonVersionSpecificMarkupControl\CLSID*中找到。

![版本无关的eDrawings标记控件GUID](non-version-specific-markup-guid.png)

特定版本的GUID可以在相应版本的标记控件下找到（例如*eDrawings 2018*的*EModelViewMarkup.EModelViewMarkupControl.18*或*eDrawings 2019*的*EModelViewMarkup.EModelViewMarkupControl.19*）

~~~ cs
//使用ProgId创建版本无关的标记实例
var eDrawingsMarkupCtrl = eDrawingsCtrl.CoCreateInstance("EModelViewMarkup.EModelMarkupControl") as EModelMarkupControl;
...
//使用GUID创建版本无关的标记实例
var eDrawingsMarkupCtrl = eDrawingsCtrl.CoCreateInstance("{5BBBC05A-BD4D-4e3b-AD5B-51A79DFC522F}") as EModelMarkupControl;
...
//使用ProgId创建特定版本的标记实例（eDrawings 2018）
var eDrawingsMarkupCtrl = eDrawingsCtrl.CoCreateInstance("EModelViewMarkup.EModelMarkupControl.18") as EModelMarkupControl;
~~~