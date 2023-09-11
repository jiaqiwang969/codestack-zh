---
layout: sw-macro-fix
title: Fix SOLIDWORKS macro which is using future version APIs
caption: Macro Is Using Future Version APIs
description: Fixing the macro which fails when run on old (not the latest) version of SOLIDWORKS and Run-time error '438' - object doesn't support this property or method or Run-time error '445' - object doesn't support this action error is displayed
image: object-doesnt-support-this-action.png
labels: [macro, troubleshooting]
redirect-from:
  - /2018/04/macro-troubleshooting-macro-using-future-version-apis.html
---
## 症状

最近开发的SOLIDWORKS宏在旧版本（非最新版本）SOLIDWORKS上运行。运行时，显示*运行时错误'438'：对象不支持此属性或方法*。

![运行宏时显示运行时错误'438'：对象不支持此属性或方法](object-doesnt-support-this-property-or-method.png){ width=400 height=151 }

或者可能显示*运行时错误'445'：对象不支持此操作*。

![运行宏时显示运行时错误'445'：对象不支持此操作](object-doesnt-support-this-action.png){ width=400 height=171 }

## 原因

SOLIDWORKS是[向后兼容](https://en.wikipedia.org/wiki/Backward_compatibility)的系统，这意味着旧版本的文件或API将与每个新版本兼容。然而，SOLIDWORKS不是[向前兼容](https://en.wikipedia.org/wiki/Forward_compatibility)，这意味着不能在旧版本的软件中使用新的API。每个SOLIDWORKS版本都会向库中添加新的API，开发人员可以使用这些API编写宏。但是这些宏不能在旧版本的SOLIDWORKS中使用。

## 解决方法

* 检查SOLIDWORKS API帮助文档，查看错误中突出显示的方法的可访问性

![SOLIDWORKS API帮助文档中的可用性选项](comp-config-properties-availability.png){ width=400 height=216 }

* 如果最早可用版本较新，则需要用替代方法替换该方法

通常，SOLIDWORKS会使用索引命名方法，例如OpenDoc4、OpenDoc5、OpenDoc6，表示被取代的版本。如果是这种情况，请尝试查看是否有旧版本的该方法可用。如果有，可以使用该方法。请注意，旧版本可能具有不同的参数集，所以仅更改版本号可能不足够。

![CompConfigProperties API方法的不同版本之间的差异](comp-config-prps-vers-diff.png){ width=400 height=122 }

* 如果没有可用的旧方法，则需要使用替代方法重写宏的逻辑。
* 将SOLIDWORKS软件升级到最新的最低支持版本

示例宏使用了添加到SOLIDWORKS 2017的API

{% code-snippet { file-name: suppress-component-sw2017.vba } %}

修改后的宏，与SOLIDWORKS 2005及更高版本兼容

{% code-snippet { file-name: suppress-component-sw2005.vba } %}