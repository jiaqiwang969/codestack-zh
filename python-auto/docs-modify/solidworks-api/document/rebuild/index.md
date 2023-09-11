---
layout: sw-tool
title: Macro to force rebuild SOLIDWORKS document
caption: Rebuild Model
description: VBA macro to force rebuild, hide all types and show isometric view of SOLIDWORKS model
image: force-rebuild.svg
labels: [api, upgrade, performance, rebuild]
group: Performance
---
这个VBA宏允许执行通常需要升级SOLIDWORKS模型到新版本所需的操作。它可以：

* 强制重建模型（ctrl+Q）

![重建所有配置](rebuild-all-configurations.png)

* 将模型设置为等轴方向

![缩放以适应](zoom-to-fit.png)

* 隐藏所有视图类型

![隐藏所有类型](view-hide-all-types.png)

通过设置相应常量的值来配置宏的操作

~~~ vb
Const DEFAULT_VIEWZOOMTOFIT As Boolean = True
Const DEFAULT_REBUILD As Boolean = True
Const DEFAULT_HIDE_ALL_TYPES As Boolean = True
~~~

此宏还支持[宏参数](https://cadplus.xarial.com/macro-arguments/)：**-zoomtofit**，**-rebuild**，**-hidealltypes**

![在Batch+中指定的宏参数](batch-plus-arguments.png)

{% code-snippet { file-name: Macro.vba } %}