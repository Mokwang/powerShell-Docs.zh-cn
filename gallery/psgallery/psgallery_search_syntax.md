---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "库,powershell,cmdlet,psgallery"
title: psgallery_search_syntax
ms.openlocfilehash: 409ae607557af760f9cec4e3c54f39e51b5fac18
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a id="gallery-search-syntax" class="xliff"></a>
# 库搜索语法

PowerShell 库提供文本搜索框，可以在其中使用单词、短语和关键字表达式来缩小搜索结果的范围。

<a id="search-by-keywords" class="xliff"></a>
## 按关键字搜索

    dsc azure sql

“搜索”将最大程度地查找包含所有 3 个关键字的相关文档，并返回匹配的文档。

<a id="search-using-phrases-and-keywords" class="xliff"></a>
## 使用短语和关键字进行搜索

    "azure sql" deployment

在引号（“”）之间输入短语将搜索更改为查找特定的短语而不是单独的关键字。
匹配的文档通常应包含确切的短语“azure sql”，包括大写的变体。“Azure SQL”，并通常还包含“deployment”一词。

<a id="filtering-on-fields" class="xliff"></a>
## 按字段进行筛选

通过将字段名称作为前缀加入搜索词，可以搜索特定项 ID（或“Id”或“id”），或一些其他字段。

目前可搜索的字段有“Id”、“Version”、“Tags”、“Author”、“Owner”、“Functions”、“Cmdlet”、“DscResources”和“PowerShellVersion”。

[ID 和标题之间的区别是什么？ ID 是在控制台中使用的名称。 标题是在搜索结果中的项页顶部所显示的内容。]

<a id="examples" class="xliff"></a>
## 示例

    ID:"PSReadline"
    id:"AzureRM.Profile"

分别在其 ID 字段中查找具有“PSReadline”或“AzureRM.Profile”的项。

    Id:"AzureRM.Profile"

是另一种在其 ID 字段中查找具有“AzureRM.Profile”项的方法。

“Id”筛选器是一个子字符串匹配，因此，如果搜索以下内容：

    Id:"azure"
    
你将得到如“AzureRM.Profile”和“Azure.Storage”等结果。

你也可以搜索单个字段中的多个关键字。 或混合和匹配字段。

    id:azure tags:intellisense
    id:azure id:storage

并且，你可以执行短语搜索：

    id:"azure.storage"


搜索具有 DSC 标记的所有项。

    Tags:"DSC"

搜索具有指定函数的所有项。

    Functions:"Update-AzureRM"

搜索具有指定 cmdlet 的所有项。
    
    Cmdlets:"Get-AzureRmEnvironment"

搜索具有指定 DSC 资源名称的所有项。

    DscResources:"xArchive"

搜索具有指定 PowerShellVersion 的所有项

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


最后，如果你使用不支持的字段（如“commands”），我们将忽略该字段并搜索所有字段。 因此以下查询

    commands:blobs storage
    
的解释与此查询完全相同：

    blobs storage

