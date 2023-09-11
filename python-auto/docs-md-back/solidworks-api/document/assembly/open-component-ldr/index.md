---
layout: sw-tool
title: Open selected components in the Large Design Review (LDR) mode
caption: Open components in LDR mode
description: VBA macro to open all selected sub-assemblies and part components in the Large Design Review (LDR) mode and view only mode correspondingly
image: ldr-sub-assembly.svg
labels: [performance, ldr, view only, large design review, open]
group: Assembly
---
这个VBA宏可以在以大型设计审查（LDR）模式打开的装配或以详细模式打开的图纸中运行。宏将以它们自己的窗口打开所有选定的组件，但与开箱即用的功能不同，装配将不会被解析，并且将保留LDR模式。

![选定的子装配组件](selected-sub-assemblies.png)

然后可以在LDR模式下启用编辑，修改装配并更新顶层装配中的图形。

在所有步骤中保留LDR模式将显著提高性能。

## 图纸

这个宏也可以在以详细模式打开的图纸中工作。在运行宏之前，需要选择图纸视图。

![选定的图纸视图](selected-drawing-view.png)

要启用图纸支持，需要在宏中启用文档管理器API。请按照[激活文档管理器](/solidworks-document-manager-api/getting-started/create-connection#activating-document-manager)部分的详细步骤来请求文档管理器许可证密钥。

在VBA编辑器的**工具->引用**菜单下添加对**SwDocumentMgr [Year] Type Library**的引用。请参考[在VBA中使用文档管理器](/solidworks-document-manager-api/getting-started/create-connection#vba)获取更多信息。

![文档管理器引用](swdm-reference.png)

在**DM_LIC_KEY**变量中设置许可证密钥。请注意，此宏只需要密钥的**swdocmgr_general**部分。以下格式足够使用。

~~~ vb
Const DM_LIC_KEY As String = "[CompanyName]:swdocmgr_general-00000-{31 times}"
~~~

如果宏只会从装配中使用，则不需要此过程。

## 注意事项和限制

* 子装配组件将以大型设计审查模式打开，而零件组件将以仅查看模式打开
* 如果目标零件或装配没有存储显示数据，将会抛出错误
* 组件必须从特征管理器树中选择。在图形区域选择的实体将被忽略
* 此VBA宏使用了[用于引用文档的搜索例程](https://help.solidworks.com/2016/english/SolidWorks/sldworks/c_Search_Routine_for_Referenced_Documents.htm)的简化版本，并且仅在回退到组件的缓存路径之前检查活动装配的文件夹和子文件夹。在某些情况下，这可能导致加载不正确的引用（例如，如果使用了搜索文件夹）。但这只适用于被复制并且缓存文件路径从未更新的装配。

### 引用的配置

此宏将尝试以组件的引用配置打开装配，但默认情况下，SOLIDWORKS仅在活动配置中存储显示数据，除非配置标记为“显示数据标记”。

![在配置中添加显示数据标记](add-display-data-mark.png){ width=250 }

如果组件的引用配置未标记为上述标记，并且它不是活动配置，则无法在大型设计审查中加载它。在这种情况下，宏将加载默认配置并显示下面的警告，指示加载了不同配置的图形。

![无效配置的错误](configuration-error.png)

{% code-snippet { file-name: Macro.vba } %}