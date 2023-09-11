---
title: Handling the long operation progress using progress bar in SOLIDWORKS API
caption: User Progress Bar
description: Displaying the long operation progress using user progress bar in SOLIDWORKS API
image: taskbar-progress.png
labels: [progress,user progress bar,background]
---
为了改善宏或插件的用户体验，建议在执行长时间的SOLIDWORKS API操作时显示和更新进度条。

SOLIDWORKS API提供了一种内置方法，在主线程被锁定时（即在进程中执行操作）显示进度。进度值和消息可以通过[SOLIDWORKS API接口](https://help.solidworks.com/2017/English/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IUserProgressBar.html)的[IUserProgressBar](https://help.solidworks.com/2017/English/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IUserProgressBar.html)接口来处理。

消息和进度显示在应用程序左下角的标准SOLIDWORKS进度条中。

![进度和消息显示在进度条中](user-progress-bar.png)

进度也会反映在任务栏中的SOLIDWORKS图标中。

![进度显示在任务栏中的SOLIDWORKS图标中](taskbar-progress.png)

## 注意事项和限制

* 进度值和消息可以被SOLIDWORKS的标准进度消息覆盖（例如重建操作、文件加载等）。

## 运行宏

* 打开带有实体的零件文档
* 宏遍历每个实体的所有面，并对每个面执行数据提取操作
* 操作按照*ITERATIONS_COUNT*常量指定的次数重复
* 显示进度条
* 按ESC键可以选择取消操作

~~~ vb
Const ITERATIONS_COUNT As Integer = 1000

Dim swApp As SldWorks.SldWorks

Sub main()

    Set swApp = Application.SldWorks
    
    Dim swModel As SldWorks.ModelDoc2
    
    Set swModel = swApp.ActiveDoc
    
    If TypeOf swModel Is SldWorks.PartDoc Then
        
        Dim swPart As SldWorks.PartDoc
        Set swPart = swModel
        Dim vBodies As Variant
        vBodies = swPart.GetBodies2(swBodyType_e.swAllBodies, False)
            
        If Not IsEmpty(vBodies) Then
            PerformOperation vBodies
        Else
            MsgBox "There are no bodies in this part"
        End If
            
    Else
        MsgBox "Please open part document"
    End If
    
End Sub

Sub PerformOperation(bodies As Variant)
    
    Dim swPrgBar As SldWorks.UserProgressBar
    swApp.GetUserProgressBar swPrgBar
    
    swPrgBar.Start 0, GetProgressBarUpperBound(bodies), "Performing operations on faces"
    
    Dim i As Integer
    
    Dim pos As Long
    pos = 0
    
    For i = 0 To UBound(bodies)
        
        Dim swBody As SldWorks.Body2
        Set swBody = bodies(i)
        
        Dim vFaces As Variant
        vFaces = swBody.GetFaces()
        
        swPrgBar.UpdateTitle "Processing " & swBody.Name & " with " & UBound(vFaces) + 1 & " face(s)"
        
        Dim j As Integer
        
        For j = 0 To UBound(vFaces)
            
            Dim k As Integer
            
            For k = 0 To ITERATIONS_COUNT
                
                pos = pos + 1
                
                Dim swFace As SldWorks.Face2
                Set swFace = vFaces(j)
                
                Dim swSurf As SldWorks.Surface
                Set swSurf = swFace.GetSurface()
                    
                swSurf.EvaluateAtPoint 0, 0, 0
                swSurf.GetClosestPointOn 0, 0, 0
                
                If swUpdateProgressError_e.swUpdateProgressError_UserCancel = swPrgBar.UpdateProgress(pos) Then
                    If swApp.SendMsgToUser2("Cancel operation?", swMessageBoxIcon_e.swMbWarning, swMessageBoxBtn_e.swMbYesNo) = swMessageBoxResult_e.swMbHitYes Then
                        swPrgBar.End
                    End If
                End If
                
            Next
        Next
        
    Next
    
End Sub

Function GetProgressBarUpperBound(bodies As Variant) As Long
    
    Dim totalFaceCount As Long
    
    Dim i As Integer
    
    For i = 0 To UBound(bodies)
        Dim swBody As SldWorks.Body2
        Set swBody = bodies(i)
        totalFaceCount = swBody.GetFaceCount()
    Next
    
    GetProgressBarUpperBound = totalFaceCount * ITERATIONS_COUNT
    
End Function
~~~

