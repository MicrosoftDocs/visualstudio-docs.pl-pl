---
title: CombinePath — — zadanie | Microsoft Docs
description: Dowiedz się więcej na temat używania zadania CombinePath — programu MSBuild do łączenia określonych ścieżek w jedną ścieżkę.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc33c3a413d788bd9a5a30a7db69c4c7766a3392
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796618"
---
# <a name="combinepath-task"></a>CombinePath — zadanie

Łączy określone ścieżki w jedną ścieżkę.
## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli opisano parametry [zadania CombinePath —](../msbuild/combinepath-task.md).


|Parametr|Opis|
|---------------|-----------------|
|`BasePath`|Wymagany parametr interfejsu `String`.<br /><br /> Ścieżka podstawowa, która ma zostać połączona z innymi ścieżkami. Może być ścieżką względną, ścieżką bezwzględną lub pustą.|
|`Paths`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Lista poszczególnych ścieżek do połączenia z BasePath w celu utworzenia połączonej ścieżki. Ścieżki mogą być względne lub bezwzględne.|
|`CombinedPaths`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Połączona Ścieżka utworzona przez to zadanie.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

 Poniższy przykład pokazuje, jak utworzyć strukturę folderu wyjściowego przy użyciu, `CombinePath` Aby skonstruować Właściwość `$(OutputDirectory)` przez połączenie ścieżki głównej `$(PublishRoot)` połączonej z `$(ReleaseDirectory)` i listy podfolderów `$(LangDirectories)` .

 ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <PublishRoot>C:\Site1\Release</PublishRoot>
  </PropertyGroup>

  <ItemGroup>
    <LangDirectories Include="en-us\;fr-fr\"/>
  </ItemGroup>

  <Target Name="CreateOutputDirectories" AfterTargets="Build">
    <CombinePath BasePath="$(PublishRoot)" Paths="@(LangDirectories)" >
      <Output TaskParameter="CombinedPaths" ItemName="OutputDirectories"/>
    </CombinePath>
    <MakeDir Directories="@(OutputDirectories)" />
  </Target>
```

Jedyną właściwością, która może `CombinePath` być listą `Paths` , w tym przypadku dane wyjściowe są również listą. Tak więc, `$(PublishRoot)` Jeśli *jest \\ C:\Site1* , `$(ReleaseDirectory)` a *wersja \\* to `@(LangDirectories)` *en-us \; fr- \\ fr* , to przykłady te tworzą foldery:

- C:\Site1\Release\en-us\
- C:\Site1\Release\fr-fr\

## <a name="see-also"></a>Zobacz także

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
