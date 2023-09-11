---
title: Managing cut-list bodies using SOLIDWORKS API
caption: Cut-Lists
description: Automating cut-list bodies (weldment and sheet metal) using SOLIDWORKS API
order: 11
labels: [cut-list,weldment,sheet metal]
---

在SOLIDWORKS中，切割清单实体是从钣金件和焊接件生成的。尽管这些实体仍然通过[SOLIDWORKS API接口的IBody2](https://help.solidworks.com/2019/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ibody2.html)进行管理，但与普通实体相比，它们提供了额外的功能：

- 切割清单实体按几何形状分组在切割清单文件夹中
- 切割清单文件夹（一组实体）可以具有自定义属性和自动生成的属性（如长度、厚度等）

可以通过调用切割清单文件夹项的[IFeature::CustomPropertyManager](https://help.solidworks.com/2019/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IFeature~CustomPropertyManager.html)属性来自动化自定义属性。

切割清单是SOLIDWORKS API自动化中最常见的元素之一。请浏览本节中的示例，了解访问切割清单数据的宏和代码片段。