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

{% code-snippet { file-name: GetFilesFromFolder.vba } %}