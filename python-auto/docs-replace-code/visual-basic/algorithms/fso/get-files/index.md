---
title: Get files paths from folder using Visual Basic 6 (VBA)
caption: Get Files From Folder
description: Function to get the list of all files in the folder with an option to traverse sub directories and specify the file extension using Visual Basic 6 (VBA)
labels: [files,extension,traverse,recursive]
---
这个函数是使用Visual Basic 6 (VBA)编写的，可以在指定文件夹中查找文件的路径，并可以选择遍历子目录和指定要返回的文件扩展名：

~~~ vb
vFiles = GetFiles("D:\MyFolder") '获取D盘中MyFolder目录及其所有子文件夹中的所有文件
vFiles = GetFiles("D:\MyFolder", False) '仅获取D盘中MyFolder目录中的顶层文件
vFiles = GetFiles("D:\MyFolder", True, "txt") '获取D盘中MyFolder目录中所有以.txt格式的文件
~~~

~~~ vb
Function GetFiles(path As String, Optional includeSubFolders As Boolean = True, Optional ext As String = "") As Variant

    Dim paths() As String
    Dim isInit As Boolean
    
    isInit = False
    
    Dim fso As Object
    Set fso = CreateObject("Scripting.FileSystemObject")
    
    Dim folder As Object
    Set folder = fso.GetFolder(path)
    
    CollectFilesFromFolder folder, includeSubFolders, ext, paths, isInit
    
    If isInit Then
        GetFiles = paths
    Else
        GetFiles = Empty
    End If
    
End Function

Sub CollectFilesFromFolder(folder As Object, includeSubFolders As Boolean, ext As String, ByRef paths() As String, ByRef isInit As Boolean)
    
    For Each file In folder.files
        Dim fileExt As String
        fileExt = Right(file.path, Len(file.path) - InStrRev(file.path, "."))
        If LCase(fileExt) = LCase(ext) Then
            If Not isInit Then
                ReDim paths(0)
                isInit = True
            Else
                ReDim Preserve paths(UBound(paths) + 1)
            End If
            paths(UBound(paths)) = file.path
        End If
    Next
    
    If includeSubFolders Then
        Dim subFolder As Object
        For Each subFolder In folder.SubFolders
            CollectFilesFromFolder subFolder, includeSubFolders, ext, paths, isInit
        Next
    End If
    
End Sub
~~~

