---
title: CreateVisualBasicManifestResourceName — — Zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 636cd4a7d287f60235f3827837050efa1e15eb90
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596921"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName — zadanie
Tworzy nazwę manifestu [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]w stylu na podstawie danej nazwy pliku *resx* lub innego zasobu.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry [zadania CreateVisualBasicManifestResourceName —](../msbuild/createvisualbasicmanifestresourcename-task.md).

| Parametr | Opis |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem> `[]` wyjściowego parametru tylko do odczytu.<br /><br /> Nazwy manifestów. |
| `ResourceFiles` | Wymagany `String` parametr.<br /><br /> Nazwa pliku zasobów, z którego ma zostać utworzona Nazwa manifestu [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. |
| `RootNamespace` | Opcjonalny parametr `String`.<br /><br /> Główna przestrzeń nazw pliku zasobów, zazwyczaj pobierana z pliku projektu. Może być `null`. |
| `PrependCultureAsDirectory` | Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, nazwa kultury zostanie dodana jako nazwa katalogu tuż przed nazwą zasobu manifestu. Wartość domyślna to `true`. |
| `ResourceFilesWithManifestResourceNames` | Opcjonalny parametr wyjściowy `String` tylko do odczytu.<br /><br /> Zwraca nazwę pliku zasobu, który zawiera teraz nazwę zasobu manifestu. |

## <a name="remarks"></a>Uwagi
 [Zadanie CreateVisualBasicManifestResourceName —](../msbuild/createvisualbasicmanifestresourcename-task.md) określa odpowiednią nazwę zasobu manifestu, która ma zostać przypisana do danego pliku *resx* lub innego zasobu. Zadanie zawiera nazwę logiczną pliku zasobów, a następnie dołącza ją do parametru wyjściowego jako metadane.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
