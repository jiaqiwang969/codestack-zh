标题：分配标签和管理Property Manager页面控件依赖关系
说明：使用SwEx.PMPage框架分配自定义标签和管理SOLIDWORKS Property Manager页面控件依赖关系（可见性、启用状态等）
图片：cascading-controls.gif
标签：[级联、依赖、标签]
目录组名称：实验室-solidworks-swex
顺序：12

可能需要开发响应式的属性管理器页面，其控件状态取决于其他控件的值，例如[控件启用状态](#controls-enable-state)、[级联列表](#cascading-lists)等。SwEx框架提供了易于设置和使用的功能来实现这些要求，并允许动态更新状态。

为了定义将用于依赖关系的控件，需要分配标签。控件标签允许跟踪从数据模型属性创建的控件。可以通过在数据模型属性上装饰[ControlTagAttribute](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Attributes_ControlTagAttribute.htm)来分配控件标签。控件标签可以表示为任何类型，建议使用枚举或字符串作为标签。

处理程序类必须继承[DependencyHandler](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_Base_DependencyHandler.htm)类，并且每当需要解析状态时（即更改父控件的值时），将调用[UpdateControlState](https://docs.codestack.net/swex/pmpage/html/M_CodeStack_SwEx_PMPage_Base_DependencyHandler_UpdateControlState.htm)方法。

请参阅下面的几个示例，以了解使用此技术开发响应式属性页面的方法。可以实现任何自定义逻辑，并在需要时提供多个父控件。

## 控件启用状态

下面是一个代码示例，演示了如何根据复选框的值禁用/启用选择框控件。

![根据复选框更改控件启用状态](enable-control.gif)

{% code-snippet { file-name: TagsAndDependencies.Enable.* } %}

## 级联列表

下面的代码示例演示了如何实现级联列表。

![在Property Manager页面中级联控件可见性](cascading-controls.gif)

下拉列表中的每个值（通过枚举定义）都有自己的嵌套选项列表（也由另一个枚举定义）。一旦下拉列表的值更改，选项组的可见性也会发生变化。

{% code-snippet { file-name: TagsAndDependencies.CascadingVisibility.* } %}