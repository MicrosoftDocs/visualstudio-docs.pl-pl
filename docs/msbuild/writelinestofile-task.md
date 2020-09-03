---
title: WriteLinesToFile — — zadanie | Microsoft Docs
ms.date: 09/20/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27673ba3691e53540bce2249700c4453cb56c166
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85286105"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile — zadanie

Zapisuje ścieżki określonych elementów do określonego pliku tekstowego.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli opisano parametry `WriteLinestoFile` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`File`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa plik, do którego mają zostać zapisane elementy.|
|`Lines`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa elementy do zapisu w pliku. Wartość domyślna to pusta lista.|
|`Overwrite`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` zadanie zastąpi istniejącą zawartość pliku. Wartość domyślna to `false`.|
|`Encoding`|Opcjonalny `String` parametr.<br /><br /> Wybiera kodowanie znaków, na przykład "Unicode". Wartość domyślna to UTF-8.  Zobacz też <xref:System.Text.Encoding>.|
|`WriteOnlyWhenDifferent`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` plik docelowy zostanie określony (jeśli istnieje), zostanie najpierw odczytany w celu porównania z zapisaniem zadania. Jeśli taka sama, plik nie jest zapisywana na dysku i sygnatura czasowa zostanie zachowana. Wartość domyślna to `false`.|

## <a name="remarks"></a>Uwagi

 Jeśli `Overwrite` jest `true` , tworzy nowy plik, zapisuje zawartość w pliku, a następnie zamyka plik. Jeśli plik docelowy już istnieje, zostanie nadpisany. Jeśli `Overwrite` jest `false` , dołącza zawartość do pliku, tworząc plik docelowy, jeśli jeszcze nie istnieje.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład używa zadania, `WriteLinesToFile` Aby zapisać ścieżki elementów w `MyItems` kolekcji elementów do pliku określonego przez `MyTextFile` kolekcję elementów.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyTextFile Include="Items.txt"/>
        <MyItems Include="*.cs"/>
    </ItemGroup>

    <Target Name="WriteToFile">
        <WriteLinesToFile
            File="@(MyTextFile)"
            Lines="@(MyItems)"
            Overwrite="true"
            Encoding="Unicode"/>
    </Target>

</Project>
```

W tym przykładzie użyto właściwości z osadzonym znakiem nowego wiersza, aby napisać plik tekstowy z wieloma wierszami. Jeśli wpis w `Lines` zawiera osadzone znaki nowego wiersza, nowe wiersze zostaną uwzględnione w pliku wyjściowym. W ten sposób można odwoływać się do wielowierszowych właściwości.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <Target Name="WriteLaunchers" AfterTargets="CopyFilesToOutputDirectory">
      <PropertyGroup>
        <LauncherCmd>
@ECHO OFF
dotnet %~dp0$(AssemblyName).dll %*
        </LauncherCmd>
      </PropertyGroup>

      <WriteLinesToFile
        File="$(OutputPath)$(AssemblyName).cmd"
        Overwrite="true"
        Lines="$(LauncherCmd)" />
  </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
