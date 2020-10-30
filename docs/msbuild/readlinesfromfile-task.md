---
title: ReadLinesFromFile — — zadanie | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild odczytuje listę elementów z pliku tekstowego przy użyciu zadania ReadLinesFromFile —. Plik musi zawierać jeden element w każdym wierszu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ReadLinesFromFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ReadLinesFromFile task
- ReadLinesFromFile task [MSBuild]
ms.assetid: a18af929-b53a-4d9e-b7bf-e3d3737ee85f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff2c43af40ea429714f0624db67c53fa46eb6427
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048779"
---
# <a name="readlinesfromfile-task"></a>ReadLinesFromFile — zadanie

Odczytuje listę elementów z pliku tekstowego.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `ReadLinesFromFile` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`File`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa plik, który ma zostać odczytany. Plik musi zawierać jeden element w każdym wierszu.|
|`Lines`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera wiersze odczytane z pliku.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład używa `ReadLinesFromFile` zadania do tworzenia elementów z listy w pliku tekstowym. Elementy odczytane z pliku są przechowywane w `ItemsFromFile` kolekcji elementów.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyTextFile Include="Items.txt"/>
    </ItemGroup>

    <Target Name="ReadFromFile">
        <ReadLinesFromFile
            File="@(MyTextFile)" >
            <Output
                TaskParameter="Lines"
                ItemName="ItemsFromFile"/>
        </ReadLinesFromFile>
    </Target>

</Project>
```

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [Zadania](../msbuild/msbuild-tasks.md)
