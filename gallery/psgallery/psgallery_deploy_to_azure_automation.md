---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "库,powershell,cmdlet,psgallery"
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 91f48fb43d7fb099e34ce5d3b3b632e3cb119d64
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="deploy-to-azure-automation" class="xliff"></a>
部署到 Azure 自动化
===========================

项详细信息页上的“部署到 Azure 自动化”按钮会将项从 PowerShell 库部署到 Azure 自动化。

![“部署到 Azure 自动化”按钮](Images/DeployToAzureAutomationButton.png)

单击后，将重定向到 Azure 管理门户，可使用 Azure 帐户凭据进行登录。
如果该项包含依赖关系，则所有依赖关系也将部署到 Azure 自动化。

警告：如果自动化帐户中已存在相同的项和版本，将其从 PowerShell 库再次部署会覆盖自动化帐户中的项。

如果部署模块，则该模块会出现在 Azure 自动化的“模块”部分中。  如果部署脚本，则该脚本会出现在 Azure 自动化的“Runbook”部分中。

通过将 AzureAutomationNotSupported 标记添加到项元数据可禁用“部署到 Azure 自动化”按钮。

若要了解有关 Azure 自动化的详细信息，请参阅 Azure 自动化网站 [Azure 自动化网站](http://azure.microsoft.com/en-us/services/automation/)。

