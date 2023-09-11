---
caption: Toggle Drawing Detailing Mode On Save
title: Save SOLIDWORKS drawing with detailing mode on and off
description: VBA Macro to toggle detailing mode on and off while saving
---
在处理大型绘图时，使用细节模式可能会有益。为了正确使用细节模式，需要将数据保存在文档本身中。

这个过程可能会降低保存性能。

启用或禁用保存细节模式数据的切换选项由文档首选项驱动。

该宏允许打开或关闭设置并执行文档的保存。

~~~ vb
Const ENABLE As Boolean = True 'True表示保存时包含细节数据，False表示保存时不包含细节数据
~~~

可以创建两个宏按钮（一个用于保存包含细节数据，一个用于保存不包含细节数据）。

~~~ vb
Const ENABLE As Boolean = True

Const swCommands_Save As Long = 2

Dim swApp As SldWorks.SldWorks

Sub main()

    Set swApp = Application.SldWorks
    
    Dim swModel As SldWorks.ModelDoc2
    
    Set swModel = swApp.ActiveDoc
    
    If Not swModel Is Nothing Then
        
        If swModel.GetType() = swDocumentTypes_e.swDocDRAWING Then
            Dim saveModelDataOpt As Boolean
            Dim includeStandardView As Boolean
            
            saveModelDataOpt = swModel.Extension.GetUserPreferenceToggle(swUserPreferenceToggle_e.swDetailingModeSaveModelData, swUserPreferenceOption_e.swDetailingNoOptionSpecified)
            includeStandardView = swModel.Extension.GetUserPreferenceToggle(swUserPreferenceToggle_e.swDetailingModeIncludeStandardViewsInViewPalette, swUserPreferenceOption_e.swDetailingNoOptionSpecified)
            
            swModel.Extension.SetUserPreferenceToggle swUserPreferenceToggle_e.swDetailingModeSaveModelData, swUserPreferenceOption_e.swDetailingNoOptionSpecified, ENABLE
            swModel.Extension.SetUserPreferenceToggle swUserPreferenceToggle_e.swDetailingModeIncludeStandardViewsInViewPalette, swUserPreferenceOption_e.swDetailingNoOptionSpecified, ENABLE
            
            swApp.RunCommand swCommands_Save, ""
            
            swModel.Extension.SetUserPreferenceToggle swUserPreferenceToggle_e.swDetailingModeSaveModelData, swUserPreferenceOption_e.swDetailingNoOptionSpecified, saveModelDataOpt
            swModel.Extension.SetUserPreferenceToggle swUserPreferenceToggle_e.swDetailingModeIncludeStandardViewsInViewPalette, swUserPreferenceOption_e.swDetailingNoOptionSpecified, includeStandardView
        Else
            Err.Raise vbError, "", "Only drawing documents are supported"
        End If
    Else
        Err.Raise vbError, "", "Open drawing document"
    End If
    
End Sub
~~~

