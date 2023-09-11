---
标题：使用SOLIDWORKS API缩放导入几何体的VBA宏
描述：VBA宏使用指定的缩放因子来缩放外部格式（例如STEP、IGES）的导入特征的实体
图片：imported-feature.png
---
![导入的几何特征](imported-feature.png){ width=250 }

这个VBA宏会缩放活动SOLIDWORKS零件文件中导入特征的所有实体。如果从STEP、IGES、Parasolid等中性格式加载文件，将会生成导入特征，除非使用了3D互连选项。

在**SCALE_FACTOR**常量中设置缩放因子。

{% code-snippet { file-name: Macro.vba } %}