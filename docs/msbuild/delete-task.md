---
title: Usuwanie zadania | Microsoft Docs
description: Dowiedz się więcej o parametrach i zagadnieniach dotyczących MSBuild usuwania określonych plików.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09945306a2260bed5b264d380dcea745ff3f7c07
ms.sourcegitcommit: 8fb1500acb7e6314fbb6b78eada78ef5d61d39bf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2021
ms.locfileid: "113280432"
---
# <a name="delete-task"></a>Delete — Zadanie

Usuwa określone pliki.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry `Delete` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`DeletedFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa pliki, które zostały pomyślnie usunięte.|
|`Files`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki do usunięcia.|
|`TreatErrorsAsWarnings`|Parametr `Boolean` opcjonalny<br /><br /> Jeśli `true` , błędy są rejestrowane jako ostrzeżenia. Wartość domyślna to `false`.|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej to zadanie dziedziczy parametry z klasy , która <xref:Microsoft.Build.Tasks.TaskExtension> sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy . Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension, klasa bazowa](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Należy zachować ostrożność podczas używania symboli wieloznacznych w `Delete` zadaniu. Niewłaściwe pliki można łatwo usunąć za pomocą wyrażeń, takich jak lub , zwłaszcza jeśli właściwość ma wartość pustego ciągu. W takim przypadku parametr może zostać oceniony jako katalog główny dysku i usunąć znacznie więcej, niż chcesz `$(SomeProperty)\**\*.*` `$(SomeProperty)/**/*.*` `Files` usunąć.

## <a name="example"></a>Przykład

Poniższy przykład usuwa plik *ConsoleApp1.pdb* podczas kompilowania obiektu `DeleteDebugSymbolFile` docelowego.

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

Jeśli chcesz śledzić usunięte pliki, ustaw na `TaskParameter` wartość z nazwą elementu w następujący `DeletedFiles` sposób:

```xml
      <Target Name="DeleteDebugSymbolFile">
        <Delete Files="$(OutDir)$(AppName).pdb" >
              <Output TaskParameter="DeletedFiles" ItemName="DeletedList"/>
        </Delete>
        <Message Text="Deleted files: '@(DeletedList)'"/>
    </Target>
```

Zamiast bezpośrednio używać symboli wieloznacznych w zadaniu, utwórz plik , aby usunąć i `Delete` uruchomić zadanie w tym `ItemGroup` `Delete` celu. Pamiętaj jednak, aby dokładnie umieścić `ItemGroup` to miejsce. Jeśli umieścisz element na najwyższym poziomie w pliku projektu, zostanie on oceniony na wczesnym etapie przed rozpoczęciem kompilacji, więc nie będzie zawierać żadnych plików, które zostały skompilowane w ramach `ItemGroup` procesu kompilacji. Dlatego umieść element , `ItemGroup` który tworzy listę elementów do usunięcia w celu blisko `Delete` zadania. Można również określić warunek, aby sprawdzić, czy właściwość nie jest pusta, aby nie można było utworzyć listy elementów ze ścieżką, która rozpoczyna się w katalogu głównym dysku.

Zadanie `Delete` jest przeznaczone do usuwania plików. Jeśli chcesz usunąć katalog, użyj [RemoveDir](removedir-task.md).

Zadanie nie zapewnia opcji usuwania plików tylko `Delete` do odczytu. Aby usunąć pliki tylko do odczytu, można użyć zadania do uruchomienia polecenia lub równoważnego z odpowiednią opcją, aby włączyć usuwanie plików `Exec` `del` tylko do odczytu. Należy zwrócić uwagę na długość listy elementów wejściowych, ponieważ w wierszu polecenia istnieje ograniczenie długości, a także upewnij się, że nazwy plików są obsługiwane ze spacjami, jak w tym przykładzie:

```xml
<Target Name="DeleteReadOnly">
  <ItemGroup>
    <FileToDelete Include="read only file.txt"/>
  </ItemGroup>
  <Exec Command="del /F /Q &quot;@(FileToDelete)&quot;"/>
</Target>
```

Ogólnie rzecz biorąc, podczas pisania skryptów kompilacji należy rozważyć, czy usunięcie jest logicznie częścią `Clean` operacji. Jeśli musisz ustawić niektóre pliki do wyczyszczenia w ramach normalnej operacji, możesz dodać je do listy i zostaną one usunięte w `Clean` `@(FileWrites)` następnym pliku `Clean` . Jeśli jest potrzebne więcej przetwarzania niestandardowego, zdefiniuj element docelowy i określ jego uruchomienie przez ustawienie atrybutu lub lub albo zdefiniuj niestandardową wersję obiektów `BeforeTargets="Clean"` `AfterTargets="Clean"` `BeforeClean` `AfterClean` docelowych lub . Zobacz [Dostosowywanie kompilacji.](customize-your-build.md)

## <a name="see-also"></a>Zobacz też

- [RemoveDir — zadanie](removedir-task.md)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
