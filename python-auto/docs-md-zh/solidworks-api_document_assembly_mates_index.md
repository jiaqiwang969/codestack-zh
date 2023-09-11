---
标题：使用SOLIDWORKS API自动化装配中的配对
说明：收集有关在装配中配对组件的文章和代码示例
图片：assembly-mating.png
标签：[装配，配对]
顺序：1
---
![通过API配对装配组件](assembly-mating.png){ width=200 }

可以通过[SOLIDWORKS API的IAssemblyDoc::AddMate3](https://help.solidworks.com/2012/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IAssemblyDoc~AddMate3.html)方法（或该方法的更新版本）以编程方式对装配组件进行配对。

需要为不同的配对类型使用不同的标记来标记所选对象。请参考SOLIDWORKS API帮助文档以获取特定配对的标记值，或使用SOLIDWORKS宏记录器来捕获正确的标记。