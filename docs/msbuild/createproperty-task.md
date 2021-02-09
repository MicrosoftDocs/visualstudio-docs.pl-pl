---
title: Zadanie właściwości | Microsoft Docs
description: Zadanie programu MSBuild. Property służy do wypełniania właściwości wartościami przekazywania, co umożliwia kopiowanie wartości z jednej właściwości lub ciągu do innej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6ea412f67629998eab035b8cca79111659ab8a0c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901366"
---
# <a name="createproperty-task"></a>CreateProperty — zadanie

Wypełnia właściwości wartościami z przekazaną. Pozwala to na kopiowanie wartości z jednej właściwości lub ciągu do innej.

## <a name="attributes"></a>Atrybuty

W poniższej tabeli opisano parametry `CreateProperty` zadania.

| Parametr | Opis |
|------------------| - |
| `Value` | Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa wartość, która ma zostać skopiowana do nowej właściwości. |
| `ValueSetByTask` | Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera tę samą wartość, co `Value` parametr. Tego parametru należy użyć tylko wtedy, gdy nie ma właściwości Output ustawionej przez MSBuild, gdy pomija otaczający element docelowy, ponieważ dane wyjściowe są aktualne. |

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie użyto `CreateProperty` zadania do utworzenia `NewFile` właściwości przy użyciu kombinacji wartości `SourceFilename` `SourceFileExtension` właściwości i.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <SourceFilename>Module1</SourceFilename>
        <SourceFileExtension>vb</SourceFileExtension>
    </PropertyGroup>

    <Target Name="CreateProperties">

        <CreateProperty
            Value="$(SourceFilename).$(SourceFileExtension)">
            <Output
                TaskParameter="Value"
                PropertyName="NewFile" />
        </CreateProperty>

    </Target>

</Project>
```

Po uruchomieniu projektu wartość `NewFile` właściwości jest *Module1. vb*.

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
