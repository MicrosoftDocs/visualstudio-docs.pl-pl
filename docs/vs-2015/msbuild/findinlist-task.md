---
title: FindInList — — zadanie | Microsoft Docs
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
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d1fdbc29cfe2fb7d387c6f261953930d2f528150
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149721"
---
# <a name="findinlist-task"></a>FindInList — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na określonej liście znajduje się element, który ma pasującą specyfikacja_elementu.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry [zadania FindInList —](../msbuild/findinlist-task.md).  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`CaseSensitive`|Opcjonalny `Boolean` parametr.<br /><br /> W przypadku `true` wyszukiwania rozróżniana jest wielkość liter; w przeciwnym razie nie jest. Wartość domyślna to `true` .|  
|`FindLastMatch`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , zwróć ostatni odpowiednik; w przeciwnym razie Zwróć pierwsze dopasowanie. Wartość domyślna to `false` .|  
|`ItemFound`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy tylko do odczytu.<br /><br /> Pierwszy pasujący element znajduje się na liście, jeśli istnieje.|  
|`ItemSpecToFind`|Wymagany parametr interfejsu `String`.<br /><br /> Specyfikacja_elementu do wyszukania.|  
|`List`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Lista, w której ma zostać wyszukana wartość specyfikacja_elementu.|  
|`MatchFileNameOnly`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` dopasowuje się tylko do części nazwy pliku specyfikacja_elementu; w przeciwnym razie dopasowuje się do całej klasy specyfikacja_elementu. Wartość domyślna to `true` .|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
