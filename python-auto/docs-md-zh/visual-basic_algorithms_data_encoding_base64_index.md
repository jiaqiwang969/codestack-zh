---
title: 在Visual Basic 6 (VBA)中以Base64字符串格式编码和解码数据
caption: Base64字符串
description: 在Visual Basic 6 (VBA)中将字节数组编码和解码为Base64字符串格式
labels: [base64,编码,解码]
---
Base64字符串可以将字节数组数据以字符串格式保存。

## 编码

~~~vb
Dim arr(5) As Byte
arr(0) = 1: arr(1) = 5: arr(2) = 2
arr(3) = 21: arr(4) = 101: arr(5) = 51

Dim base64Str As String
base64Str = ConvertToBase64String(arr) 'AQUCFWUz
~~~

{% code-snippet { file-name: encode-base64.vba } %}

## 解码

~~~vb
Dim base64Str As String
base64Str = "AQUCFWUz"

dim vArr As Variant
vArr = Base64ToArray(base64Str) '字节数组: 1, 5, 2, 21, 101, 51
~~~

{% code-snippet { file-name: decode-base64.vba } %}