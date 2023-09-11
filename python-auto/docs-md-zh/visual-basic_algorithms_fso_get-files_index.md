---
title: 使用Visual Basic 6 (VBA)从文件夹获取文件路径
caption: 从文件夹获取文件
description: 使用Visual Basic 6 (VBA)编写的函数，可以获取指定文件夹中所有文件的路径，并可以选择遍历子目录和指定文件扩展名。
labels: [文件,扩展名,遍历,递归]
---
这个函数是使用Visual Basic 6 (VBA)编写的，可以在指定文件夹中查找文件的路径，并可以选择遍历子目录和指定要返回的文件扩展名：

~~~ vb
vFiles = GetFiles("D:\MyFolder") '获取D盘中MyFolder目录及其所有子文件夹中的所有文件
vFiles = GetFiles("D:\MyFolder", False) '仅获取D盘中MyFolder目录中的顶层文件
vFiles = GetFiles("D:\MyFolder", True, "txt") '获取D盘中MyFolder目录中所有以.txt格式的文件
~~~

{% code-snippet { file-name: GetFilesFromFolder.vba } %}