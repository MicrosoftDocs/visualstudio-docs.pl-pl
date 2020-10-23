---
title: FindInList — — zadanie | Microsoft Docs
description: Dowiedz się, jak za pomocą zadania MSBuild FindInList — znaleźć element, który ma pasującą wartość specyfikacja_elementu na określonej liście.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b4afc20b7845f3af71de1fbbb89f074801e08d1d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92435699"
---
# <a name="findinlist-task"></a>FindInList — zadanie

Na określonej liście znajduje się element, który ma pasującą specyfikacja_elementu.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry [zadania FindInList —](../msbuild/findinlist-task.md).

|Parametr|Opis|
|---------------|-----------------|
|`CaseSensitive`|Opcjonalny `Boolean` parametr.<br /><br /> W przypadku `true` wyszukiwania rozróżniana jest wielkość liter; w przeciwnym razie nie jest. Wartość domyślna to `true`.|
|`FindLastMatch`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , zwróć ostatni odpowiednik; w przeciwnym razie Zwróć pierwsze dopasowanie. Wartość domyślna to `false`.|
|`ItemFound`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy tylko do odczytu.<br /><br /> Pierwszy pasujący element znajduje się na liście, jeśli istnieje.|
|`ItemSpecToFind`|Wymagany parametr interfejsu `String`.<br /><br /> Specyfikacja_elementu do wyszukania.|
|`List`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Lista, w której ma zostać wyszukana wartość specyfikacja_elementu.|
|`MatchFileNameOnly`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` dopasowuje się tylko do części nazwy pliku specyfikacja_elementu; w przeciwnym razie dopasowuje się do całej klasy specyfikacja_elementu. Wartość domyślna to `true`.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
