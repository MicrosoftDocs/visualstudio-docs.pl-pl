---
title: WriteLinesToFile Zadanie | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630668"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile — zadanie

Zapisuje ścieżki określonych elementów do określonego pliku tekstowego.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli `WriteLinestoFile` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`File`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa plik, do który mają być zapisywane elementy.|
|`Lines`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa elementy, które mają być zapisywane w pliku.|
|`Overwrite`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`zadanie zastąpi istniejącą zawartość w pliku.|
|`Encoding`|Parametr `String` opcjonalny.<br /><br /> Wybiera kodowanie znaków, na przykład "Unicode".  Zobacz też <xref:System.Text.Encoding>.|
|`WriteOnlyWhenDifferent`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`określony plik docelowy, jeśli istnieje, zostanie najpierw odczytany w celu porównania z tym, co zostałoby napisane. Jeśli plik jest identyczny, plik nie jest zapisywany na dysku, a sygnatura czasowa zostanie zachowana.|

## <a name="remarks"></a>Uwagi

 Jeśli `Overwrite` `true`jest , tworzy nowy plik, zapisz zawartość do pliku, a następnie zamyka plik. Jeśli plik docelowy już istnieje, zostanie zastąpiony. Jeśli `Overwrite` `false`tak, dołącza zawartość do pliku, tworząc plik docelowy, jeśli jeszcze nie istnieje.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 W poniższym przykładzie `WriteLinesToFile` użyto zadania do zapisania `MyItems` ścieżek elementów w `MyTextFile` kolekcji elementów do pliku określonego przez kolekcję elementów.

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

W tym przykładzie używamy właściwości z osadzonymi nowymi wierszami do pisania pliku tekstowego z wieloma wierszami. Jeśli wpis `Lines` w ma osadzone znaki nowego wiersza, nowe wiersze zostaną uwzględnione w pliku wyjściowym. W ten sposób można odwoływać się do właściwości wieloliniowych.

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
