---
title: SwEx.PMPage框架的示例和源代码
caption: 示例
description: 使用SwEx.PMPage框架开发SOLIDWORKS的示例集合
toc-group-name: 实验室-solidworks-swex
order: 4
---
本节包含使用SwEx.PMPage框架和SOLIDWORKS API开发高级属性管理器页面的示例。

## 用于调试主要框架功能的虚拟插件（C#）
[源代码](https://github.com/codestackdev/swex-pmpage/tree/master/Samples/AddIn)

该项目包含一个简短的示例，利用了SwEx.PMPage框架的所有功能，尽管该项目没有执行任何有用的操作，但它是探索SwEx.PMPage API的良好起点。

## 插入注释示例（C#）
* [源代码](https://github.com/codestackdev/swex-examples/tree/master/pmpage/InsertNote/csharp)

此示例使用属性管理器页面收集SOLIDWORKS绘图文档中插入重复注释所需的用户输入：

* 注释文本
* 注释位置
* 可选的附加实体

用户输入将被存储，并可以在不同的SOLIDWORKS会话中重复使用。