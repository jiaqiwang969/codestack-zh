---
layout: sw-tool
title: 强制重建SOLIDWORKS文档的宏
caption: 重建模型
description: VBA宏，用于强制重建SOLIDWORKS模型、隐藏所有类型并显示等轴视图
image: force-rebuild.svg
labels: [api, 升级, 性能, 重建]
group: 性能
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

该宏还支持[宏参数](https://cadplus.xarial.com/macro-arguments/)：**-zoomtofit**，**-rebuild**，**-hidealltypes**

![在Batch+中指定的宏参数](batch-plus-arguments.png)

{% code-snippet { file-name: Macro.vba } %}