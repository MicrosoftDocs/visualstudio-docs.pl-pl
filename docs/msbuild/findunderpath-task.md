---
title: Zadanie FindUnderPath | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 4d97b727dcba8cd16fe97ee33764947797c36db7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634139"
---
# <a name="findunderpath-task"></a>FindUnderPath — zadanie

Określa, które elementy w kolekcji określonego elementu mają ścieżki, które znajdują się w lub poniżej określonego folderu.

## <a name="parameters"></a>Parametry

W poniższej tabeli `FindUnderPath` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Files`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa pliki, których ścieżki powinny być porównywane `Path` ze ścieżką określoną przez parametr.|
|`InPath`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Zawiera elementy, które zostały znalezione w ramach określonej ścieżki.|
|`OutOfPath`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Zawiera elementy, które nie zostały znalezione w ramach określonej ścieżki.|
|`Path`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa ścieżkę folderu, która ma być używana jako odwołanie.|
|`UpdateToAbsolutePaths`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli true, ścieżki elementów wyjściowych są aktualizowane jako ścieżki bezwzględne.|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład używa `FindUnderPath` zadania, aby ustalić, czy `MyFiles` pliki zawarte w elemencie `SearchPath` mają ścieżki, które istnieją w ścieżce określonej przez właściwość. `FilesNotFoundInPath` Po zakończeniu zadania element zawiera plik *File1.txt,* `FilesFoundInPath` a element zawiera plik *File2.txt.*

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

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
