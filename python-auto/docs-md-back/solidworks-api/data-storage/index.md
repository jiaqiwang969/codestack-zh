---
title: Storing data in SOLIDWORKS models using API
caption: Data Storage
description: Collection of articles and code examples which demonstrate how to store different type of data within the SOLIDWORKS models (3rd party storage, attributes, custom properties)
image: solidworks-model-data-storage.png
order: 4
---
![通过API在模型中存储用户数据](solidworks-model-data-storage.png){ width=250 }

SOLIDWORKS提供了多种方式，可以使用API在SOLIDWORKS模型中存储自定义用户数据（例如文本、数字或更复杂的类型，如图像或视频）。最常见的方式有：

## 自定义属性

允许在模型或配置中添加自定义键值对。键的类型是不区分大小写的字符串，必须在范围内是唯一的（例如文档级别或配置级别）。值的类型可以是文本、数字、日期和布尔值（是或否）。用户可以编辑自定义属性。

## 属性

属性是添加到特征树中的自定义特征，可以保存带有值（字符串或数字）的参数。属性还可以与可选择的对象（面、顶点、边和组件）关联。属性不能与草图段关联。属性可以在特征树中隐藏。属性不能从用户界面更改。

## 第三方存储

SOLIDWORKS允许在主模型流中创建自定义COM存储。可以在此流中序列化/反序列化任何自定义数据。

本节包含了演示使用上述技术在模型中保存数据的宏和代码示例，使用SOLIDWORKS API。