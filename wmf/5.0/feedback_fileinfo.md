---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,安装程序"
ms.openlocfilehash: 587f3f592f4aab53c95bbc6d37ea37d7f2364aec
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="updates-to-fileinfo-object" class="xliff"></a>
# 对 FileInfo 对象的更新
文件版本信息可能会产生误导，尤其是在对文件进行了修补的情况下。 此版本的 WMF 5.0 向 FileInfo 对象添加了新的 **FileVersionRaw** 和 **ProductVersionRaw** 脚本属性。 以下是为 powershell.exe 显示的属性（假设 $pid 为 PowerShell 进程的 ID）：

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117

