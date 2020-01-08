---
title: FindUnderPath — — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FindUnderPath task
- FindUnderPath task [MSBuild]
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33912df490b148c91c2a0d152f979bd6149d8ae3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566075"
---
# <a name="findunderpath-task"></a>FindUnderPath — zadanie
Określa, które elementy w określonej kolekcji elementów mają ścieżki, które znajdują się w lub poniżej określonego folderu.

## <a name="parameters"></a>Parametry
W poniższej tabeli opisano parametry zadania `FindUnderPath`.

|Parametr|Opis|
|---------------|-----------------|
|`Files`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa pliki, których ścieżki należy porównać ze ścieżką określoną przez parametr `Path`.|
|`InPath`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Zawiera elementy, które zostały znalezione pod określoną ścieżką.|
|`OutOfPath`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Zawiera elementy, które nie zostały odnalezione w określonej ścieżce.|
|`Path`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa ścieżkę folderu, która ma być używana jako odwołanie.|
|`UpdateToAbsolutePaths`|Opcjonalny parametr `Boolean`.<br /><br /> W przypadku wartości true ścieżki elementów wyjściowych są aktualizowane jako ścieżki bezwzględne.|

## <a name="remarks"></a>Uwagi
Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład
Poniższy przykład używa zadania `FindUnderPath`, aby określić, czy pliki zawarte w elemencie `MyFiles` mają ścieżki istniejące w ścieżce określonej przez właściwość `SearchPath`. Po zakończeniu zadania `FilesNotFoundInPath` element zawiera plik *plik1. txt* , a element `FilesFoundInPath` zawiera plik *plik2. txt* .

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MyFiles Include="C:\File1.txt" />
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />
    </ItemGroup>

    <PropertyGroup>
        <SearchPath>C:\Projects\MyProject</SearchPath>
    </PropertyGroup>

    <Target Name="FindFiles">
        <FindUnderPath
            Files="@(MyFiles)"
            Path="$(SearchPath)">
            <Output
                TaskParameter="InPath"
                ItemName="FilesFoundInPath" />
            <Output
                TaskParameter="OutOfPath"
                ItemName="FilesNotFoundInPath" />
        </FindUnderPath>
    </Target>

</Project>
```

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
