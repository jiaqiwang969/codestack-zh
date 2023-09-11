---
title: Power Shell script to set folder permissions using SOLIDWORKS PDM API
caption: Set Folder Permissions
description: Vb.NET Power Shell script to set permissions to specified folder for specified user using SOLIDWORKS PDM API
image: folder-permissions.png
labels: [permissions,folder]
---
![SOLIDWORKS PDM 管理面板中的文件夹权限](folder-permissions.png){ width=450 }

此 Power Shell 脚本允许使用 SOLIDWORKS PDM API 为指定用户设置指定文件夹的权限。

要使用脚本，请创建 PowerShell 文件和命令行文件，如下所示。

需要将 SOLIDWORKS PDM 互操作文件放置在与脚本文件相同的文件夹中。有关生成互操作文件的更多信息，请参阅[.NET Framework 2.0 中的互操作](/solidworks-pdm-api/getting-started#framework-20-or-older)文章。

脚本参数：

1. *vaultName* - 执行操作的库的名称
1. *userName* - 执行操作的用户名（应具有分配权限的权限）
1. *password* - 上述用户名的密码
1. *folderName* - 要更改权限的文件夹的完整路径
1. *targetUserName* - 要更改权限的用户名
1. *permissions* - 要分配的权限。整数值，表示单个权限或一组权限。权限数字在[EdmRightFlags](https://help.solidworks.com/2018/english/api/epdmapi/EPDM.Interop.epdm~EPDM.Interop.epdm.EdmRightFlags.html)中定义。将所需权限的值相加以分配多个值（例如，为读取文件权限设置 1，为读取、签出、删除和添加文件设置 15 [1 + 2 + 4 + 8]）

~~~
> set-permissions.cmd MyVault admin pwd "D:\My Vaults\Vault1\Folder1" user1 15
~~~

## set-permissions.ps1

{% code-snippet { file-name: set-permissions.ps1 } %}

## set-permissions.cmd

{% code-snippet { file-name: set-permissions.cmd } %}