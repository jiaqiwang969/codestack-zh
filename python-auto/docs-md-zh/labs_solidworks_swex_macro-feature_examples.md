---
title: 使用 SwEx.MacroFeature 框架构建的包含源代码的 SOLIDWORKS API 示例
caption: 示例
description: 使用 SwEx.MacroFeature 框架的 SOLIDWORKS API 示例集合
toc-group-name: labs-solidworks-swex
order: 4
---
SwEx.MacroFeature 是一个用于 SOLIDWORKS API 的框架，可以简化宏特征的开发和数据绑定。

本节列出了基于 SwEx.MacroFeature 框架的示例和应用程序。

## 测试宏特征项目

[源代码](https://github.com/codestackdev/swex-macrofeature/tree/dev/AddInExample)
这是一个基本示例，展示了 SwEx.Framework 中的所有功能。该示例没有执行任何有用的功能，您可以使用它来探索框架使用的代码片段。

## 库存主控

[源代码](https://github.com/codestackdev/stock-fit-geometry)

这是一个用于自动生成三维几何文档库存适配（边界元素）的实用工具。宏特征用于生成自定义库存特征，根据输入参数在输入体周围生成圆柱几何。

## 将实体转换为曲面

[源代码](https://github.com/codestackdev/solidworks-api-examples/tree/master/swex/macro-feature/convert-solid-to-surface)

这是一个示例宏特征，允许将实体转换为曲面体并保持关联性。

## 几何++

[源代码](https://github.com/codestackdev/geometry-plus-plus)

用于管理 SOLIDWORKS 中几何体的高级命令。所有命令都以动态宏特征的形式实现，可以修改现有几何体或添加新的几何体。

## 将几何体链接到外部文件

[源代码](https://github.com/codestackdev/solidworks-api-examples/tree/master/swex/macro-feature/link-external-file)

示例演示了从外部文件加载几何体（类似于插入零件功能）的方法。