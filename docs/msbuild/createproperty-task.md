---
title: Tworzenieproperty Zadanie | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 155e8e6b57cc388e8c2981297be8b26ef5444c1b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634321"
---
# <a name="createproperty-task"></a>CreateProperty — zadanie

Wypełnia właściwości z wartościami przekazanymi. Dzięki temu wartości mają być kopiowane z jednej właściwości lub ciągu do innej.

## <a name="attributes"></a>Atrybuty

W poniższej tabeli `CreateProperty` opisano parametry zadania.

| Parametr | Opis |
|------------------| - |
| `Value` | Opcjonalny parametr wyjściowy. `String`<br /><br /> Określa wartość do skopiowania do nowej właściwości. |
| `ValueSetByTask` | Opcjonalny parametr wyjściowy. `String`<br /><br /> Zawiera taką samą `Value` wartość jak parametr. Ten parametr należy używać tylko wtedy, gdy chcesz uniknąć właściwości wyjściowej ustawionej przez MSBuild, gdy pomija otaczający obiekt docelowy, ponieważ dane wyjściowe są aktualne. |

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

W poniższym `CreateProperty` przykładzie użyto `NewFile` zadania do utworzenia właściwości `SourceFilename` `SourceFileExtension` przy użyciu kombinacji wartości i właściwości.

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

Po uruchomieniu projektu, wartość `NewFile` właściwości jest *Module1.vb*.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
