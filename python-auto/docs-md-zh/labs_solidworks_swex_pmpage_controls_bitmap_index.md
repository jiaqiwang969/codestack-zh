---
title: SOLIDWORKS属性管理器页面中的位图控件
caption: 位图
description: 使用SwEx.PMPage框架在属性管理器页面中创建位图控件
image: bitmap.png
toc-group-name: labs-solidworks-swex
order: 11
---
![位图控件](bitmap.png)

静态位图将在属性管理器页面中为属性创建，该属性的类型为[Image](https://docs.microsoft.com/zh-cn/dotnet/api/system.drawing.image?view=netframework-4.8)或其他可分配给此类型的类型，例如[Bitmap](https://docs.microsoft.com/zh-cn/dotnet/api/system.drawing.bitmap?view=netframework-4.8)。

{% code-snippet { file-name: Bitmap.* } %}

## 位图大小

位图的默认大小为18x18像素，但可以使用[BitmapOptionsAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_BitmapOptionsAttribute.htm)通过在构造函数参数中提供宽度和高度值来覆盖此值：

{% code-snippet { file-name: Bitmap.Size.* } %}

> 由于SOLIDWORKS API的限制，位图无法在属性管理器页面显示后作为[动态值](/labs/solidworks/swex/pmpage/controls/dynamic-values/)更改。请在数据模型类的构造函数中或作为属性的默认值中分配图像。