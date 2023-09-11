使用SOLIDWORKS API自动化表格（BOM、通用、修订等）

所有由SOLIDWORKS支持的表格类型都可以通过API访问。这包括但不限于：

- 物料清单（BOM）
- 通用表格
- 焊接构件切割清单
- 孔表格

等等。

所有表格都继承了ITableAnnotation SOLIDWORKS API接口。该接口提供了与表格工作的方法（例如更改单元格、更改格式、添加/删除行等）。

对于通用表格注释，有特定的表格注释。例如，IBomTableAnnotation是物料清单（BOM）表格的特定表格注释。可以通过直接分配指针将通用表格注释转换为特定表格注释。

表格也存在于特征管理器树中，这意味着它还提供了IFeature接口提供的方法。每个特定的表格注释都提供了访问特定表格特征的属性。例如，IBomTableAnnotation::BomFeature将返回特定的BOM特征。要获取IFeature的指针，需要对所有特定表格特征调用::GetFeature方法。