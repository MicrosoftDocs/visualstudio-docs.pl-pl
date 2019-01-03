---
title: Resolvenonmsbuildprojectoutput — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ca7fe0b9ed987896749319e3c14f2a926450782
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990925"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput — zadanie
Określa pliki wyjściowe dla odwołań do projektu niekorzystających z programu MSBuild.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `ResolveNonMSBuildProjectOutput` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`PreresolvedProjectOutputs`|Opcjonalnie `String` parametru.<br /><br /> Określa, że ciągu XML, który zawiera rozwiązane dane wyjściowe projektu.|  
|`ProjectReferences`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa odwołania do projektu.|  
|`ResolvedOutputPaths`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera listę ścieżek rozpoznanych odwołań (i zachowuje oryginalne atrybutach odwołania projektu).|  
|`UnresolvedProjectReferences`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera listę elementów odniesienia projektu, których nie można rozwiązać za pomocą preresolved listy wyników.<br /><br /> Ponieważ program Visual Studio preresolves tylko projekty niekorzystających z programu MSBuild, oznacza to, że odwołania projektu na tej liście są w formacie programu MSBuild.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)