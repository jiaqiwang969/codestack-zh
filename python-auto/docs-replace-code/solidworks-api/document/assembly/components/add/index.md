---
title: Add components to assembly using SOLIDWORKS API
caption: Add Components To Assembly
description: Example Demonstrates 2 different ways to add component into the assembly tree (single component add or batch adding)
labels: [add component, assembly, example, solidworks api]
redirect-from:
  - /2018/03/solidworks-api-assembly-add-components.html
  - /solidworks-api/document/assembly/add-components
---
该示例演示了使用SOLIDWORKS API将组件添加到装配体树中的两种不同方法。

* 传统的方式是通过[SOLIDWORKS API的AddComponentX](https://help.solidworks.com/2015/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IAssemblyDoc~AddComponent5.html)来添加组件，该方法需要将模型加载到内存中。否则，操作将失败。
* 更高级的方式是使用[SOLIDWORKS API的AddComponents](https://help.solidworks.com/2012/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IAssemblyDoc~AddComponents3.html)。该方法允许在不预先打开模型的情况下批量插入不同的组件。

[下载示例文件](parts.zip)

~~~ vb
Dim swApp As SldWorks.SldWorks
Dim swMathUtils As SldWorks.MathUtility
Dim swAssy As SldWorks.AssemblyDoc

Sub main()

    Set swApp = Application.SldWorks
    
    Set swMathUtils = swApp.GetMathUtility
    
    Set swAssy = swApp.ActiveDoc
    
    If Not swAssy Is Nothing Then
        
        Dim comp1Path As String
        Dim comp2Path As String
        
        comp1Path = swApp.GetCurrentMacroPathFolder() & "\Part1.sldprt"
        comp2Path = swApp.GetCurrentMacroPathFolder() & "\Part2.sldprt"
        
        Dim swComp As SldWorks.Component2
        
        'Following API call will fail as it is required to have the model loaded into the memory
        Set swComp = swAssy.AddComponent4(comp1Path, "", 0, 0, 0)
        
        Debug.Assert Not swComp Is Nothing
                
        'Loading model invisibly
        swApp.DocumentVisible False, swDocumentTypes_e.swDocPART
        swApp.OpenDoc6 comp1Path, swDocumentTypes_e.swDocPART, swOpenDocOptions_e.swOpenDocOptions_Silent, "", 0, 0
        swApp.DocumentVisible True, swDocumentTypes_e.swDocPART
        
        'Now this API call succeeded
        Set swComp = swAssy.AddComponent4(comp1Path, "", 0, 0, 0)
        
        Debug.Assert Not swComp Is Nothing
        
        Dim strCompNames(0) As String
        Dim vTransformData As Variant
        Dim vComps As Variant
        strCompNames(0) = comp2Path
        
        vTransformData = swMathUtils.CreateTransform(Empty).ArrayData
        
        'It is not required to load document into memory if this method is used
        vComps = swAssy.AddComponents(strCompNames, vTransformData)
    
        Debug.Assert UBound(vComps) <> 1
        
    Else
        
        MsgBox "Please open or create assembly"
        
    End If

End Sub


~~~

