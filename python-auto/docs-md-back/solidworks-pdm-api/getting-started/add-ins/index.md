---
标题：使用SOLIDWORKS PDM API开发插件
说明：开发SOLIDWORKS PDM插件的指南和代码示例
标签：[插件，PDM]

SOLIDWORKS PDM中的插件是集成到系统中的应用程序。插件安装在SOLIDWORKS PDM管理控制台中，并在连接到存储库的所有客户端之间重新分发。

插件可以访问所有可用的SOLIDWORKS API接口和方法。

要创建插件，需要实现[IEdmAddIn5](https://help.solidworks.com/2018/english/api/epdmapi/epdm.interop.epdm~epdm.interop.epdm.iedmaddin5.html)接口。

本节提供了使用SOLIDWORKS PDM API创建和排除故障的插件的指南。