---
title: MakeDir — zadanie | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa zadania MakeDir do tworzenia katalogów i, w razie potrzeby, wszystkich katalogów nadrzędnych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MakeDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MakeDir task [MSBuild]
- MSBuild, MakeDir task
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fa7b853ea6706c4958635c399bbc6134e823223c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966230"
---
# <a name="makedir-task"></a>MakeDir — zadanie

Tworzy katalogi i, w razie potrzeby, wszystkie katalogi nadrzędne.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry `MakeDir` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Directories`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Zestaw katalogów do utworzenia.|
|`DirectoriesCreated`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Katalogi, które są tworzone przez to zadanie. Jeśli nie można utworzyć niektórych katalogów, może to nie zawierać wszystkich elementów, które zostały przesłane do `Directories` parametru.|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład kodu używa `MakeDir` zadania do utworzenia katalogu określonego przez `OutputDirectory` Właściwość.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <OutputDirectory>\Output\</OutputDirectory>
    </PropertyGroup>

    <Target Name="CreateDirectories">
        <MakeDir
            Directories="$(OutputDirectory)"/>
    </Target>

</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
