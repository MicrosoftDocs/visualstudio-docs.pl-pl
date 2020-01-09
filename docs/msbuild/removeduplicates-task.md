---
title: RemoveDuplicates — — zadanie | Microsoft Docs
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
ms.openlocfilehash: 235f96b3d67b0ad2e3c3bd1c486c5c9f2eeb86c2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596011"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates — zadanie
Usuwa zduplikowane elementy z określonej kolekcji elementów.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania `RemoveDuplicates`.

|Parametr|Opis|
|---------------|-----------------|
|`Filtered`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Zawiera kolekcję elementów z usuniętymi wszystkimi zduplikowanymi elementami. Kolejność elementów wejściowych jest zachowywana, zachowując pierwsze wystąpienie każdego zduplikowanego elementu.|
|`Inputs`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Kolekcja elementów, z której mają zostać usunięte zduplikowane elementy.|

## <a name="remarks"></a>Uwagi
 To zadanie uwzględnia wielkość liter i nie porównuje metadanych elementów podczas określania duplikatów.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład
 W poniższym przykładzie użyto zadania `RemoveDuplicates`, aby usunąć zduplikowane elementy z kolekcji elementów `MyItems`. Po zakończeniu zadania kolekcja `FilteredItems` elementów zawiera jeden element.

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

 Poniższy przykład pokazuje, że zadanie `RemoveDuplicates` zachowuje swoją kolejność wprowadzania danych. Po zakończeniu zadania kolekcja `FilteredItems` elementów zawiera elementy *MyFile2.cs*, *MyFile1.cs*i *MyFile3.cs* w tej kolejności.

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

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [Zadania](../msbuild/msbuild-tasks.md)
