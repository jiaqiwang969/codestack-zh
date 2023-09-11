---
caption: Set Configuration BOM Options
title: Macro to change the Bill Of Materials options (Part Number source and children visibility) of SOLIDWORKS configuration
description: VBA macro which changes the Bill Of Materials part number source (configuration name, document name, parent name) and children display (show, hide, promote) options for all or active configuration in SOLIDWORKS document
image: configuration-options.png
---

这个VBA宏允许更改配置的选项，以便在BOM中进行处理。

* 零件编号来源
    * 配置名称
    * 文档名称
    * 父级名称
* 子组件显示
    * 显示
    * 隐藏
    * 提升

![配置选项属性管理器页面](configuration-options.png)

宏可以处理所有配置或仅活动配置。

通过更改宏的常量来配置宏。

对于**PART_NUMBER_SRC**或**CHILD_COMPS_DISP**选项，指定-1以保留原始值，或指定新值以覆盖。

~~~ vb
Const ALL_CONFIGS As Boolean = True 'True表示处理所有配置，False表示仅处理活动配置
Const PART_NUMBER_SRC As Integer = swBOMPartNumberSource_e.swBOMPartNumber_ConfigurationName '零件编号来源：-1表示保持原样，或者swBOMPartNumberSource_e.swBOMPartNumber_ConfigurationName、swBOMPartNumberSource_e.swBOMPartNumber_DocumentName或swBOMPartNumberSource_e.swBOMPartNumber_ParentName
Const CHILD_COMPS_DISP As Integer = swChildComponentInBOMOption_e.swChildComponent_Promote '在BOM中显示组件：-1表示保持原样，或者swChildComponentInBOMOption_e.swChildComponent_Show、swChildComponentInBOMOption_e.swChildComponent_Hide或swChildComponentInBOMOption_e.swChildComponent_Promote
~~~

{% code-snippet { file-name: Macro.vba } %}