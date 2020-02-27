---
title: FindInList — — zadanie | Microsoft Docs
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 915265a775f572467ad1296499bdd3201adc1f8b
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634152"
---
# <a name="findinlist-task"></a>FindInList — zadanie

Na określonej liście znajduje się element, który ma pasującą specyfikacja_elementu.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry [zadania FindInList —](../msbuild/findinlist-task.md).

|Parametr|Opis|
|---------------|-----------------|
|`CaseSensitive`|Opcjonalny parametr `Boolean`.<br /><br /> W przypadku `true`w wyszukiwaniu jest uwzględniana wielkość liter. w przeciwnym razie nie jest. Wartość domyślna to `true`.|
|`FindLastMatch`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, zwróć ostatnie dopasowanie; w przeciwnym razie Zwróć pierwsze dopasowanie. Wartość domyślna to `false`.|
|`ItemFound`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametru wyjściowego tylko do odczytu.<br /><br /> Pierwszy pasujący element znajduje się na liście, jeśli istnieje.|
|`ItemSpecToFind`|Wymagany `String` parametr.<br /><br /> Specyfikacja_elementu do wyszukania.|
|`List`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Lista, w której ma zostać wyszukana wartość specyfikacja_elementu.|
|`MatchFileNameOnly`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, Dopasuj tylko do części nazwy pliku w specyfikacja_elementu; w przeciwnym razie Dopasuj do całej. Wartość domyślna to `true`.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
