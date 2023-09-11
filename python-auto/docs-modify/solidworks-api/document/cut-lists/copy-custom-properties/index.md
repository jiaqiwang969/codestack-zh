---
layout: sw-tool
title: Macro to copy SOLIDWORKS custom properties from cut-list to model
caption: Copy Cut-List Custom Properties To Model
description: VBA macro to copy SOLIDWORKS custom properties from cut-list (sheet metal or weldment) to model or configuration
image: copy-cutlist-properties.svg
labels: [cut-list,sheet metal,properties]
group: Custom Properties
---
此VBA宏将指定或所有SOLIDWORKS切割清单项的自定义属性复制到模型或配置。

将复制第一个找到的切割清单的属性。

{% code-snippet { file-name: Macro.vba } %}

## 配置

可以通过更改常量来配置宏

### 属性范围

*CONF_SPEC_PRP* 常量设置目标属性的范围。

* True：将属性复制到配置特定选项卡
* False：将属性复制到自定义选项卡

### 属性来源

*COPY_RES_VAL* 常量设置属性来源

* True：复制解析值

![已复制的解析值到自定义属性](copied-property-values.png) { width=500 }

* False：复制表达式

![已复制的表达式到自定义属性](copied-expressions.png) { width=500 }

### 属性列表

*PROPERTIES* 数组包含要复制的属性列表

复制指定的属性

~~~ vb
Sub Init(Optional dummy As Variant = Empty)
    PROPERTIES = Array("属性1", "属性2", "属性3") '复制属性1、属性2、属性3
End Sub
~~~

复制所有属性

~~~ vb
Sub Init(Optional dummy As Variant = Empty)
    PROPERTIES = Empty
End Sub
~~~