---
layout: sw-tool
title: 查找并删除SOLIDWORKS图纸中特定注释的宏
caption: 查找并删除注释
description: VBA宏，根据文本、正则表达式或空值，在所有SOLIDWORKS图纸中查找并删除注释
image: delete-note.svg
labels: [注释, 删除, 正则表达式, regex]
group: 图纸
---
此VBA宏允许根据不同的条件（如文本、表达式（与属性关联的文本）、正则表达式或空值）查找并删除SOLIDWORKS图纸中的所有注释。

## 配置

可以通过修改常量来配置宏

~~~ vb
Const FILTER As String = "" '当SEARCH_TYPE设置为ByText或ByExpression时使用的过滤器
Const SEARCH_TYPE As Integer = SearchType_e.EmptyText '搜索类型（ByText、ByExpression、EmptyText、EmptyExpression、All）
Const USE_REGULAR_EXPRESSION As Boolean = False '将FILTER常量中的值视为正则表达式时设置为True
~~~

### 查找所有注释

将**SEARCH_TYPE**常量的值设置为**All**，将找到并删除所有注释。

### 按文本查找

将注释的显示文本的值设置为**FILTER**常量，并将**SEARCH_TYPE**设置为**ByText**，将找到并删除与此值匹配的所有注释。

### 按表达式查找

将注释的表达式（与属性关联的文本）的值设置为**FILTER**常量，并将**SEARCH_TYPE**设置为**ByExpression**，将找到并删除与此值匹配的所有注释。

这可用于查找与自定义属性关联的注释，例如下面的示例将查找与图纸的**零件编号**自定义属性关联的所有注释。

~~~ vb
Const FILTER As String = "$PRPSHEET:""Part Number"""
Const SEARCH_TYPE As Integer = SearchType_e.ByExpression
Const USE_REGULAR_EXPRESSION As Boolean = False
~~~

### 按空文本或表达式查找

将**SEARCH_TYPE**常量的值设置为**EmptyText**或**EmptyExpression**，将找到并删除所有空注释。

### 正则表达式

为了更高级的搜索选项，可以使用正则表达式。要启用此选项，请将**USE_REGULAR_EXPRESSION**设置为**True**。有关更多信息，请参阅[正则表达式](https://docs.microsoft.com/zh-cn/dotnet/standard/base-types/the-regular-expression-object-model)。

下面的示例将查找并删除所有包含数字值的注释。

~~~ vb
Const FILTER As String = "\d+"
Const SEARCH_TYPE As Integer = SearchType_e.ByText
Const USE_REGULAR_EXPRESSION As Boolean = True
~~~

{% code-snippet { file-name: Macro.vba } %}