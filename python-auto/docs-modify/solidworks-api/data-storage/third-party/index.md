---
title: Data saving in the 3rd party storage using SOLIDWORKS API
caption: 3rd Party Storage And Store
description: Section explaining how to use 3rd party storage and 3rd party store in SOLIDWORKS API to serialize and deserialize the data directly in the model stream
image: store-diagram.svg
labels: [store,3rd party,third party,storage,serialization]
---
第三方存储和第三方存储库是外部应用程序（插件、宏、独立应用程序）用于将数据直接序列化到模型流中的容器。

这种技术允许存储复杂的数据，并提供了读写大量数据的最佳性能选项。

SOLIDWORKS可以将数据存储在两个不同的容器中：

* 存储（流）
* 存储库

如果将文件系统作为类比，存储对应于文件，而存储库对应于文件夹。存储库可以有子流或子存储库。

下图解释了SOLIDWORKS模型存储的结构。红色元素表示由SOLIDWORKS直接管理的容器，而其他元素表示由第三方管理的容器。

![文档存储图](store-diagram.svg){ width=550 }

## 第三方存储

这是一个通过[IStream](https://docs.microsoft.com/en-us/windows/desktop/api/objidl/nn-objidl-istream)接口管理的容器。当应用程序只需要存储单个数据结构（例如XML树、文本、图像、二进制数据）时，可以使用此选项。

为了获取流的指针（用于读取或写入），需要调用[SOLIDWORKS API方法IModelDoc2::IGet3rdPartyStorage](https://help.solidworks.com/2015/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IModelDoc2~IGet3rdPartyStorage.html)并传递相应的标志。

### 注意事项

* 如果流以前从未被写入过，则[IModelDoc2::IGet3rdPartyStorage](https://help.solidworks.com/2015/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IModelDoc2~IGet3rdPartyStorage.html)方法返回null。
* 在调用获取方法后，无论获取方法是否返回null（即流以前未存储），都应始终释放流，方法是通过[IModelDoc2::IRelease3rdPartyStorage](https://help.solidworks.com/2015/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IModelDoc2~IRelease3rdPartyStorage.html)。
* 存储数据时不应调用[IStream::Commit](https://docs.microsoft.com/en-us/windows/desktop/api/objidl/nf-objidl-istream-commit)方法，否则将引发“方法未实现”异常。

### 生命周期

存储在[LoadFromStorage](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.dpartdocevents_loadfromstoragenotifyeventhandler.html)通知和模型销毁之间可供读取。LoadFromStorageStore在[part](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.dpartdocevents_loadfromstoragenotifyeventhandler.html)、[assembly](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.dassemblydocevents_loadfromstoragenotifyeventhandler.html)和[drawing](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ddrawingdocevents_loadfromstoragenotifyeventhandler.html)中可用。

存储仅在[part](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.dpartdocevents_savetostoragenotifyeventhandler.html)、[assembly](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.dassemblydocevents_savetostoragenotifyeventhandler.html)和[drawing](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ddrawingdocevents_savetostoragenotifyeventhandler.html)通知中可用于写入。

## 第三方存储库

这是一个通过[IStorage](https://docs.microsoft.com/en-us/windows/desktop/api/objidl/nn-objidl-istorage)接口管理的容器。当应用程序管理复杂的数据集并需要在特定时间访问某些部分时，可以使用此选项。存储容器允许创建子流和子存储库来管理数据，并且只有在需要时才能访问特定的流，避免了将整个结构加载到内存中的需要。

要获取存储库的指针，需要调用[SOLIDWORKS API方法IModelDocExtension::IGet3rdPartyStorageStore](https://help.solidworks.com/2015/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IModelDocExtension~IGet3rdPartyStorageStore.html)。

### 注意事项

* [IModelDocExtension::IGet3rdPartyStorageStore](https://help.solidworks.com/2015/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IModelDocExtension~IGet3rdPartyStorageStore.html)对于以前从未写入过的存储返回null。
* 与流类似，存储库始终需要通过[IModelDocExtension::IRelease3rdPartyStorageStore](https://help.solidworks.com/2015/english/api/sldworksapi/SolidWorks.Interop.sldworks~SolidWorks.Interop.sldworks.IModelDocExtension~IRelease3rdPartyStorageStore.html)方法释放。
* 使用[IStorage](https://docs.microsoft.com/en-us/windows/desktop/api/objidl/nn-objidl-istorage)接口的方法创建子流和存储库。

### 生命周期

存储在[LoadFromStorageStore](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.dpartdocevents_loadfromstoragestorenotifyeventhandler.html)通知和模型销毁之间可供读取。LoadFromStorageStore在[part](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.dpartdocevents_loadfromstoragestorenotifyeventhandler.html)、[assembly](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.dassemblydocevents_loadfromstoragestorenotifyeventhandler.html)和[drawing](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ddrawingdocevents_loadfromstoragestorenotifyeventhandler.html)中可用。

存储仅在[part](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.dpartdocevents_savetostoragestorenotifyeventhandler.html)、[assembly](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.dassemblydocevents_savetostoragestorenotifyeventhandler.html)和[drawing](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.ddrawingdocevents_savetostoragestorenotifyeventhandler.html)通知中可用于写入。

## 用法

通常，在模型补充了额外功能（例如电气数据、PDM、安全性等）的插件中使用第三方容器（存储和存储库）。在这种情况下，此附加信息通常显示在特征树、任务窗格等中，并在打开模型时加载，并与模型一起保存，使此方法成为完全集成的解决方案。

*SOLIDWORKS API通知SaveToStorage*和*SaveToStorageStore*在文件保存通知之后直接触发，这意味着无需实现自定义数据保存，因为它将通过用户保存自动触发。

最佳的附加保存和加载事件的位置应该在[DocumentLoadNotify](https://help.solidworks.com/2015/english/api/sldworksapi/solidworks.interop.sldworks~solidworks.interop.sldworks.dsldworksevents_documentloadnotify2eventhandler.html)事件中。

当第三方数据被修改时（例如用户在第三方树中添加了新节点），建议通过[IModelDoc2::SetSaveFlag](https://help.solidworks.com/2015/english/api/sldworksapi/SOLIDWORKS.Interop.sldworks~SOLIDWORKS.Interop.sldworks.IModelDoc2~SetSaveFlag.html)将模型标记为脏，以指示需要用户保存模型。

## 存储和流命名冲突

存储和存储库通过相应的名称访问。不同的开发人员可能会对存储或存储库使用相同的名称，这样就会发生冲突。在使用第三方容器时，建议通过SOLIDWORKS API支持注册存储或存储库名称，并在这种情况下，此名称将被保留。

有关如何使用SwEx.AddIn框架访问第三方容器的信息，请参阅[在SOLIDWORKS模型中使用SwEx.AddIn框架存储第三方数据](/labs/solidworks/swex/add-in/third-party-data-storage/)文章。