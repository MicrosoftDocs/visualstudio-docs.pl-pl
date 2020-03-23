---
title: RemoveDuplicates Zadanie | Dokumenty firmy Microsoft
ms.date: 03/01/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90366bab14eefd1be4edac81d6b09b3f57aa3332
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632787"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates — zadanie

Usuwa zduplikowane elementy z określonej kolekcji towarów.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `RemoveDuplicates` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Filtered`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Zawiera kolekcję elementów z usuniętymi wszystkimi zduplikowanymi elementami. Kolejność elementów wejściowych jest zachowywana, zachowując pierwsze wystąpienie każdego zduplikowanego elementu.|
|`Inputs`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Kolekcja towarów, z którego można usunąć zduplikowane elementy.|

## <a name="remarks"></a>Uwagi

 To zadanie jest niewrażliwe na wielkości i nie porównuje metadanych elementu podczas określania duplikatów.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 W poniższym przykładzie `RemoveDuplicates` użyto zadania, `MyItems` aby usunąć zduplikowane elementy z kolekcji towarów. Po zakończeniu zadania kolekcja `FilteredItems` elementów zawiera jeden element.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyItems Include="MyFile.cs"/>
        <MyItems Include="MyFile.cs">
            <Culture>fr</Culture>
        </MyItems>
        <MyItems Include="myfile.cs"/>
    </ItemGroup>

    <Target Name="RemoveDuplicateItems">
        <RemoveDuplicates
            Inputs="@(MyItems)">
            <Output
                TaskParameter="Filtered"
                ItemName="FilteredItems"/>
        </RemoveDuplicates>
    </Target>
</Project>
```

 Poniższy przykład pokazuje, że `RemoveDuplicates` zadanie zachowuje jego kolejność wprowadzania. Po zakończeniu zadania kolekcja `FilteredItems` zapasów zawiera elementy *MyFile2.cs ,* *MyFile1.cs*i *MyFile3.cs* w tej kolejności.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyItems Include="MyFile2.cs"/>
        <MyItems Include="MyFile1.cs" />
        <MyItems Include="MyFile3.cs" />
        <MyItems Include="myfile1.cs"/>
    </ItemGroup>

    <Target Name="RemoveDuplicateItems">
        <RemoveDuplicates
            Inputs="@(MyItems)">
            <Output
                TaskParameter="Filtered"
                ItemName="FilteredItems"/>
        </RemoveDuplicates>
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
- [Zadania](../msbuild/msbuild-tasks.md)
