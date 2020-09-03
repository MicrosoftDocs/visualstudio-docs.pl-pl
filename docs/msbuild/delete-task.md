---
title: Usuń zadanie | Microsoft Docs
ms.date: 06/11/2020
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eddb9804378a4c32de9d1b68f952bc715f32ffd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288913"
---
# <a name="delete-task"></a>Delete — Zadanie

Usuwa określone pliki.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry `Delete` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`DeletedFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa pliki, które zostały pomyślnie usunięte.|
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki do usunięcia.|
|`TreatErrorsAsWarnings`|`Boolean`Parametr opcjonalny<br /><br /> Jeśli `true` Błędy są rejestrowane jako ostrzeżenia. Wartość domyślna to `false`.|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Należy zachować ostrożność w przypadku używania symboli wieloznacznych z `Delete` zadaniem. Można łatwo usunąć niewłaściwe pliki z wyrażeniami, takimi jak `$(SomeProperty)\**\*.*` lub `$(SomeProperty)/**/*.*` , zwłaszcza jeśli właściwość zwraca pusty ciąg, w takim przypadku `Files` parametr może zostać oceniony jako katalog główny dysku i usunąć wiele więcej niż chcesz usunąć.

## <a name="example"></a>Przykład

Poniższy przykład usuwa plik *MojaApl. pdb* podczas kompilowania `DeleteDebugSymbolFile` obiektu docelowego.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

    <PropertyGroup>
        <AppName>ConsoleApp1</AppName>
    </PropertyGroup>

    <Target Name="DeleteDebugSymbolFile">
        <Message Text="Deleting $(OutDir)$(AppName).pdb"/>
        <Delete Files="$(OutDir)$(AppName).pdb" />
    </Target>
  
</Project>

```

Jeśli chcesz śledzić usunięte pliki, ustaw `TaskParameter` na wartość `DeletedFiles` przy użyciu nazwy elementu w następujący sposób:

```xml
      <Target Name="DeleteDebugSymbolFile">
        <Delete Files="$(OutDir)$(AppName).pdb" >
              <Output TaskParameter="DeletedFiles" ItemName="DeletedList"/>
        </Delete>
        <Message Text="Deleted files: '@(DeletedList)'"/>
    </Target>
```

Zamiast bezpośrednio korzystać z symboli wieloznacznych w `Delete` zadaniu, Utwórz `ItemGroup` pliki do usunięcia i uruchomienia `Delete` zadania. Pamiętaj jednak, aby `ItemGroup` uważnie umieścić. Jeśli umieścisz `ItemGroup` na najwyższego poziomu w pliku projektu, zostanie on obliczony na początku, przed rozpoczęciem kompilacji, więc nie będzie zawierać żadnych plików, które zostały skompilowane jako część procesu kompilacji. W tym celu należy umieścić element, `ItemGroup` który tworzy listę elementów do usunięcia w miejscu docelowym, blisko `Delete` zadania. Możesz również określić warunek, aby sprawdzić, czy właściwość nie jest pusta, aby nie utworzyć listy elementów ze ścieżką rozpoczynającą się w katalogu głównym dysku.

`Delete`Zadanie jest przeznaczone do usuwania plików. Jeśli chcesz usunąć katalog, użyj [RemoveDir —](removedir-task.md).

`Delete`Zadanie nie udostępnia opcji usuwania plików tylko do odczytu. Aby usunąć pliki tylko do odczytu, można użyć `Exec` zadania do uruchomienia `del` polecenia lub równoważnego, z odpowiednią opcją włączenia usuwania plików tylko do odczytu. Musisz zwrócić uwagę na długość listy elementów wejściowych, ponieważ w wierszu polecenia występuje ograniczenie długości, a także upewnienie się, że nazwy plików są obsługiwane z spacjami, jak w tym przykładzie:

```xml
<Target Name="DeleteReadOnly">
  <ItemGroup>
    <FileToDelete Include="read only file.txt"/>
  </ItemGroup>
  <Exec Command="del /F /Q &quot;@(FileToDelete)&quot;"/>
</Target>
```

Ogólnie rzecz biorąc, podczas pisania skryptów kompilacji, należy rozważyć, czy usuwanie jest logicznie częścią `Clean` operacji. Jeśli konieczne jest ustawienie niektórych plików do oczyszczenia w ramach normalnej `Clean` operacji, można dodać je do `@(FileWrites)` listy, a następnie zostaną usunięte `Clean` . Jeśli potrzebujesz więcej przetwarzania niestandardowego, zdefiniuj element docelowy i określ go do uruchomienia przez ustawienie atrybutu `BeforeTargets="Clean"` lub `AfterTargets="Clean"` lub Zdefiniuj swoją niestandardową wersję `BeforeClean` `AfterClean` elementów docelowych lub. Zobacz [Dostosowywanie kompilacji](customize-your-build.md).

## <a name="see-also"></a>Zobacz też

- [RemoveDir — zadanie](removedir-task.md)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
