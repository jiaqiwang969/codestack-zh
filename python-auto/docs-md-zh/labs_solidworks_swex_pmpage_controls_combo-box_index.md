---
标题：SOLIDWORKS属性管理器页面中的组合框控件
说明：组合框控件的选项概述
图片：combobox.png
目录组名：实验室-SOLIDWORKS-SWEX
顺序：7
---

![带有3个选项的组合框控件](combobox.png)

组合框控件将自动为所有枚举类型的属性生成。枚举器的所有值将被视为组合框中的选项：

{% code-snippet { file-name: ComboBox.Simple.* } %}

可以通过[ComboBoxOptionsAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_ComboBoxOptionsAttribute.htm)来指定组合框控件的附加选项和样式。

### 项目文本
可以使用[ComboBoxItemTextAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_ComboBoxItemTextAttribute.htm)属性来指定在组合框中显示的用户友好标题。

{% code-snippet { file-name: ComboBox.ItemsText.* } %}