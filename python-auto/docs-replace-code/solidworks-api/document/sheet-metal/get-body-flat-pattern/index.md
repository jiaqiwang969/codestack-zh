---
title: Find cut-list item from the sheet metal flat pattern using SOLIDWORKS API
caption: Get Cut List Item From Flat Pattern
description: VBA macro which finds the pointer to the cut-list feature from the selected flat pattern feature
image: cut-list-folder-flat-pattern.png
labels: [sheet metal, cut-list, flat pattern]
---
![切割清单文件夹和展开图案特征](cut-list-folder-flat-pattern.png){ width=200 }

这个VBA宏演示了如何从选定的钣金展开图案特征中找到相应的切割清单文件夹特征。

该宏支持钣金特征的展平和取消展平状态。

~~~ vb
Dim swApp As SldWorks.SldWorks
Dim swModel As SldWorks.ModelDoc2

Sub main()

    Set swApp = Application.SldWorks
    
    Set swModel = swApp.ActiveDoc
    
    Dim swFeat As SldWorks.Feature
    
    Set swFeat = swModel.SelectionManager.GetSelectedObject6(1, -1)
    
    If Not swFeat Is Nothing Then
    
        If swFeat.GetTypeName2 = "FlatPattern" Then
                    
            Dim swFlatPattern As SldWorks.FlatPatternFeatureData
            Set swFlatPattern = swFeat.GetDefinition
            
            Dim swFixedFace As SldWorks.Face2
            Set swFixedFace = swFlatPattern.FixedFace2
            
            Dim swBody As SldWorks.Body2
            Set swBody = swFixedFace.GetBody
            
            Dim swCutListFeat As SldWorks.Feature
            
            Set swCutListFeat = GetCutListFromBody(swModel, swBody)
            
            Debug.Print swCutListFeat.Name
            
        Else
            Err.Raise vbError, "", "Selected feature is not sheet metal flat pattern"
        End If
    
    Else
        Err.Raise vbError, "", "Select feature"
    End If
    
End Sub

Function GetCutListFromBody(model As SldWorks.ModelDoc2, body As SldWorks.Body2) As SldWorks.Feature
    
    Dim swFeat As SldWorks.Feature
    Dim swBodyFolder As SldWorks.BodyFolder
    
    Set swFeat = model.FirstFeature
    
    Do While Not swFeat Is Nothing
        
        If swFeat.GetTypeName2 = "CutListFolder" Then
            
            Set swBodyFolder = swFeat.GetSpecificFeature2
            
            Dim vBodies As Variant
            
            vBodies = swBodyFolder.GetBodies
            
            Dim i As Integer
            
            If Not IsEmpty(vBodies) Then
                For i = 0 To UBound(vBodies)
                    
                    Dim swCutListBody As SldWorks.Body2
                    Set swCutListBody = vBodies(i)
                    
                    If swApp.IsSame(swCutListBody, body) = swObjectEquality.swObjectSame Then
                        Set GetCutListFromBody = swFeat
                        Exit Function
                    End If
                    
                Next
            End If
            
        End If
        
        Set swFeat = swFeat.GetNextFeature
        
    Loop

End Function
~~~

