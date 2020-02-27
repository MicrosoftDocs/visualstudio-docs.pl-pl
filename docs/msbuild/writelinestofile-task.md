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
ms.openlocfilehash: b78ac2347a5143aeb532a4bcc294551430584b4a
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630668"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile — zadanie

Zapisuje ścieżki określonych elementów do określonego pliku tekstowego.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli opisano parametry zadania `WriteLinestoFile`.

|Parametr|Opis|
|---------------|-----------------|
|`File`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa plik, do którego mają zostać zapisane elementy.|
|`Lines`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa elementy do zapisu w pliku.|
|`Overwrite`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, zadanie zastąpi istniejącą zawartość pliku.|
|`Encoding`|Opcjonalny parametr `String`.<br /><br /> Wybiera kodowanie znaków, na przykład "Unicode".  Zobacz również <xref:System.Text.Encoding>.|
|`WriteOnlyWhenDifferent`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, określony plik docelowy, jeśli istnieje, zostanie najpierw odczytany, aby porównać się z zapisaniem zadania. Jeśli taka sama, plik nie jest zapisywana na dysku i sygnatura czasowa zostanie zachowana.|

## <a name="remarks"></a>Uwagi

 Jeśli `Overwrite` jest `true`, program utworzy nowy plik, zapisze zawartość w pliku, a następnie zamknie plik. Jeśli plik docelowy już istnieje, zostanie nadpisany. Jeśli `Overwrite` jest `false`, dołącza zawartość do pliku, tworząc plik docelowy, jeśli jeszcze nie istnieje.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład używa zadania `WriteLinesToFile`, aby napisać ścieżki elementów w kolekcji elementów `MyItems` do pliku określonego przez kolekcję `MyTextFile` elementów.

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
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
