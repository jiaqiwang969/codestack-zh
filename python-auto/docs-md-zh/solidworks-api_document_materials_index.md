---
title: 使用SOLIDWORKS API处理零件材料
caption: 材料
description: 收集与使用SOLIDWORKS API处理材料相关的文章和示例
order: 15
---
SOLIDWORKS中的材料数据库存储在XML文件中。SOLIDWORKS API没有提供直接处理材料数据库（如搜索、添加、读取等）的方法。然而，由于XML是一种开放格式，可以使用任何XML解析技术，例如使用[XmlDocument](https://docs.microsoft.com/zh-cn/dotnet/api/system.xml.xmldocument)、[XmlSerializer](https://docs.microsoft.com/zh-cn/dotnet/api/system.xml.serialization.xmlserializer)等。

[SOLIDWORKS API的ISldWorks::GetMaterialDatabases](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.isldworks~getmaterialdatabases.html)方法返回材料数据库的路径。

[IPartDoc::GetMaterialPropertyName2](https://help.solidworks.com/2018/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ipartdoc~getmaterialpropertyname2.html)返回材料的名称以及存储该材料的数据库的名称。

本节包含了关于如何使用SOLIDWORKS中的材料数据库、如何应用和读取SOLIDWORKS零件和实体的材料信息的示例。