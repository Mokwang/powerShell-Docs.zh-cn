---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: New-ScriptFileInfo
ms.openlocfilehash: 9aed0e16f2dec3681ca4b58595aae8d4972a3808
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="new-scriptfileinfo" class="xliff"></a>
# New-ScriptFileInfo

使用元数据创建脚本文件。

<a id="description" class="xliff"></a>
## 说明

New-ScriptFileInfo cmdlet 创建 PowerShell 脚本文件，包括有关脚本的元数据。

<a id="cmdlet-syntax" class="xliff"></a>
## Cmdlet 语法

```powershell
Get-Command -Name New-ScriptFileInfo -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Cmdlet 联机帮助参考

[New-ScriptFileInfo](http://go.microsoft.com/fwlink/?LinkId=619792)

<a id="example-commands" class="xliff"></a>
## 示例命令

<a id="passthru-parameter" class="xliff"></a>
### PassThru 参数

```powershell
New-ScriptFileInfo -Description "Script file description." -PassThru
```

<a id="new-scriptfileinfo-cmdlet" class="xliff"></a>
### New-ScriptFileInfo cmdlet
New-ScriptFileInfo cmdlet 可创建包含诸如 Version、Guid、Author 和 Description 等元数据的新脚本文件。 

```powershell
# Create a new script file with minimum required metadata values
New-ScriptFileInfo -Path C:\ScriptSharingDemo\Demo-Script.ps1 -Description "Script file description goes here"

Get-Content -Path C:\ScriptSharingDemo\Demo-Script.ps1
<#PSScriptInfo
.VERSION 1.0
.GUID 926b47c3-6af2-4b18-b6f5-8b813a9e93ab
.AUTHOR manikb
.COMPANYNAME
.COPYRIGHT
.TAGS
.LICENSEURI
.PROJECTURI
.ICONURI
.EXTERNALMODULEDEPENDENCIES
.REQUIREDSCRIPTS
.EXTERNALSCRIPTDEPENDENCIES
.RELEASENOTES
#>
<#
.DESCRIPTION
Script file description goes here
#>
Param()

# Validate and get the script metadata
Test-ScriptFileInfo -Path C:\ScriptSharingDemo\Demo-Script.ps1
Version Name Author Description
------- ---- ------ -----------
1.0 Demo-Script manikb Script file description goes here

# Add function and workflow to the script file
Add-Content -Path C:\ScriptSharingDemo\Demo-Script.ps1 -Value @"
   
    Function Demo-ScriptFunction { 'Demo-ScriptFunction' }
   
    Workflow Demo-ScriptWorkflow { 'Demo-ScriptWorkflow' }
   
    Demo-ScriptFunction
    Demo-ScriptWorkflow
"@

# Validate and get the script metadata
Test-ScriptFileInfo -Path C:\ScriptSharingDemo\Demo-Script.ps1

Version Name Author Description
------- ---- ------ -----------
1.0 Demo-Script manikb Script file description goes here

# Create a script file all metadata properties
New-ScriptFileInfo -Path 'C:\ScriptSharingDemo\Demo-ScriptWithCompletePSScriptInfo.ps1' `
    -Version 1.0 `
    -Author 'manikb' `
    -Description "my new script file" `
    -CompanyName "Microsoft Corporation" `
    -Copyright "(c) 2015 Microsoft Corporation. All rights reserved." `
    -Tags @('Tag1', 'Tag2', 'Tag3') `
    -ProjectUri 'https://contoso.com' `
    -LicenseUri "https://contoso.com/License" `
    -IconUri 'https://contoso.com/Icon' `
    -ReleaseNotes @('contoso script now supports following features',
    'Feature 1',
    'Feature 2',
    'Feature 3',
    'Feature 4',
    'Feature 5') `
    -RequiredModules @('RequiredModule1',
    @{ModuleName='RequiredModule2';ModuleVersion='1.0'},
    @{ModuleName='RequiredModule3';RequiredVersion='2.0'},
    @{ModuleName = 'RequiredModule4'; ModuleVersion = '0.1'; MaximumVersion = '1.*'; },
    @{ModuleName = 'RequiredModule5'; MaximumVersion = '1.*'; },
    'ExternalModule1') `
    -ExternalModuleDependencies 'ExternalModule1' `
    -RequiredScripts 'Start-WFContosoServer', 'Stop-ContosoServerScript', 'ExternalScript1' `
    -ExternalScriptDependencies 'ExternalScript1'

