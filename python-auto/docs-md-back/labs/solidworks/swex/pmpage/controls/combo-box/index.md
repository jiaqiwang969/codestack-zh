---
title: Combo Box control in SOLIDWORKS property Manager Page
caption: Combo Box
description: Overview of options applied to Combo Box control
image: combobox.png
toc-group-name: labs-solidworks-swex
order: 7
---

![带有3个选项的组合框控件](combobox.png)

组合框控件将自动为所有枚举类型的属性生成。枚举器的所有值将被视为组合框中的选项：

{% code-snippet { file-name: ComboBox.Simple.* } %}

可以通过[ComboBoxOptionsAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_ComboBoxOptionsAttribute.htm)来指定组合框控件的附加选项和样式。

### 项目文本
可以使用[ComboBoxItemTextAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_ComboBoxItemTextAttribute.htm)属性来指定在组合框中显示的用户友好标题。

{% code-snippet { file-name: ComboBox.ItemsText.* } %}