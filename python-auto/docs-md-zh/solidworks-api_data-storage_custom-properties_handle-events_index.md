---
title: 使用SOLIDWORKS API处理自定义属性修改事件（添加、删除、更改）
caption: 处理修改事件
description: 使用SOLIDWORKS API处理与一般或配置特定自定义属性的修改相关的所有事件。解决当AddCustomPropertyNotify、DeleteCustomPropertyNotify、ChangeCustomPropertyNotify事件未被触发时的问题。
image: custom-properties-events-console.png
labels: [自定义属性, 通知]
---
SOLIDWORKS API提供了通知来处理自定义属性的修改（如添加、删除或更改）。这些事件（AddCustomPropertyNotify、DeleteCustomPropertyNotify、ChangeCustomPropertyNotify）会在零件、装配体和图纸中触发，并支持一般和配置特定的自定义属性。然而，自SOLIDWORKS 2018起，这些事件不再对用户界面中由用户修改的自定义属性触发，只支持通过SOLIDWORKS API修改的自定义属性。

下面的代码示例提供了解决此问题的方法，并使得无论以何种方式修改自定义属性，都能处理通知。

* 创建控制台应用程序并添加下面的代码
* 运行控制台
* 修改自定义属性。修改结果将输出到控制台窗口：

![将属性修改信息输出到控制台](custom-properties-events-console.png)

## Program.cs

程序的入口点

{% code-snippet { file-name: Program.cs } %}

## CustomPropertiesEventsHandler.cs

{% code-snippet { file-name: CustomPropertiesEventsHandler.cs } %}