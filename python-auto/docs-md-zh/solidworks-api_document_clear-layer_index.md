---
布局：sw-tool
标题：清除图层
说明：在SOLIDWORKS模型中删除图层中的所有项目（注释、草图线段、块等）的VBA宏
图片：remove-layer-items.svg
分组：模型
---
![SOLIDWORKS图层](solidworks-layers.png)

此VBA宏会收集并删除指定图层上的所有项目（注释、草图线段、块、草图点和填充）。图层本身不会被删除。

在**LAYER_NAME**常量中设置图层的名称。

{% code-snippet { file-name: Macro.vba } %}