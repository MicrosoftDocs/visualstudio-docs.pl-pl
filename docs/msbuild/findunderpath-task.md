---
title: FindUnderPath — — zadanie | Microsoft Docs
description: Za pomocą zadania MSBuild FindUnderPath — Znajdź elementy w określonej kolekcji elementów ze ścieżkami w lub poniżej określonego folderu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 82275b14fbda0d63e6235b87b55a0dbb5f2416b0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949431"
---
# <a name="findunderpath-task"></a>FindUnderPath — zadanie

Określa, które elementy w określonej kolekcji elementów mają ścieżki, które znajdują się w lub poniżej określonego folderu.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry `FindUnderPath` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Files`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa pliki, których ścieżki należy porównać ze ścieżką określoną przez `Path` parametr.|
|`InPath`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera elementy, które zostały znalezione pod określoną ścieżką.|
|`OutOfPath`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera elementy, które nie zostały odnalezione w określonej ścieżce.|
|`Path`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa ścieżkę folderu, która ma być używana jako odwołanie.|
|`UpdateToAbsolutePaths`|Opcjonalny `Boolean` parametr.<br /><br /> W przypadku wartości true ścieżki elementów wyjściowych są aktualizowane jako ścieżki bezwzględne.|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład używa zadania, `FindUnderPath` Aby określić, czy pliki zawarte w `MyFiles` elemencie mają ścieżki istniejące w ścieżce określonej przez `SearchPath` Właściwość. Po zakończeniu zadania `FilesNotFoundInPath` element zawiera plik *File1.txt* , a `FilesFoundInPath` element zawiera plik *File2.txt* .

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

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
