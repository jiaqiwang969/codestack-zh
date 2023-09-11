标题：使用SOLIDWORKS API向组件添加和读取带参数的属性
标题：向组件添加带参数的属性并读取值
描述：示例通过SOLIDWORKS API接口向所选组件添加带有字符串值的属性作为参数。重新构建模型并通过[IComponent2::FindAttribute](https://help.solidworks.com/2018/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IComponent2~FindAttribute.html)方法找到并读取属性。

属性是可以附加到SOLIDWORKS实体并存储自定义数据的轻量级特性。

![使用SOLIDWORKS API在特征管理器树中创建的两个属性特性](two-attributes-features-tree.png){ width=301 height=320 }

{% code-snippet { file-name: Macro.vba } %}