---
title: Sorting data in Visual Basic 6 (VBA)
caption: Sorting
description: Code example of various method of sorting data in Visual Basic 6 (VBA)
labels: [sort,bubble,logical]
---
## 逻辑冒泡排序

[逻辑排序](https://en.wikipedia.org/wiki/Natural_sort_order)是一种字母排序，除了多位数值以单个数字排序外。

例如，按字母顺序排序时，以下逻辑顺序ab1、ab2、ab3、ab12与ab1、ab12、ab2、ab3不同。当文件在文件资源管理器中排序时，使用逻辑顺序。

以下示例使用[冒泡排序](https://en.wikipedia.org/wiki/Bubble_sort)技术按逻辑顺序对指定的字符串数组进行排序。

*asc*参数指定值是按升序还是降序排序：

~~~ vb
Dim vSortedArr As Variant
Dim vInputArr as Variant '字符串数组
vSortedArr = BubbleSort(vInputArr, False) '按降序排序
~~~

~~~ vb
Declare PtrSafe Function StrCmpLogicalW Lib "shlwapi" (ByVal s1 As String, ByVal s2 As String) As Integer

Function BubbleSort(vStrArray As Variant, asc As Boolean) As Variant
    
    Dim swapPos As Integer
    swapPos = IIf(asc, 1, -1)
    
    Dim vResStrArray As Variant
    vResStrArray = vStrArray
    
    Dim i As Integer
    Dim j As Integer
    Dim tempVal As String
    
    For i = 0 To UBound(vResStrArray)
        For j = i To UBound(vResStrArray)
            If StrCmpLogicalW(StrConv(CStr(vResStrArray(i)), vbUnicode), StrConv(CStr(vResStrArray(j)), vbUnicode)) = swapPos Then
                tempVal = vResStrArray(j)
                vResStrArray(j) = vResStrArray(i)
                vResStrArray(i) = tempVal
            End If
        Next
    Next
    
    BubbleSort = vResStrArray
    
End Function
~~~

