---
title: Findinlist — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f083d44578a4fe61029c707b3798191c5b8b3665
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865638"
---
# <a name="findinlist-task"></a>FindInList — zadanie
Na określonej liście wyszukuje element, który ma pasujące itemspec.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry [findinlist — zadanie](../msbuild/findinlist-task.md).  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`CaseSensitive`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, w wyszukiwaniu jest uwzględniana wielkość liter; w przeciwnym razie, nie jest. Wartość domyślna to `true`.|  
|`FindLastMatch`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zwracają ostatniego dopasowania; w przeciwnym razie zwraca pierwsze dopasowanie. Wartość domyślna to `false`.|  
|`ItemFound`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru wyjściowego tylko do odczytu.<br /><br /> Pierwsze dopasowanie znaleziono elementu na liście, jeśli istnieje.|  
|`ItemSpecToFind`|Wymagane `String` parametru.<br /><br /> Specyfikacja_elementu do wyszukania.|  
|`List`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Lista, w których należy szukać itemspec.|  
|`MatchFileNameOnly`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, dopasowywania tylko plik część nazwy specyfikacja_elementu; w przeciwnym razie dopasowywania całego itemspec. Wartość domyślna to `true`.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)