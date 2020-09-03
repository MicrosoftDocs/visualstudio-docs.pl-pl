---
title: XslTransformation — — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1705fd2b79f8b5044aa4ffa0b65801d6db6c7f33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198954"
---
# <a name="xsltransformation-task"></a>XslTransformation — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przekształca dane wejściowe XML przy użyciu XSLT lub skompilowanego XSLT i wyjść do urządzenia wyjściowego lub pliku.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `XslTransformation` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`OutputPaths`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki wyjściowe transformacji XML.|  
|`Parameters`|Opcjonalny `String` parametr.<br /><br /> Określa parametry dokumentu wejściowego XSLT.|  
|`XmlContent`|Opcjonalny `String` parametr.<br /><br /> Określa dane wejściowe w formacie XML jako ciąg.|  
|`XmlInputPaths`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa pliki wejściowe XML.|  
|`XslCompiledDllPath`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa skompilowane XSLT.|  
|`XslContent`|Opcjonalny `String` parametr.<br /><br /> Określa dane wejściowe XSLT jako ciąg.|  
|`XslInputPath`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa plik wejściowy XSLT.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
