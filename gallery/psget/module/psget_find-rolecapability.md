---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: Find-RoleCapability
ms.openlocfilehash: 77c5b492d9681fa05315401fba410c508af1d13b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="find-rolecapability" class="xliff"></a>
# Find-RoleCapability

在模块中查找角色功能。

<a id="description" class="xliff"></a>
## 说明
Find-RoleCapability cmdlet 查找模块中的 PowerShell 角色功能。 Find-RoleCapability 在已注册的存储库中搜索模块。 对于此 cmdlet 查找的每个角色功能，它将返回 PSGetRoleCapabilityInfo 对象。 可以将 PSGetRoleCapabilityInfo 对象传递给 Install-Module cmdlet 以安装包含角色功能的模块。
PowerShell 角色功能定义在 Just Enough Administration (JEA) 终结点中可供用户使用的命令、应用程序等。 角色功能由扩展名为“.psrc”的文件定义。

- Find-RoleCapability 可使用版本参数 MinimumVersion、RequiredVersion、AllVersions 进行筛选。
  - 这些参数彼此排斥。
  - 这些版本参数只允许具有单个模块名称，而不能具有任何通配符。
  - 如果未指定 RequiredVersion 参数，Find-RoleCapability 将返回等于或高于指定的最低版本的最新版本的模块或最新版本的模块（若未指定最低版本）。
  - 如果指定了 RequiredVersion 参数，Find-RoleCapability 仅返回与指定版本完全匹配的模块。
- Find-RoleCapability 可使用 -Tag 参数对模块元数据进行筛选
- Find-RoleCapability 可使用 -Filter 参数对存储库特定搜索语言进行筛选。
- Find-RoleCapability 可以从所有或少数已注册存储库中对模块进行筛选。

<a id="cmdlet-syntax" class="xliff"></a>
## Cmdlet 语法
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Cmdlet 联机帮助参考

[Find-RoleCapability](http://go.microsoft.com/fwlink/?LinkId=718029)

<a id="example-commands" class="xliff"></a>
## 示例命令
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```

