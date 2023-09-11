---
caption: 链接到钣金切割清单属性
title: 将钣金切割清单属性链接到SOLIDWORKS零件自定义属性的宏
description: VBA宏，可在指定的钣金零件的切割清单属性和文件自定义属性之间添加永久链接（表达式），并可选择添加备用值
image: linked-sheet-metal-cut-list-properties.png
---
![链接的钣金切割清单自定义属性](linked-sheet-metal-cut-list-properties.png){ width=800 }

这个VBA宏允许将指定的切割清单自定义属性从钣金零件链接到SOLIDWORKS文件的自定义属性。

自定义属性将通过公式进行链接，并且如果钣金的几何形状发生变化，它们将自动更新。

可以指定一个备用值，如果源零件不是钣金文档，则将写入自定义属性。

为了自定义属性映射，请在下面的**Init**函数中添加或删除映射值，如下所示。

在最后一个参数（**备用值**）中指定表达式时，需要用其他**"**（引号）转义**"**（引号）。例如，SOLIDWORKS质量的公式是**"SW-Mass"**，如果需要将其设置为备用值，则第三个参数应为**"""SW-Mass"""**，其中外部引号是表示[VBA字符串值](/visual-basic/variables/standard-types#string)的引号。

~~~ vb
Sub Init(Optional dummy As Variant = Empty)
    
    Set Map = New Collection
    
    Map.Add CreateMapValue("零件编号", "", "") '添加空的“零件编号”自定义属性
    Map.Add CreateMapValue("宽度", "包围盒宽度", "") '从钣金的“包围盒宽度”添加自定义属性“宽度”，如果不是钣金零件，则为空
    Map.Add CreateMapValue("材料", "", """SW-Material""") '添加自定义属性“材料”，并将其设置为“SW-Material”公式，无论是否为钣金零件
        
End Sub
~~~

## 注意事项和限制

* 仅支持单个切割清单文件（如果有多个切割清单，则会引发错误）
* 宏将在切割清单文件夹上设置**自动创建切割清单**和**自动更新**选项
* 仅支持零件文档
* 切割清单自定义属性通过表达式和切割清单名称进行链接。如果更改了切割清单的名称，属性将不会更新，需要重新运行宏。但是，如果切割清单保持原始名称，所有属性将动态更新，无需重新运行宏。

{% code-snippet { file-name: Macro.vba } %}