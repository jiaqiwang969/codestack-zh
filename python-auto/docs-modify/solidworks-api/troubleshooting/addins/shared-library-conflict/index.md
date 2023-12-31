---
layout: sw-addin-fix
title: How to fix the error of SOLIDWORKS add-ins sharing common libraries
caption: Add-ins which are using shared libraries cannot work together
description: Fixing the issue of using different versions of shared library by enabling binding redirect
labels: [add-in, troubleshooting, shared library]
---
## 症状

有几个SOLIDWORKS插件（通常来自同一供应商）无法一起工作。SOLIDWORKS可能会崩溃或表现异常。如果单独加载插件，则插件可以正常工作。

## 原因

当同一个库（即使是不同版本）被同一应用程序域（例如SOLIDWORKS中的插件）中的不同项目使用时，.NET框架将使用缓存的库。缓存的库将是首次访问的库。例如，当点击插件按钮时可能会访问该库。

这会导致解析程序集引用时可能出现冲突的问题。

## 解决方法

使用[强名称](https://docs.microsoft.com/zh-cn/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)对冲突的程序集进行签名。在这种情况下，将使用特定版本的程序集来解决冲突。

然而，可能存在这样一种情况，即主项目A引用了具有版本1的共享dll B，并且还引用了引用了具有版本2的dll C的dll B，这意味着需要同时加载版本1和2的B。由于dll通常编译在同一个目录中，因此要么需要将它们添加到不同的文件夹中，要么使用[Binding Redirect](https://docs.microsoft.com/zh-cn/dotnet/framework/configure-apps/file-schema/runtime/bindingredirect-element)元素来重定向共享库的不同版本：

将以下代码段添加到**app.config**文件中：

~~~ xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
	<runtime>
		<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
			<dependentAssembly>
				<assemblyIdentity name="[程序集名称]" publicKeyToken="[公钥令牌]" culture="neutral" />
				<bindingRedirect oldVersion="0.0.0.0-9999.9999.9999.9999" newVersion="[当前版本]" />
			</dependentAssembly>
		</assemblyBinding>
	</runtime>
</configuration>
~~~

您可以使用以下代码段从共享库中找到所需的标识信息（即程序集名称、版本、公钥令牌和区域设置）。

~~~ cs
System.Diagnostics.Debug.Print(typeof([共享程序集中的任何类型]).Assembly.FullName);
~~~

这将打印为

~~~
[程序集名称]，Version=[版本]，Culture=[区域设置]，PublicKeyToken=[公钥令牌]
~~~

视频演示：

{% youtube { id: ZeWDoJ5TC7o } %}

在使用绑定重定向时要注意向后兼容性，即从版本1重定向到版本2需要向后兼容，否则此解决方案将无法工作。

如果共享程序集未使用强名称进行签名，则可以通过捕获[AppDomain::AssemblyResolve](https://docs.microsoft.com/zh-cn/dotnet/api/system.appdomain.assemblyresolve?view=netframework-4.8)事件并从方法处理程序返回解析的程序集来在运行时解决冲突。