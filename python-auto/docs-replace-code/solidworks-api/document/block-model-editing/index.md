---
title: Block model editing using SOLIDWORKS API
caption: Block Model Editing
description: Example demonstrate different ways of disabling the model editing
labels: [block editing, block model, example, lock, menu, solidworks api]
redirect-from:
  - /2018/03/block-model-editing.html
---

该示例演示了使用SOLIDWORKS API禁用模型编辑的不同方法：

* 阻止菜单 - 用户无法调用菜单命令。通常在显示属性管理器页面时使用此功能，以防止调用任何命令。
* 阻止模型编辑 - 模型只能查看，无法更改。
* 完全阻止 - 禁用编辑和视图操作。

需要逐步调试宏以查看不同的SOLIDWORKS API函数的实际效果。

~~~ vb
Dim swApp As SldWorks.SldWorks
Dim swModel As SldWorks.ModelDoc2

Sub main()

    Set swApp = Application.SldWorks
    
    Set swModel = swApp.ActiveDoc
    
    BlockAll
    UnblockAll
    
    BlockMenusAndEdit
    UnlockMenusAndEdit
    
    BlockMenu
    UnblockMenu
        
End Sub

'Block menu, buttons and any manipulations (including model rotation)
Sub BlockAll()
    
    'get the current blocking state if it will be required to reset
    Dim curBlock As Integer
    curBlock = swModel.GetBlockingState
        
    swModel.SetBlockingState swBlockingStates_e.swSystemBlock
        
End Sub

'Block menu, buttons and any manipulations (including model rotation)
Sub UnblockAll()
    
    swModel.ResetBlockingState
    
End Sub

'Blocks menus and edits, but allows model moving and zooming
Sub BlockMenusAndEdit()
    
    swModel.Lock
    
End Sub

Sub UnlockMenusAndEdit()
    
    swModel.UnLock
    
End Sub

'Only blocks file related menu commands (new or save)
Sub BlockMenu()

    swApp.EnableFileMenu = False

End Sub

Sub UnblockMenu()

    swApp.EnableFileMenu = True
    
End Sub

~~~

