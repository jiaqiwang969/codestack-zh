---
layout: sw-macro-fix
title: Fix invalid namespace in VSTA (C# or VB.NET) SOLIDWORKS macro
caption: Invalid Namespace In VSTA (C# or VB.NET) Macro
description: Fixing the compile error of VSTA macro when the code is copied from the example
image: vsta-copy-example-compile-error.png
labels: [macro, troubleshooting, vsta]
---
## 症状

从SOLIDWORKS API帮助文档或其他来源复制的SOLIDWORKS VSTA宏（C#或VB.NET）示例代码出现了多个编译错误：

* MacroName.SolidWorksMacro不包含'SwApp'的定义
* 当前上下文中不存在名称'Main'

![从示例中复制代码到VSTA宏时出现编译错误](vsta-copy-example-compile-error.png){ width=450 }

## 原因

VSTA宏基于多个连接的文件，这些文件必须位于相同的命名空间中。当创建新宏时，命名空间可能与示例源代码中使用的命名空间不一致。

~~~ cs
namespace MacroName.csproj
{
  ...
}
~~~

## 解决方法

将*SolidWorksMacro.cs*文件中的命名空间更改为与默认命名空间匹配

* 打开项目属性页面

![VSTA宏项目属性](project-properties.png){ width=250 }

* 复制“应用程序”选项卡中“默认命名空间”字段的值

![VSTA项目的默认命名空间](project-default-namespace.png){ width=350 }

* 将命名空间重命名为复制的值

![重命名命名空间以匹配默认命名空间](modified-namespace.png){ width=500 }

* 重新构建宏