---
title: SOLIDWORKS属性管理器页面中的选项卡控件
caption: 选项卡
description: 使用SwEx.PMPage框架在属性管理器页面中创建选项卡控件
image: pmpage-tab.png
toc-group-name: 实验室-SOLIDWORKS-SwEx
order: 3
---
![在属性管理器页面中分组的控件选项卡](pmpage-tab.png)

使用[TabAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_TabAttribute.htm)对复杂类型进行装饰，可以创建选项卡容器。

{% code-snippet { file-name: Tab.* } %}

## 带有嵌套组的选项卡

控件可以直接添加到选项卡中，也可以放置在嵌套组中：

{% code-snippet { file-name: Tab.WithGroup.* } %}