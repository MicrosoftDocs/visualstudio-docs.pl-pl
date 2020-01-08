---
title: Zadanie właściwości | Microsoft Docs
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
ms.openlocfilehash: cac0af3371a5c4ae385cc19367b360b8e8f608fd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590062"
---
# <a name="createproperty-task"></a>CreateProperty — zadanie
Wypełnia właściwości wartościami z przekazaną. Pozwala to na kopiowanie wartości z jednej właściwości lub ciągu do innej.

## <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}
W poniższej tabeli opisano parametry zadania `CreateProperty`.

| Parametr | Opis |
|------------------| - |
| `Value` | Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa wartość, która ma zostać skopiowana do nowej właściwości. |
| `ValueSetByTask` | Opcjonalny `String` parametr wyjściowy.<br /><br /> Zawiera taką samą wartość jak parametr `Value`. Tego parametru należy użyć tylko wtedy, gdy chcesz uniknąć, aby Właściwość Output była ustawiona przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], gdy pomija otaczający element docelowy, ponieważ dane wyjściowe są aktualne. |

## <a name="remarks"></a>Uwagi
Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład
W poniższym przykładzie użyto zadania `CreateProperty`, aby utworzyć właściwość `NewFile` przy użyciu kombinacji wartości właściwości `SourceFilename` i `SourceFileExtension`.

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

Po uruchomieniu projektu wartość właściwości `NewFile` jest *Module1. vb*.

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
