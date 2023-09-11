---
title: Number Box in SOLIDWORKS Property Manager Page
caption: Number Box
description: Overview of options applied to Number Box control
image: number-box-units-wheel.png
toc-group-name: labs-solidworks-swex
order: 6
---
![简单的数字框](number-box.png)

数字框将自动为 *int* 和 *double* 类型的属性创建。

{% code-snippet { file-name: NumberBox.Simple.* } %}

数字框的样式可以通过 [NumberBoxOptionsAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_NumberBoxOptionsAttribute.htm) 进行自定义。

![带有额外样式的数字框，允许指定单位并显示滑轮以更改值](number-box-units-wheel.png)

{% code-snippet { file-name: NumberBox.Style.* } %}