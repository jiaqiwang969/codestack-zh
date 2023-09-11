---
layout: sw-tool
title: SOLIDWORKS VBA macro to copy preselected faces
caption: Copy Surfaces
description: SOLIDWORKS VBA macro to copy selected faces by calling the "Surface Offset" feature with distance 0
image: surface-offset-equal.svg
labels: [surface, geometry, macro, face, solidworks api, vba]
group: Geometry
---
作者：[Eddy Alleman](https://www.linkedin.com/in/eddyalleman/) ([EDAL Solutions](www.edalsolutions.be))

![距离为0的偏移曲面](surface-offset-workflow.png){ width=525 }

此VBA宏在零件文件中从所选面创建一个新的曲面特征，从而复制所选曲面并给其指定的颜色。
如果您想重用现有曲面而不想合并现有曲面，则这将非常有用。

操作步骤

* 必须将零件文件设为活动文档。
* 您必须选择至少一个面。
* 如果选择其他类型的实体，它们将被过滤掉。
* 运行宏。结果将创建一个距离为0的曲面偏移特征。
* 默认情况下，此特征将呈黄色，但您可以更改RGB颜色以设置其他颜色。

作者：[Eddy Alleman](https://www.linkedin.com/in/eddyalleman/) ([EDAL Solutions](https://www.edalsolutions.be/index.php/en/))

~~~ vb
Option Explicit

' INPUT You can change to another RGB color here (This example uses yellow)
Const RED = 255
Const GREEN = 255
Const BLUE = 0

Dim swxApp As SldWorks.SldWorks
Dim swModel As SldWorks.ModelDoc2
Dim selMgr As SldWorks.SelectionMgr

Sub main()

try_:
    On Error GoTo catch_

    Set swxApp = Application.SldWorks
    
    Set swModel = swxApp.ActiveDoc

    'Check if active document is a Part file
    Select Case True
    
           Case swModel Is Nothing, swModel.GetType <> swDocPART
              Call swxApp.SendMsgToUser2("Please open a part file", swMbInformation, swMbOk)
              
           Case Else
               Call ProcessSelectedFaces
               
    End Select

    GoTo finally_:
    
catch_:

    MsgBox Err.Description
    
finally_:
    
End Sub

Private Function ProcessSelectedFaces() As Boolean

    EnableUpdates False
                  
        Set selMgr = swModel.SelectionManager
        
        'Get number of selections
        Dim nSelections As Integer
        nSelections = selMgr.GetSelectedObjectCount2(-1)
               
        'only process if there is something selected
        If nSelections > 0 Then
         
              Call RemoveNonFacesFromSelection

              'Get the number of selected faces
              Dim nFaces As Integer
              nFaces = selMgr.GetSelectedObjectCount2(-1)
        
              If nFaces > 0 Then
              
                  'Offset selected faces
                  swModel.InsertOffsetSurface 0#, False
                  
                  'Give a name to the newly created offset feature
                  Dim featOffset As Feature
                  Set featOffset = swModel.Extension.GetLastFeatureAdded
                    
                  featOffset.Name = featOffset.Name & " Offsets " & nFaces & " Faces"
                  
                  'give the offset feature a color
                  Call SetColor(featOffset)
                     
                  ' Deselect face to see new color
                  swModel.ClearSelection2 True

              End If 'nFaces > 0
      
         End If 'nSelections > 0
        
    EnableUpdates True
    
End Function


Private Function EnableUpdates(update As Boolean)
    With swModel
        .FeatureManager.EnableFeatureTree = update
        .ActiveView.EnableGraphicsUpdate = update
    End With
End Function

'Removes entities that are not faces from the selection manager
Private Function RemoveNonFacesFromSelection()

        'Get number of selections
        Dim nSelections As Integer
        nSelections = selMgr.GetSelectedObjectCount2(-1)
                
        Dim i As Integer
        For i = 0 To nSelections
           
           Dim ObjectType As Long
           ObjectType = selMgr.GetSelectedObjectType3(i, -1)

           If ObjectType <> swSelectType_e.swSelFACES Then
               Dim res As Boolean
               res = selMgr.DeSelect2(i, -1)
           End If
                  
        Next
              
End Function

'Sets the INPUT color on a feature
Private Function SetColor(ByRef Feat As Feature) As Boolean

      'get material properties from model
      Dim MatProp As Variant
      MatProp = swModel.MaterialPropertyValues
                  
      ' set color fi. RGB(225, 255 , 0), but we need them to be in range 0 to 1
      MatProp(0) = RED / 255
      MatProp(1) = GREEN / 255
      MatProp(2) = BLUE / 255
            
      SetColor = Feat.SetMaterialPropertyValues(MatProp)
                  
End Function
~~~

