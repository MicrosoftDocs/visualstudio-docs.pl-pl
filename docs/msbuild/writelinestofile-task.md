---
title: Writelinestofile — zadanie | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cfe294e94acce70f48b96265b3edc491b37e668
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56653879"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile — zadanie
Zapisuje ścieżek określonych elementów do określonego pliku.

## <a name="task-parameters"></a>Parametry zadania
 W poniższej tabeli opisano parametry `WriteLinestoFile` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`File`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa plik do elementów do zapisania.|
|`Lines`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa elementy do zapisu w pliku.|
|`Overwrite`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie zastępuje istniejącą zawartość w pliku.|
|`Encoding`|Opcjonalnie `String` parametru.<br /><br /> Wybiera kodowanie, na przykład "Unicode" znaków.  Zobacz też <xref:System.Text.Encoding>.|
|`WriteOnlyWhenDifferent`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, plik docelowy określony, jeśli istnieje, zostanie odczytany najpierw, aby porównać co zadania, musieli napisać. Jeśli taka sama, plik nie jest zapisywany na dysku i sygnaturę czasową zostaną zachowane.|

## <a name="remarks"></a>Uwagi
 Jeśli `Overwrite` jest `true`, tworzy nowy plik, zapisywania zawartości pliku, a następnie zamyka plik. Jeśli plik docelowy już istnieje, zostanie zastąpiony. Jeśli `Overwrite` jest `false`, dołącza zawartość do pliku, tworzenia pliku docelowego, jeśli jeszcze nie istnieje.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład
 W poniższym przykładzie użyto `WriteLinesToFile` zadanie, aby zapisać ścieżki elementów w `MyItems` elementu kolekcji do pliku określonego przez `MyTextFile` elementu kolekcji.

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

W tym przykładzie używamy właściwości z osadzonych oddzielane do wpisywanie tekstu do pliku z wieloma wierszami. Jeśli wpis w `Lines` zawierający osadzone znaki nowego wiersza, nowe wiersze, które zostaną uwzględnione w pliku wyjściowym. W ten sposób możesz odwoływać się właściwości wiele wierszy.

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

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
