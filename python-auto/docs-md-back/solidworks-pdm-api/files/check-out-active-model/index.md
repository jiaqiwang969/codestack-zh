---
title: Check-out active SOLIDWORKS model using SOLIDWORKS and PDM API
caption: Check-Out Active Model
description: VBA macro to check-out active model (using release lock) opened in SOLIDWORKS from PDM vault using SOLIDWORKS and PDM APIs
image: open-read-only-warning.png
labels: [check-out,release locks]
---
当已经检入到 SOLIDWORKS PDM 保险库的文件在 SOLIDWORKS 中打开时，将以只读方式访问

![在 SOLIDWORKS 中打开已检入文件](open-read-only-warning.png)

相应的状态将显示在文件名旁边。

![活动文档的只读状态](read-only-file.png)

如果使用标准的 SOLIDWORKS PDM 加载项，可以自动将此文件检出以进行编辑，而无需关闭文件。然而，对于这种情况，调用 [IEdmFile5::LockFile](https://help.solidworks.com/2014/english/api/epdmapi/EPDM.Interop.epdm~EPDM.Interop.epdm.IEdmFile5~LockFile.html) SOLIDWORKS PDM API 将导致以下 COM 异常。

> -2147220981: 尝试访问由其他应用程序独占打开的文件。

SOLIDWORKS API 提供了方法来临时释放活动文档的锁定，以便其他应用程序可以对其进行更新或更改。稍后可以重新加载具有应用的更改的模型。这种技术允许在文件由其他应用程序编辑时，模型信息和视觉数据保持在 SOLIDWORKS 中加载。

以下宏将演示此技术，并在 SOLIDWORKS 应用程序中检出当前打开的已检入（只读）文件。

![具有写访问权限的活动文档](write-access-file.png)

将 *VAULT_NAME* 变量的值修改为打开活动模型的相应保险库名称。

{% code-snippet { file-name: Macro.vba } %}