---
title: 使用OpenGL和SOLIDWORKS API渲染带透明度的方块网格
caption: 渲染带透明度的方块网格
description: 使用OpenGL和SOLIDWORKS API渲染带透明度的方块网格
image: opengl-cubes.png
labels: [opengl,渲染,透明度]
---
![使用OpenGL渲染的透明方块](opengl-cubes.png){ width=250 }

这个示例演示了如何使用OpenGL和SOLIDWORKS API在预定义的网格中渲染带透明度的方块。

方块会自动渲染在所有打开的3D模型（零件或装配体）上。

可以通过更改插件中声明的常量来配置参数：

~~~ cs
private const int INST_COUNT = 27;
private const int ROWS_COUNT = 3;
private const int COLUMNS_COUNT = 3;
private const double DIST = 0.05;
private const double WIDTH = 0.1;
private const double HEIGHT = 0.1;
private const double LENGTH = 0.1;
private readonly Color COLOR = Color.FromArgb(200, Color.Blue);
~~~

请注意，这种方法是渲染OpenGL对象的简单方法，但它并不能提供最佳的性能优势。请参考[导入XAML文件并使用VBO进行渲染](/solidworks-api/adornment/opengl/vbo-xaml-importer/)以获取使用OpenGL顶点缓冲对象（VBO）进行高性能图形渲染的代码示例。

源代码可以从[GitHub](https://github.com/codestackdev/solidworks-api-examples/tree/master/swex/add-in/opengl/OpenGlBoxGrid)下载。

## AddIn.cs

这是插件的入口点。使用[SwEx.AddIn](/labs/solidworks/swex/add-in/)框架来通过提供包装类来管理文档的生命周期。

{% code-snippet { file-name: AddIn.cs } %}

## OpenGlDocumentHandler.cs

这是每个模型文档的处理程序类，它订阅SOLIDWORKS提供的OpenGL缓冲区交换通知，并根据输入参数计算方块的坐标并在模型的图形视图中进行渲染。

{% code-snippet { file-name: OpenGlDocumentHandler.cs } %}

## OpenGL.cs

OpenGL函数的导入列表。

{% code-snippet { file-name: OpenGL.cs } %}