---
title: ResolveNativeReference — — zadanie | Microsoft Docs
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 417c4536f13aa90505ec5e69b2719219af0d7e81
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595166"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference — zadanie
Rozwiązuje odwołania natywne. Implementuje klasę <xref:Microsoft.Build.Tasks.ResolveNativeReference>. Ta klasa obsługuje infrastrukturę .NET Framework, która nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="task-parameters"></a>Parametry zadania
 W poniższej tabeli opisano parametry zadania `ResolveNativeReference`.

|Parametr|Opis|
|---------------|-----------------|
|`AdditionalSearchPaths`|Wymagany parametr interfejsu <xref:System.String?displayProperty=fullName>`[]`.<br /><br /> Pobiera lub ustawia ścieżki wyszukiwania służące do rozpoznawania tożsamości zestawów natywnych odwołań.|
|`ContainedComComponents`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Pobiera lub ustawia składniki COM zestawu macierzystego.|
|`ContainedLooseEtcFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Pobiera lub ustawia pliki luźne *etc* wymienione w manifeście natywnym.|
|`ContainedLooseTlbFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Pobiera lub ustawia luźne pliki *TLB* zestawu natywnego.|
|`ContainedPrerequisiteAssemblies`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Pobiera lub ustawia zestawy, które muszą być obecne, aby można było użyć manifestu.|
|`ContainedTypeLibraries`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Pobiera lub ustawia biblioteki typów macierzystego zestawu.|
|`ContainingReferenceFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Pobiera lub ustawia pliki referencyjne.|
|`NativeReferences`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Pobiera lub ustawia natywne odwołania do zestawu Win32.|

## <a name="remarks"></a>Uwagi
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
