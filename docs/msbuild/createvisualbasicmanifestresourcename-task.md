---
title: Utwórz zadanie CreateVisualBasicManifestResourceName | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 6aa419001d2e890c87873862f0575607b31d22c2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634295"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName — zadanie

Tworzy nazwę manifestu w stylu języka Visual Basic z podanej nazwy pliku *resx* lub innego zasobu.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry [zadania CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md).

| Parametr | Opis |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem>`[]` wyjściowego parametru tylko do odczytu.<br /><br /> Wynikowe nazwy manifestu. |
| `ResourceFiles` | Wymagany parametr interfejsu `String`.<br /><br /> Nazwa pliku zasobu, z którego ma być tworzę nazwę manifestu języka Visual Basic. |
| `RootNamespace` | Parametr `String` opcjonalny.<br /><br /> Główny obszar nazw pliku zasobów, zwykle pobrany z pliku projektu. Może `null`być . |
| `PrependCultureAsDirectory` | Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`nazwa kultury jest dodawana jako nazwa katalogu tuż przed nazwą zasobu manifestu. Wartością `true`domyślną jest . |
| `ResourceFilesWithManifestResourceNames` | Opcjonalny parametr `String` wyjściowy tylko do odczytu.<br /><br /> Zwraca nazwę pliku zasobu, który teraz zawiera nazwę zasobu manifestu. |

## <a name="remarks"></a>Uwagi

 [Zadanie CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) określa odpowiednią nazwę zasobu manifestu do przypisania do danego pliku *.resx* lub innego pliku zasobów. Zadanie zawiera nazwę logiczną do pliku zasobów, a następnie dołącza go do parametru wyjściowego jako metadane.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
