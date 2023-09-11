如何创建SOLIDWORKS PDM Professional（EPDM）插件

SOLIDWORKS PDM Professional（以前称为SOLIDWORKS Enterprise PDM）提供了丰富的API库，使第三方能够为系统开发自定义扩展。通过开发应用程序作为SOLIDWORKS PDM插件，可以实现最高级别的集成。下面详细的逐步指南将引导您从头开始创建插件。

在本文中，我将在Microsoft Visual Studio中使用.NET（C#和VB.NET）创建插件。

1. 启动Visual Studio并创建新项目
2. 从项目模板中选择类库
3. 指定插件的名称
4. 必须添加对PDM Interop Library的引用（针对Framework 3.5和2.0的项目，引用*EdmInterface.dll*，针对Framework 4.0或更高版本的项目，引用*EPDM.Interop.epdm.dll*）。该库可以在SOLIDWORKS PDM安装文件夹中找到（通常是*C:\Program Files\SOLIDWORKS PDM\EPDM.Interop.epdm.dll*用于Framework 4.0及更高版本，*C:\Program Files\SOLIDWORKS PDM\EdmInterface.dll*用于旧版本）。
5. 如果您的项目针对.NET Framework 4.0或更高版本，请将*Embed Interop Types*选项设置为*False*，否则插件可能无法正常工作。

![嵌入互操作程序集选项](embed-interops.png){ width=320 height=291 }

为了创建PDM插件的类，需要执行3个必要的步骤：

1. 实现[IEdmAddIn5](https://help.solidworks.com/2014/english/api/epdmapi/epdm.interop.epdm~epdm.interop.epdm.iedmaddin5.html)接口。
2. 将类标记为Com Visible。
3. 在[GetAddInInfo](https://help.solidworks.com/2014/english/api/epdmapi/EPDM.Interop.epdm~EPDM.Interop.epdm.IEdmAddIn5~GetAddInInfo.html)中通过设置[EdmAddInInfo.mlRequiredVersionMajor](https://help.solidworks.com/2014/english/api/epdmapi/epdm.interop.epdm~epdm.interop.epdm.edmaddininfo~mlrequiredversionmajor.html)属性来指定插件支持的最低主要版本。

{% code-snippet { file-name: SampleAddIn.* } %}

注意事项：

* 建议**不要勾选**“使程序集COM可见”选项，而是对所有需要COM可见的类（例如插件的主类）使用[ComVisible](https://msdn.microsoft.com/zh-cn/library/system.runtime.interopservices.comvisibleattribute(v=vs.110).aspx)属性。否则，这可能会显著增加插件的加载时间。

![在项目设置中使程序集COM可见选项](make-assm-com-vis.png){ width=320 height=269 }

* 与注册SOLIDWORKS插件不同，**不需要**实际注册PDM插件DLL作为COM对象（即运行RegAsm实用程序或在项目属性中选中“为COM互操作注册程序集”选项）。
* 建议使用[Guid](https://msdn.microsoft.com/zh-cn/library/system.runtime.interopservices.guidattribute(v=vs.110).aspx)属性装饰插件的类，这样可以更好地跟踪客户端机器上的插件（例如调试或清除插件缓存）。

为了将PDM插件加载到存储库中，请按照以下步骤操作：

* 启动*SOLIDWORKS PDM Administration*控制台（可以在Windows开始菜单中找到）
* 导航到PDM存储库
* 选择*Add-Ins*节点，然后选择*New Add-In...*命令

![在管理面板中添加新插件](new-addin.png){ width=320 height=250 }

* 从项目的*bin*目录中选择所有文件。您不需要添加临时文件（如*.pdb*或*.xml*）。
* 插件加载后，显示其摘要信息。

![插件摘要页面](addin-summary.png){ width=320 height=263 }

导航到存储库视图，然后从上下文菜单中选择*Test Menu Command*。

![存储库资源管理器中的插件命令](menu-cmd.png){ width=320 height=318 }

将显示消息框：

![Hello World消息框](hello-world.png){ width=198 height=200 }

SOLIDWORKS PDM是一个客户端-服务器架构系统，这意味着每当插件加载到存储库中时，它将分发到所有客户端。当客户端登录到存储库时，PDM将插件DLL本地下载到*%localappdata%\SolidWorks\SOLIDWORKS PDM\Plugins\**VaultName**\**AddIn Guid**Index*文件夹中。

插件DLL将加载到多个进程中（包括*explorer.exe*）第一次登录到PDM存储库时。由于.NET Framework的限制，无法从应用程序域中卸载.NET库。这就是为什么当将插件添加到存储库时，PDM显示“'You have chosen to load a .NET add-in. SOLIDWORKS PDM cannot force a reload of .NET add-ins'”的原因。

![添加.NET插件时显示的警告](net-addin-replace-warning.png){ width=320 height=169 }

这个消息意味着缓存的（之前的）版本的PDM插件将继续使用，直到DLL被解锁。而不是重新启动机器，可以使用以下命令行脚本一次性释放插件：

{% code-snippet { file-name: UnloadPdmClient.cmd } %}

SOLIDWORKS PDM提供了方便的功能，简化了PDM插件的调试。请阅读以下文章：[调试SOLIDWORKS PDM插件-最佳实践](../debugging-best-practices)

下面是从头开始创建SOLIDWORKS PDM插件的视频演示：

{% youtube { id: GsTWneNoIW4 } %}