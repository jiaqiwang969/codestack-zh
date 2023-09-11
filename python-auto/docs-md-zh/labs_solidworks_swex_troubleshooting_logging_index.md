标题：SOLIDWORKS插件中SwEx框架的日志功能
说明：从SwEx模块中记录调试信息的日志
标签：[日志]
目录组名称：实验室-SOLIDWORKS-SwEx

所有基本的SwEx模块都继承了[IModule](https://docs.codestack.net/swex/common/html/T_CodeStack_SwEx_Common_Base_IModule.htm)接口，该接口提供了对[ILogger](https://docs.codestack.net/swex/common/html/T_CodeStack_SwEx_Common_Diagnostics_ILogger.htm)实例的访问，允许从模块中记录自定义消息和异常。

以下模块提供了日志记录器：

- [SwAddInEx](https://docs.codestack.net/swex/add-in/html/T_CodeStack_SwEx_AddIn_SwAddInEx.htm)
- [MacroFeatureEx](https://docs.codestack.net/swex/macro-feature/html/T_CodeStack_SwEx_MacroFeature_MacroFeatureEx.htm)
- [PropertyManagerPageEx](https://docs.codestack.net/swex/pmpage/html/T_CodeStack_SwEx_PMPage_PropertyManagerPageEx_2.htm)

可以通过使用[LoggerOptionsAttribute](https://docs.codestack.net/swex/common/html/M_CodeStack_SwEx_Common_Attributes_LoggerOptionsAttribute__ctor.htm)修饰模块类来指定其他选项。

{% code-snippet { file-name: LogAddIn.* } %}

指定的日志记录器名称将附加到SwEx模块名称之后（例如SwEx.AddIn.MyAddInLog或SwEx.MacroFeature.MyAddInLog或SwEx.PMPage.MyAddInLog）。

日志消息将按照[LoggerOptionsAttribute](https://docs.codestack.net/swex/common/html/M_CodeStack_SwEx_Common_Attributes_LoggerOptionsAttribute__ctor.htm)属性设置的方式输出到输出中。目前仅支持调试跟踪日志记录器。请参考[Troubleshooting](/labs/solidworks/swex/troubleshooting/)文章了解如何捕获调试跟踪消息的说明。