---
title: Zadanie FindInList | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634152"
---
# <a name="findinlist-task"></a>FindInList — zadanie

Na określonej liście znajduje element, który ma pasujące itemspec.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry [zadania FindInList](../msbuild/findinlist-task.md).

|Parametr|Opis|
|---------------|-----------------|
|`CaseSensitive`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`w wyszukiwaniu rozróżniana jest wielkość liter; w przeciwnym razie tak nie jest. Wartością `true`domyślną jest .|
|`FindLastMatch`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, powrót ostatniego dopasowania; w przeciwnym razie zwróć pierwszy mecz. Wartością `false`domyślną jest .|
|`ItemFound`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy tylko do odczytu.<br /><br /> Pierwszy pasujący element znaleziony na liście, jeśli istnieje.|
|`ItemSpecToFind`|Wymagany parametr interfejsu `String`.<br /><br /> Itemspec do wyszukania.|
|`List`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Lista, na której ma być wyszukiwana itemspec.|
|`MatchFileNameOnly`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, dopasować tylko część nazwy pliku itemspec; w przeciwnym razie, dopasować do całego itemspec. Wartością `true`domyślną jest .|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
