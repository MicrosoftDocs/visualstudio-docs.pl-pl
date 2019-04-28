---
title: Readlinesfromfile — zadanie | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3b08ab26b30abe767674d51795dd4f3a4cfac01
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974634"
---
# <a name="readlinesfromfile-task"></a>ReadLinesFromFile — zadanie
Odczytuje listę elementów z pliku tekstowego.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry `ReadLinesFromFile` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`File`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa plik do odczytu. Nazwa pliku musi mieć jedną pozycję w każdym wierszu.|
|`Lines`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera wiersze odczytu z pliku.|

## <a name="remarks"></a>Uwagi
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład
 W poniższym przykładzie użyto `ReadLinesFromFile` zadanie tworzenia elementów z listy w pliku tekstowym. Elementy odczytu z pliku są przechowywane w `ItemsFromFile` elementu kolekcji.

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

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [Zadania](../msbuild/msbuild-tasks.md)