---
布局：sw-tool
标题：将SOLIDWORKS组件的路径复制到剪贴板的宏
标题：复制组件路径
描述：使用SOLIDWORKS API，该宏将所选组件在装配或绘图中的路径复制到剪贴板
图片：copy-component-path.png
标签：[路径，剪贴板，组件]
组：装配
---
![在特征树中选择的组件](selected-component.png){ width=250 }

该宏使用SOLIDWORKS API将所选组件的完整路径复制到剪贴板。

* 组件可以在装配或绘图文档中选择
* 组件可以在特征树或图形区域中选择
    * 还可以选择组件实体（例如面或边）以获取组件的路径

{% code-snippet { file-name: Macro.vba } %}