# Add function and workflow to the script file
Add-Content -Path 'C:\ScriptSharingDemo\Demo-ScriptWithCompletePSScriptInfo.ps1' -Value @"
   
    Function Demo-ScriptFunction { 'Demo-ScriptFunction' }
   
    Workflow Demo-ScriptWorkflow { 'Demo-ScriptWorkflow' }
   
    Demo-ScriptFunction
    Demo-ScriptWorkflow
"@

Get-Content -Path C:\ScriptSharingDemo\Demo-ScriptWithCompletePSScriptInfo.ps1

<#PSScriptInfo
.VERSION 1.0
.GUID fe4cc121-f87e-4ddb-8186-ff362e23a935
.AUTHOR manikb
.COMPANYNAME Microsoft Corporation
.COPYRIGHT (c) 2015 Microsoft Corporation. All rights reserved.
.TAGS Tag1 Tag2 Tag3
.LICENSEURI https://contoso.com/License
.PROJECTURI https://contoso.com/
.ICONURI https://contoso.com/Icon
.EXTERNALMODULEDEPENDENCIES ExternalModule1
.REQUIREDSCRIPTS Start-WFContosoServer,Stop-ContosoServerScript,ExternalScript1
.EXTERNALSCRIPTDEPENDENCIES ExternalScript1
.RELEASENOTES
contoso script now supports following features
Feature 1
Feature 2
Feature 3
Feature 4
Feature 5
#>
#Requires -Module RequiredModule1
#Requires -Module @{ModuleName = 'RequiredModule2'; ModuleVersion = '1.0'}
#Requires -Module @{RequiredVersion = '2.0'; ModuleName = 'RequiredModule3'}
#Requires -Module @{ModuleVersion = '0.1'; ModuleName = 'RequiredModule4'; MaximumVersion = '1.*'}
#Requires -Module @{MaximumVersion = '1.*'; ModuleName = 'RequiredModule5'}
#Requires -Module ExternalModule1
<#
.DESCRIPTION
my new script file
#>
Param()
Function Demo-ScriptFunction { 'Demo-ScriptFunction' }
Workflow Demo-ScriptWorkflow { 'Demo-ScriptWorkflow' }
Demo-ScriptFunction
Demo-ScriptWorkflow

# Validate and get the script metadata
Test-ScriptFileInfo C:\ScriptSharingDemo\Demo-ScriptWithCompletePSScriptInfo.ps1 | Format-List * -Force

Name : Demo-ScriptWithCompletePSScriptInfo
Version : 1.0
Guid : fe4cc121-f87e-4ddb-8186-ff362e23a935
Path : C:\ScriptSharingDemo\Demo-ScriptWithCompletePSScriptInfo.ps1
ScriptBase : C:\ScriptSharingDemo
Description : my new script file
Author : manikb
CompanyName : Microsoft Corporation
Copyright : (c) 2015 Microsoft Corporation. All rights reserved.
Tags : {Tag1, Tag2, Tag3}
ReleaseNotes : {contoso script now supports following features, Feature 1, Feature 2, Feature 3...}
RequiredModules : {RequiredModule1, @{ ModuleName = 'RequiredModule2'; ModuleVersion = '1.0' }, @{ ModuleName = 'RequiredModule3'; RequiredVersion = '2.0' }, @{ ModuleName = 'RequiredModule4'; ModuleVersion = '0.1';
MaximumVersion = '1.*' }...}
ExternalModuleDependencies : ExternalModule1
RequiredScripts : {Start-WFContosoServer, Stop-ContosoServerScript, ExternalScript1}
ExternalScriptDependencies : ExternalScript1
LicenseUri : https://contoso.com/License
ProjectUri : https://contoso.com/
IconUri : https://contoso.com/Icon
DefinedCommands : {Demo-ScriptFunction, Demo-ScriptWorkflow}
DefinedFunctions : Demo-ScriptFunction
DefinedWorkflows : Demo-ScriptWorkflow
```

