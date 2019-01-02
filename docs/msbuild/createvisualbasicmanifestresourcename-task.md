---
title: Createvisualbasicmanifestresourcename — zadanie | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 948b27aa9e2b800929d9f507535aee1395d45344
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871229"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName — zadanie
Tworzy [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]— styl nazwy manifestu z danym *resx* nazwa pliku lub innego zasobu.  

## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry [createvisualbasicmanifestresourcename — zadanie](../msbuild/createvisualbasicmanifestresourcename-task.md).  


| Parametr | Opis |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem> `[]` Parametr tylko do odczytu danych wyjściowych.<br /><br /> Wynikowy nazwy manifestu. |
| `ResourceFiles` | Wymagane `String` parametru.<br /><br /> Nazwa pliku zasobów, z której ma zostać utworzona [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nazwy manifestu. |
| `RootNamespace` | Opcjonalnie `String` parametru.<br /><br /> Przestrzeń nazw głównego pliku zasobów, zwykle pobierane z pliku projektu. Może być `null`. |
| `PrependCultureAsDirectory` | Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, nazwa kultury jest dodawany jako nazwę katalogu, tuż przed nazwę zasobu manifestu. Wartość domyślna to `true`. |
| `ResourceFilesWithManifestResourceNames` | Opcjonalnie, tylko do odczytu `String` parametr wyjściowy.<br /><br /> Zwraca nazwę pliku zasobu, który teraz zawiera nazwę zasobu manifestu. |

## <a name="remarks"></a>Uwagi  
 [Createvisualbasicmanifestresourcename — zadanie](../msbuild/createvisualbasicmanifestresourcename-task.md) Określa nazwę odpowiedniego zasobu manifestu, można przypisać do danej *resx* lub inny plik zasobów. Zadanie zawiera nazwę logiczną do pliku zasobów i dołącza go do parametru wyjściowego jako metadane.  

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  

## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)