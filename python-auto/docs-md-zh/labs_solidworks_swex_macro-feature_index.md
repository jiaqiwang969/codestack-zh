---
标题：SwEx.MacroFeature - SOLIDWORKS宏特征的高级框架
标题：SwEx.MacroFeature
描述：使用SOLIDWORKS API简化开发自定义宏特征的框架
toc-group-name：labs-solidworks-swex
顺序：4
---
![SwEx.MacroFeature SOLIDWORKS框架](logo.png)

SwEx.MacroFeature提供了一些工具，用于基于数据模型简化开发SOLIDWORKS宏特征。

{% youtube { id: 3qLUvlFZIek } %}

源代码可在[GitHub](https://github.com/codestackdev/swex-macrofeature)上获取。

## 什么是宏特征？

宏特征是一种自定义元素，可以使用SOLIDWORKS API将其添加到特征管理器设计树中。该元素的行为与任何其他标准特征（例如Boss-Extrude、Move-Copy Body、Mate等）完全相同。

![特征管理器树中的宏特征](feature-mgr-tree-macro-feature.png){ width=250 }

宏特征支持SOLIDWORKS的参数化特性，并且在任何父项更改时可以重新生成。

宏特征提供了3个主要的处理程序：

* 重建 - 在重建特征时调用（无论是作为模型强制重建操作的结果还是作为任何依赖项更新的结果）。宏特征可以创建新的实体或实体，也可以只是一个元数据元素。
* 编辑 - 当用户请求编辑特征定义时调用
* 状态更新 - 每次状态更新时调用（例如选择特征、刷新等）

宏特征可以存储附加的元数据参数（包括尺寸和选择引用）。