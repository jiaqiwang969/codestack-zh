---
title: 在Windows Presentation Foundation (WPF)中托管SOLIDWORKS eDrawings控件
caption: 在WPF中托管控件
description: 在Windows Presentation Foundation (WPF)中将SOLIDWORKS eDrawings控件托管为WPF用户控件的详细指南
image: edrawings-wpf-window.png
labels: [edrawings,托管,wpf]
---
eDrawings API没有提供用于WPF的原生控件。但是可以使用[WindowsFormsIntegration](https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.forms.integration)框架在Windows Presentation Foundation (WPF)环境中托管Windows Forms控件。请按照[在Windows Forms中托管eDrawings控件](/edrawings-api/gettings-started/winforms/)指南创建用于Windows Forms的eDrawings控件。

## 创建新项目

* 启动Visual Studio
* 创建新项目，在*Visual C#*模板部分选择*WPF应用程序*
![创建WPF应用程序](visual-studio-new-wpf-project.png){ width=550 }
* 按照[在Windows Forms中托管eDrawings控件](/edrawings-api/gettings-started/winforms/)指南的步骤添加eDrawings互操作
* 添加对*WindowsFormsIntegration*的引用

## 创建eDrawings WPF控件

为eDrawings主机Windows Forms控件创建一个包装器

### eDrawingHost.cs

{% code-snippet { file-name: eDrawingHost.cs } %}

创建新的WPF用户控件，用于托管eDrawings，并可放置在其他WPF控件或WPF窗口上

解决方案树将类似于下面的结构。

![eDrawings WPF解决方案树](visual-studio-solution-tree.png){ width=350 }

### eDrawingsHostControl.xaml

XAML中不会有任何逻辑或额外的标记，所有内容都将在代码后台中实现

{% code-snippet { file-name: eDrawingsHostControl.xaml } %}

### eDrawingsHostControl.xaml.cs

{% code-snippet { file-name: eDrawingsHostControl.xaml.cs } %}

在此示例中，该控件定义了依赖属性*FilePath*，可以进行绑定，并表示要在eDrawings中打开的SOLIDWORKS文件的路径

### MainWindow.xaml

将以下标记添加到MainWindow中。它定义了文本框控件，其*Text*属性绑定到WPF eDrawing控件的*FilePath*依赖属性。这意味着一旦文本框中的值更改，文件将立即加载。

{% code-snippet { file-name: MainWindow.xaml } %}

更改文本框中的文件路径，以查看文件加载到WPF窗体中。

![SOLIDWORKS文件加载到WPF eDrawings控件中](edrawings-wpf-window.png){ width=350 }

源代码可在[GitHub](https://github.com/codestackdev/solidworks-api-examples/tree/master/edrawings-api/eDrawingsWpfHost)上找到。