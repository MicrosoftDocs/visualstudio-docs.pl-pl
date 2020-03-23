---
title: Zadanie ResolveNativeReference | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 64b76b31e96947914c9a641ed4ceb23c7761eb85
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632683"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference — zadanie

Rozpoznaje odwołania natywne. Implementuje <xref:Microsoft.Build.Tasks.ResolveNativeReference> klasę. Ta klasa obsługuje infrastrukturę .NET Framework, która nie jest przeznaczona do użycia bezpośrednio z kodu.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli `ResolveNativeReference` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AdditionalSearchPaths`|Wymagany parametr interfejsu <xref:System.String?displayProperty=fullName>`[]`.<br /><br /> Pobiera lub ustawia ścieżki wyszukiwania do rozpoznawania tożsamości zestawu odwołań natywnych.|
|`ContainedComComponents`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Pobiera lub ustawia składniki COM natywnego złożenia.|
|`ContainedLooseEtcFiles`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Pobiera lub ustawia luźne pliki *Etc* wymienione w manifeście macierzystym.|
|`ContainedLooseTlbFiles`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Pobiera lub ustawia luźne *pliki .tlb* natywnego zestawu.|
|`ContainedPrerequisiteAssemblies`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Pobiera lub ustawia zestawy, które muszą być obecne, zanim manifest może być używany.|
|`ContainedTypeLibraries`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Pobiera lub ustawia biblioteki typów zestawu macierzystego.|
|`ContainingReferenceFiles`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Pobiera lub ustawia pliki odwołań.|
|`NativeReferences`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Pobiera lub ustawia odwołania do natywnego zestawu Win32.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
