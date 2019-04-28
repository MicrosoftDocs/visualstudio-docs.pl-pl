---
title: Resolvenativereference — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f18549fece2db8a4a758dee17f6b4b1283d97e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996614"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference — zadanie
Usuwa odwołania natywne. Implementuje <xref:Microsoft.Build.Tasks.ResolveNativeReference> klasy. Ta klasa obsługuje infrastrukturę .NET Framework, która nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="task-parameters"></a>Parametry zadania
 W poniższej tabeli opisano parametry `ResolveNativeReference` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AdditionalSearchPaths`|Wymagany parametr interfejsu <xref:System.String?displayProperty=fullName>`[]`.<br /><br /> Pobiera lub ustawia Przeszukuj ścieżki pod kątem rozpoznawania tożsamości zestawu odwołania natywne.|
|`ContainedComComponents`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Pobiera lub ustawia składników COM natywnego zestawu.|
|`ContainedLooseEtcFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Pobiera lub ustawia luźne *itp* plików na liście natywny manifest.|
|`ContainedLooseTlbFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Pobiera lub ustawia luźne *.tlb* pliki natywny zestaw.|
|`ContainedPrerequisiteAssemblies`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Pobiera lub ustawia zestawów, które musi znajdować się przed użyciem manifestu.|
|`ContainedTypeLibraries`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Pobiera lub ustawia biblioteki typu zestawu macierzystego.|
|`ContainingReferenceFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Pobiera lub ustawia pliki odwołań.|
|`NativeReferences`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Pobiera lub ustawia odwołania do zestawów natywnych Win32.|

## <a name="remarks"></a>Uwagi
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)