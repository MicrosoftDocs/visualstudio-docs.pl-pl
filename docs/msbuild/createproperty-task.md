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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d7dd8d7f5a50998832a8fac6f47bf66e9a6bbe9
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796190"
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

Po uruchomieniu projektu wartość `NewFile` właściwości jest *Module1. vb* .

## <a name="see-also"></a>Zobacz także

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
