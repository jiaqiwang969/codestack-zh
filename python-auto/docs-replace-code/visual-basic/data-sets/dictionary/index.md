---
title: Dictionary in Visual Basic
caption: Dictionary
description: Explanation of using Dictionary object to store key-value pairs in Visual Basic
image: dictionary-key-already-associated.png
order: 3
---
Visual Basic字典对象是一组唯一键和关联值的集合。在集合中，也可以使用键来索引项，但在这种情况下，只能使用字符串类型的键。而在字典中，可以创建任何类型的键。

与集合不同，字典是COM对象，需要引用“Microsoft Scripting Runtime”库才能使用早期绑定。

![Microsoft Scripting Runtime引用](microsoft-scripting-runtime-library.png){ width=350 }

~~~ vb
Dim dict As Dictionary '早期绑定
Set dict = New Dictionary
~~~

也可以使用晚期绑定，因此不需要将“Microsoft Scripting Runtime”库添加到项目中。

~~~ vb
Dim dict As Object '晚期绑定
Set dict = CreateObject("Scripting.Dictionary")
~~~

有关这些方法的更多信息，请参阅[早期绑定和晚期绑定](visual-basic/variables/declaration#early-binding-and-late-binding)文章。

## 添加、编辑和遍历元素

要添加新的键值对，需要使用**Dictionary**对象的**Add**方法。

~~~ vb
dic.Add <Key>, <Value>
~~~

键必须是唯一的，否则会显示错误。

![运行时错误 '457'，当添加重复键时，该键已与此集合的元素关联](dictionary-key-already-associated.png){ width=350 }

可以通过键或基于0的索引访问字典的元素，可以直接在变量上使用()符号，也可以通过**Item**属性访问。

~~~ vb
Debug.Print dict.Item(<Key>)
Debug.Print dict(<Key>)
~~~

可以使用**Keys**属性检索字典中的所有键。

可以使用**Values**属性检索字典中的所有值。

~~~ vb
Sub AddEditAndTraverse()

    Dim dict As Dictionary
    'Set dict = CreateObject("Scripting.Dictionary")
    Set dict = New Dictionary
    
    dict.Add 10, "Ten"
    dict.Add 100, "Hundred"
    dict.Add 1000, "Thousand"
    
    '10 = Ten
    '100 = Hundred
    '1000 = Thousand
    For Each nmbKey In dict.Keys
        Debug.Print nmbKey & " = " & dict.item(nmbKey)
    Next
    
    dict(100) = "One Hundred" 'value modified
    
    'One Hundred
    Debug.Print dict(100) 'item accessed without the the Item property
    
    'Empty
    Debug.Print dict(10000) 'not existing item

End Sub
~~~



## 键比较模式

默认情况下，键的比较模式设置为**Binary**比较。这意味着如果字典具有字符串类型的键，则键是区分大小写的，即可以同时使用*A*和*a*作为键。

**Exists**方法提供了一种安全的方式来检查键是否已在字典中注册。

**CompareMode**属性允许设置在比较条目时应使用的模式。

* BinaryCompare（默认）。字符串键区分大小写
* TextCompare。字符串键不区分大小写

只能在空字典（没有值）上更改模式，否则会显示错误。

![运行时错误 '5'：更改带有元素的字典对象的比较模式时出现无效的过程调用或参数](change-compare-mode-invalid-procedure.png){ width=400 }

~~~ vb
Sub ExistsCompareMode()
    
    Dim dict As Dictionary
    
    Set dict = New Dictionary
    
    dict.Add "A", 1
    dict.Add "B", 2
    dict.Add "C", 3
    dict.Add "D", 4
    
    'False
    Debug.Print dict.Exists("a")
    
    dict.Add "d", 5 'allows to add the element as the default comparison is binary
    
    'dict.CompareMode = TextCompare 'Run-time error 5: Invalid procedure call or argument
    
    Dim dict1 As New Dictionary
    dict1.CompareMode = TextCompare 'case-insensitive comparison
    
    dict1.Add "A", 1
    dict1.Add "B", 2
    dict1.Add "a", 3 'Run-time error 457: This key is already associated with an element of this collection
    
    'True
    Debug.Print dict1.Exists("a")
    
End Sub
~~~



## 删除元素

可以通过键或基于0的索引使用**Remove**方法从字典中删除任何元素。

> 尝试删除字典中不存在的项将引发异常

![运行时错误 '32811'：当删除不存在的元素时，对象“IDictionary”的方法Remove失败](dictionary-remove-object-error.png){ width=250 }

**RemoveAll**方法允许清除字典并删除所有项。

~~~ vb
Sub Remove()
    
    Dim dict As Dictionary
    
    Set dict = New Dictionary
    
    dict.Add "A", 1
    dict.Add "B", 2
    dict.Add "C", 3
    dict.Add "D", 4
    
    dict.Remove "A"
    
    'dict.Remove "Not Existing Item" 'Run-time error 32811: Method Remove of object IDictionary failed
    
    Dim i As Integer
    
    '2 3 4
    For i = 1 To dict.Count
        Dim item As Integer
        item = dict.Items(i - 1) '0-based index
        Debug.Print item
    Next
    
    dict.RemoveAll
    
    '0
    Debug.Print dict.Count
    
End Sub
~~~

