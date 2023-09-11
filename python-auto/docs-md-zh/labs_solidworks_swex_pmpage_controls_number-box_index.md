---
标题：SOLIDWORKS 属性管理器页面中的数字框
说明：数字框控件的选项概述
图片：number-box-units-wheel.png
目录组名：实验室-SOLIDWORKS-SWEX
顺序：6
---
![简单的数字框](number-box.png)

数字框将自动为 *int* 和 *double* 类型的属性创建。

{% code-snippet { file-name: NumberBox.Simple.* } %}

数字框的样式可以通过 [NumberBoxOptionsAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_NumberBoxOptionsAttribute.htm) 进行自定义。

![带有额外样式的数字框，允许指定单位并显示滑轮以更改值](number-box-units-wheel.png)

{% code-snippet { file-name: NumberBox.Style.* } %}