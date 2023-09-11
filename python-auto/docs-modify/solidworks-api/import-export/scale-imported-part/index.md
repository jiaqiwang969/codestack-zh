---
caption: Scale Imported Geometry
title: VBA macro to scale the geometry of the imported features using SOLIDWORKS API
description: VBA macro scales the bodies from the imported features of the foreign formats (e.g. STEP, IGES) with the specified scale factor
image: imported-feature.png
---
![导入的几何图形特征](imported-feature.png){ width=250 }

这个VBA宏会缩放活动SOLIDWORKS零件文件中导入特征的所有实体。如果从STEP、IGES、Parasolid等中性格式加载文件，将会生成导入特征，除非使用了3D互连选项。

在**SCALE_FACTOR**常量中设置缩放因子。

{% code-snippet { file-name: Macro.vba } %}