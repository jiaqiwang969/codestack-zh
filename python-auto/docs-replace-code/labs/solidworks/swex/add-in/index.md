---
title: SwEx.AddIn Framework enables easy and robust development of add-ins with SOLIDWORKS API
caption: SwEx.AddIn
description: Advanced utilities for the development of powerful SOLIDWORKS add-ins using SOLIDWORKS API in .NET (C# and VB.NET). Framework simplifies the creation and maintaining of commands and UI elements.
image: logo.png
toc-group-name: labs-solidworks-swex
order: 2
redirect-from:
  - /labs/solidworks/dev-tools-addin/
---
![SOLIDWORKS的SwEx.AddIn框架](logo.png)

SwEx.AddIn提供了简化SOLIDWORKS插件开发的工具。

功能包括：

* 自动注册插件
* 简化命令组管理
* 事件管理（未来版本）
* 任务窗格、特征管理器选项卡、模型视图选项卡（未来版本）

源代码可在[GitHub](https://github.com/codestackdev/swex-addin)上获取。

## 特点

### 注册插件

只需添加AutoRegister属性即可注册插件（无需运行自定义regasm命令，无需调用任何静态类）

{% code-snippet { file-name: Overview.Register.* } %}

### 添加命令

可以通过创建枚举来定义命令。可以通过添加属性来自定义命令，如标题、工具提示、图标等。命令可以分组在子菜单下。只需指定图像（支持透明度），框架将创建与SOLIDWORKS兼容的所需位图。无需分配灰色背景以启用透明度，无需缩放图像以适应所需大小 - 只需使用任何图像，框架将完成其余工作。使用资源本地化插件。

{% code-snippet { file-name: Overview.CommandGroup.* } %}

### 管理文档生命周期和事件

框架将通过将文档包装在指定的类中来管理文档的生命周期，并允许处理常见事件：

{% code-snippet { file-name: Overview.DocHandler.* } %}

### 读写第三方存储和存储区

读写数据到内部SOLIDWORKS文件存储区从未如此简单。只需重写相应的事件，并使用XML、DataContract、Binary等序列化器对数据进行序列化/反序列化：

{% code-snippet { file-name: Overview.3rdParty.* } %}

### 在SOLIDWORKS面板中托管用户控件

只需指定要托管的用户控件，框架将完成其余工作：

#### 任务窗格

{% code-snippet { file-name: Overview.TaskPane.* } %}

## 视频教程

### 介绍

{% youtube { id: 8BXQZcPe4bA } %}

### 详细指南

{% youtube { id: EAm-3-Njkfw } %}