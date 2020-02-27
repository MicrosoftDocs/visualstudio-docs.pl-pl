---
title: ReadLinesFromFile — — zadanie | Microsoft Docs
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
ms.openlocfilehash: 7c926c131fab101563841bea3362e88e27674226
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632904"
---
# <a name="readlinesfromfile-task"></a>ReadLinesFromFile — zadanie

Odczytuje listę elementów z pliku tekstowego.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania `ReadLinesFromFile`.

|Parametr|Opis|
|---------------|-----------------|
|`File`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa plik, który ma zostać odczytany. Plik musi zawierać jeden element w każdym wierszu.|
|`Lines`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Zawiera wiersze odczytane z pliku.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład używa zadania `ReadLinesFromFile`, aby utworzyć elementy z listy w pliku tekstowym. Elementy odczytane z pliku są przechowywane w kolekcji elementów `ItemsFromFile`.

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

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [Zadania](../msbuild/msbuild-tasks.md)
