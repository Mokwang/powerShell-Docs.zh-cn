---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: 80852bf750700d549de24e150ffd89ac55b7bf88
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="network-switch-management-with-powershell" class="xliff"></a>
# PowerShell 网络交换机管理

**Get NetworkSwitchEthernetPort** cmdlet 现在返回以下包含实例的附加信息：

- IPAddress – 与端口相关联的 IP 地址
- PortMode – 端口模式：Access、Route 或 Trunk
- AccessVLAN – Access 模式中与此端口相关联的 VLAN 的 ID
- TrunkedVLANList – Trunk 模式中与此端口相关联的 VLAN 的 ID 列表

<a id="fundamental-network-switch-management-with-windows-powershell" class="xliff"></a>
## Windows PowerShell 基本网络交换机管理

在 WMF 5.0 中引入的网络交换机 cmdlet 让你能够将交换机、虚拟 LAN (VLAN) 和基本第 2 层网络交换机端口配置应用到 Windows Server 2012 R2 徽标认证的网络交换机。 Microsoft 仍致力于支持[数据中心抽象](http://technet.microsoft.com/en-us/cloud/dal.aspx)层 (DAL) 的愿景，从而为这一领域中的客户和合作伙伴彰显价值。 通过使用这些 cmdlet，你可以执行：

- 全局交换机配置，如：
    - 设置主机名
    - 设置交换机横幅
    - 保留配置
    - 启用或禁用功能

- VLAN 配置：
    - 创建或删除 VLAN
    - 启用或禁用 VLAN
    - 枚举 VLAN
    - 为 VLAN 设置友好名称

- 第 2 层端口配置：
    - 枚举端口
    - 启用或禁用端口
    - 设置端口模式和属性
    - 添加或将 VLAN 关联到端口上的 Trunk 或 Access

通过查找所有 NetworkSwitch cmdlet 开始探索吧！

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

Jeffrey Snover WMF 5.0 预览公告博客文章中提供了详细信息：<http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>

