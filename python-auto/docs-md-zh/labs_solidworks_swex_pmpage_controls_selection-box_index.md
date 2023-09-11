---
title: 使用SwEx.PMPage框架在SOLIDWORKS属性页中的选择框控件
caption: 选择框
description: 选择框控件的选项概述
image: selection-box.png
toc-group-name: labs-solidworks-swex
order: 8
---
![选择框控件](selection-box.png)

选择框将为使用[SelectionBoxAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_SelectionBoxAttribute.htm)修饰的公共属性生成。

此属性适用于类型为object或[SolidWorks.Interop.SldWorks](https://help.solidworks.com/2014/english/api/SWHelp_List.html?id=a4a58f35c9bf4504aea25542315877d0#Pg0&ProductType=&ProductName=)命名空间中的任何特定可选择类型的属性。在这种情况下，对象的类型应与[SelectionBoxAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_SelectionBoxAttribute.htm)中指定的类型匹配。

{% code-snippet { file-name: SelectionBox.Single.* } %}

## 多重选择

此属性也适用于列表。在这种情况下，选择框将启用多重选择：

![选择框中选择的多个实体](selection-box-multiple.png)

{% code-snippet { file-name: SelectionBox.List.* } %}

可以通过[SelectionBoxOptionsAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_SelectionBoxOptionsAttribute.htm)指定其他选择框选项。

## 选择标记

选择标记用于区分选择框中的选择。在大多数情况下，每个选择都需要进入特定的选择框。在这种情况下，需要为每个选择框使用不同的选择标记。选择标记是位掩码，这意味着它们应该以2的幂递增（即1、2、4、8、16等）以确保唯一性。默认情况下，SwEx框架将在使用[此](https://docs.codestack.net/swex/pmpage/html/M_CodeStack_SwEx_PMPage_Attributes_SelectionBoxAttribute__ctor.htm)或[此](https://docs.codestack.net/swex/pmpage/html/M_CodeStack_SwEx_PMPage_Attributes_SelectionBoxAttribute__ctor_3.htm)版本的构造函数时负责分配正确的选择标记。但也可以使用[此](https://docs.codestack.net/swex/pmpage/html/M_CodeStack_SwEx_PMPage_Attributes_SelectionBoxAttribute__ctor_1.htm)和[此](https://docs.codestack.net/swex/pmpage/html/M_CodeStack_SwEx_PMPage_Attributes_SelectionBoxAttribute__ctor_2.htm)构造函数手动分配标记。

## 自定义选择过滤器

要为选择框提供自定义过滤逻辑，需要通过继承[SelectionCustomFilter](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Base_SelectionCustomFilter_1.htm)类来实现过滤器，并通过[SelectionBoxAttribute](https://docs.codestack.net/swex/pmpage/html/M_CodeStack_SwEx_PMPage_Attributes_SelectionBoxAttribute__ctor_2.htm)属性的重载构造函数来分配过滤器。

{% code-snippet { file-name: SelectionBox.CustomFilter.* } %}