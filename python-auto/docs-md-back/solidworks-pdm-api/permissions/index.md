---
title: Managing permissions in SOLIDWORKS Professional PDM API
caption: Permissions
description: Managing user, groups and folders permissions in SOLIDWORKS PDM Professional using SOLIDWORKS PDM API
labels: [rights, permissions]
order: 5
---

SOLIDWORKS PDM API提供了管理用户、文件夹和组的各种权限的功能。

可以通过[IEdmUserMgr7::GetFolderPermissions](https://help.solidworks.com/2018/english/api/epdmapi/epdm.interop.epdm~epdm.interop.epdm.iedmusermgr7~getfolderpermissions.html)和[IEdmUserMgr7::SetFolderPermissions](https://help.solidworks.com/2018/english/api/epdmapi/epdm.interop.epdm~epdm.interop.epdm.iedmusermgr7~setfolderpermissions.html)方法来管理文件夹权限。

可以通过[IEdmUserMgr9::GetStatePermissions](https://help.solidworks.com/2018/english/api/epdmapi/EPDM.Interop.epdm~EPDM.Interop.epdm.IEdmUserMgr9~GetStatePermissions.html)和[IEdmUserMgr9::SetStatePermissions](https://help.solidworks.com/2018/english/api/epdmapi/EPDM.Interop.epdm~EPDM.Interop.epdm.IEdmUserMgr9~SetStatePermissions.html)方法来管理状态权限。

可以通过[IEdmUserMgr9::GetTransitionPermissions](https://help.solidworks.com/2018/english/api/epdmapi/EPDM.Interop.epdm~EPDM.Interop.epdm.IEdmUserMgr9~GetTransitionPermissions.html)和[IEdmUserMgr9::SetTransitionPermissions](https://help.solidworks.com/2018/english/api/epdmapi/EPDM.Interop.epdm~EPDM.Interop.epdm.IEdmUserMgr9~SetTransitionPermissions.html)方法来管理转换权限。