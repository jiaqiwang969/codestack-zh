---
标题：使用SOLIDWORKS API修改轴特征定义
说明：使用SOLIDWORKS API修改轴特征选择的VBA宏示例
图片：axis-definition.png
标签：[轴,定义]
---

![轴属性管理器页面](axis-definition.png){ width=250 }

这个VBA示例演示了如何使用SOLIDWORKS API修改轴特征的定义并更改选择。

* 首先选择要修改的目标轴特征
* 选择要设置为目标轴参考的对象，例如两个相交的平面、边等。

结果是所选对象（倒数第二个）将被分配给轴（第一个选择）。

{% code-snippet { file-name: Macro.vba } %}