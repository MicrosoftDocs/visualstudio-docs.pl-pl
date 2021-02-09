---
title: CreateVisualBasicManifestResourceName — — Zadanie | Microsoft Docs
description: Przy użyciu zadania CreateVisualBasicManifestResourceName — programu MSBuild można utworzyć nazwę manifestu Visual Basic na podstawie danej nazwy pliku resx lub innego zasobu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8e9f0868cb774ee82c79ba190acddebf63193cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901383"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName — zadanie

Tworzy nazwę manifestu Visual Basic w stylu na podstawie danej nazwy pliku *resx* lub innego zasobu.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry [zadania CreateVisualBasicManifestResourceName —](../msbuild/createvisualbasicmanifestresourcename-task.md).

| Parametr | Opis |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem>`[]`wyjściowy parametr tylko do odczytu.<br /><br /> Nazwy manifestów. |
| `ResourceFiles` | Wymagany parametr interfejsu `String`.<br /><br /> Nazwa pliku zasobów, z którego ma zostać utworzona Nazwa manifestu Visual Basic. |
| `RootNamespace` | Opcjonalny `String` parametr.<br /><br /> Główna przestrzeń nazw pliku zasobów, zazwyczaj pobierana z pliku projektu. Może być `null` . |
| `PrependCultureAsDirectory` | Opcjonalny `Boolean` parametr.<br /><br /> Jeśli nazwa `true` kultury zostanie dodana jako nazwa katalogu tuż przed nazwą zasobu manifestu. Wartość domyślna to `true`. |
| `ResourceFilesWithManifestResourceNames` | Opcjonalny parametr wyjściowy tylko do odczytu `String` .<br /><br /> Zwraca nazwę pliku zasobu, który zawiera teraz nazwę zasobu manifestu. |

## <a name="remarks"></a>Uwagi

 [Zadanie CreateVisualBasicManifestResourceName —](../msbuild/createvisualbasicmanifestresourcename-task.md) określa odpowiednią nazwę zasobu manifestu, która ma zostać przypisana do danego pliku *resx* lub innego zasobu. Zadanie zawiera nazwę logiczną pliku zasobów, a następnie dołącza ją do parametru wyjściowego jako metadane.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
