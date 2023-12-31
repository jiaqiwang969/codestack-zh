---
title: Create rotational transformation of circular pattern via SOLIDWORKS API
caption: Create A Rotational Transformation Based On Circular Pattern Data
description: Example reads the transform of the selected circular pattern and creates a temp preview of the pattern of the specified seed body by applying the same transform as in the circular pattern
image: circ-pattern-emulator.png
labels: [angle, axis, circular pattern, example, geometry, instances, rotation, transform]
redirect-from:
  - /2018/03/create-rotational-transformation-based.html
---
This SOLIDWORKS API example reads the transform of the selected circular pattern and creates a temp preview of the pattern of the specified seed body by applying the same transform as in the circular pattern.

![Copy of the body created emulating the circular pattern feature](circ-pattern-emulator.png){ width=640 height=304 }

* Select circular pattern feature as a first selected object
  * It must use reference axis as the directionSelect any solid body which is not a part of the circular pattern feature
* Run the macro. Macro will read the transformation from the pattern and apply the same transformation to the body selected in previous step.
The preview will be displayed using temporarily bodies which will be destroyed immediately when macro resumes execution (i.e. F5 or run).
* There won't be any temp features created or removed during the run of this macro

~~~ vb
Dim swApp As SldWorks.SldWorks
Dim swModel As SldWorks.ModelDoc2
Dim swMathUtils As SldWorks.MathUtility
Dim swSelMgr As SldWorks.SelectionMgr

Sub main()

    Set swApp = Application.SldWorks
    
    Set swModel = swApp.ActiveDoc
    
    Set swMathUtils = swApp.GetMathUtility
    
    Set swSelMgr = swModel.SelectionManager
    
    Dim swFeat As SldWorks.Feature
    Dim swBody As SldWorks.Body2
    Dim swCircPatt As SldWorks.CircularPatternFeatureData
    
    Set swFeat = swSelMgr.GetSelectedObject6(1, -1)
    
    If Not swFeat Is Nothing Then
        If swFeat.GetTypeName2 = "CirPattern" Then
            Set swCircPatt = swFeat.GetDefinition
        End If
    End If
    
    Set swBody = swSelMgr.GetSelectedObject6(2, -1)
    
    If swBody Is Nothing Then
        MsgBox "Please select body to pattern as second selection"
        End
    End If
    
    If Not swCircPatt Is Nothing Then
                
        Dim angle As Double
        Dim swOrigPt As SldWorks.MathPoint
        Dim swDirVec As SldWorks.MathVector
        Dim instances As Integer
        Dim vPreviewBodies As Variant
        
        GetCircularPatternParameters swCircPatt, swOrigPt, swDirVec, angle, instances
        
        vPreviewBodies = CreateCircularPatternPreview(swBody, swOrigPt, swDirVec, angle, instances)
        
        Stop
        
        ClearTempBodies vPreviewBodies
        
    Else
        MsgBox "Please select the circular pattern feature as first selection"
    End If
    
End Sub

Sub GetCircularPatternParameters(swCircPatt As SldWorks.CircularPatternFeatureData, ByRef swOrigPt As MathPoint, ByRef swDirVec As MathVector, ByRef angle As Double, ByRef instances As Integer)
    
    swCircPatt.AccessSelections swModel, Nothing
    
    If swCircPatt.EqualSpacing Then
        angle = swCircPatt.Spacing / (swCircPatt.TotalInstances - 1)
    Else
        angle = swCircPatt.Spacing
    End If
    
    If swCircPatt.ReverseDirection Then
        angle = -angle
    End If
    
    instances = swCircPatt.TotalInstances - 2
    
    Dim swAxis As SldWorks.RefAxis
    Set swAxis = swCircPatt.Axis
        
    If swAxis Is Nothing Then
        MsgBox "Only reference axis is supported as the direction"
        End
    End If
    
    Dim vVec As Variant
    vVec = swAxis.GetRefAxisParams
    
    Dim dData(2) As Double
    
    dData(0) = vVec(0):  dData(1) = vVec(1): dData(2) = vVec(2)
    Set swOrigPt = swMathUtils.CreatePoint(dData)
    
    dData(0) = vVec(3) - vVec(0):  dData(1) = vVec(4) - vVec(1): dData(2) = vVec(5) - vVec(2)
    Set swDirVec = swMathUtils.CreateVector(dData)
    
    swCircPatt.ReleaseSelectionAccess
    
End Sub

Function CreateCircularPatternPreview(swBody As SldWorks.Body2, swOrigPt As MathPoint, swDirVec As MathVector, angle As Double, instances As Integer) As Variant
    
    Dim swPreviewBodies() As SldWorks.Body2
    ReDim swPreviewBodies(instances)
    
    Dim i As Integer
    
    For i = 0 To instances
        
        Dim swTransform As SldWorks.MathTransform

        Set swTransform = swMathUtils.CreateTransformRotateAxis(swOrigPt, swDirVec, angle * (i + 1))
        
        Set swPreviewBodies(i) = swBody.Copy
        
        swPreviewBodies(i).ApplyTransform swTransform
        
        swPreviewBodies(i).Display3 swModel, RGB(0, 0, 255), swTempBodySelectOptions_e.swTempBodySelectOptionNone
        
    Next
    
    CreateCircularPatternPreview = swPreviewBodies
        
End Function

Sub ClearTempBodies(vBodies As Variant)
    
    Dim i As Integer

    For i = 0 To UBound(vBodies)
        Set vBodies(i) = Nothing
    Next
    
End Sub
~~~


