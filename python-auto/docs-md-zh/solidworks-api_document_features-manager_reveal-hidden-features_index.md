---
layout: sw-tool
title: 显示或删除在SOLIDWORKS特征管理器树中隐藏的所有特征
caption: 显示隐藏特征
description: 该宏可查找SOLIDWORKS模型中所有隐藏的特征，并显示或删除它们
image: hidden-feature.svg
labels: [defeature,parasolid]
group: 性能
---
![隐藏特征](hidden-feature.svg){ width=250 }

这个VBA宏可以帮助显示在活动的SOLIDWORKS模型中特征管理器树中隐藏的所有特征。

SOLIDWORKS文件中的特征可能会因为各种原因而被隐藏。在某些情况下，这些特征可能是无效的或者悬空的。这可能会导致SOLIDWORKS的行为不可预测，包括性能问题或不稳定，如崩溃或卡顿。

* 创建一个新的宏，并将[模块代码](#macro-module)粘贴到宏中
* 将一个新的[用户窗体](/visual-basic/user-forms/)添加到宏中，并将其命名为*FeaturesForm*，然后将[代码](#featuresform-user-form)粘贴进去。宏的结构应该类似于下面的图片

![宏项目树](project-tree.png)

* 向窗体添加控件，并按照下面的图片进行命名。可选择为控件指定更多属性，如标题。

    * 名为*lstFeatures*的列表框
    * 名为*btnShow*的按钮
    * 名为*btnDelete*的按钮

![带有控件的窗体](hidden-features-form.png)

运行宏后，所有隐藏的特征将会显示在列表中。在列表中选择（或多选）特征，然后点击*Show*或*Delete*按钮来显示或删除模型中的特征。

![在特征管理器树中显示的隐藏特征](displayed-hidden-feature.png)

> !重要提示：使用删除选项要自担风险。在某些情况下，隐藏的特征是由SOLIDWORKS或第三方应用程序创建的有效特征。例如，[属性](/solidworks-api/data-storage/attributes/)可以被创建为隐藏特征，并且可能包含重要信息。删除这些特征可能会导致意外结果。

要隐藏特征，请使用[以下宏](/solidworks-api/document/features-manager/hide-features/)宏。

## 宏模块

{% code-snippet { file-name: Macro.vba } %}

## FeaturesForm 用户窗体

{% code-snippet { file-name: FeaturesForm.vba } %}