---
title: Browse for folder in VBA macro
caption: Browse For Folder
description: Code snippet to select the folder path in VBA macro
---
以下代码片段演示了如何在VBA宏中浏览文件夹路径。同样的功能也可以在VBScript中使用。

~~~ vb
Sub main()

    Debug.Print BrowseForFolder("Browse for folder")
        
End Sub

Function BrowseForFolder(Optional title As String = "Select Folder") As String
    
    Dim shellApp As Object
    
    Set shellApp = CreateObject("Shell.Application")
    
    Dim folder As Object
    Set folder = shellApp.BrowseForFolder(0, title, 0)
    
    If Not folder Is Nothing Then
        BrowseForFolder = folder.Self.Path
    End If
    
End Function
~~~

