---
title: 'Jak: Czyszczenie kompilacji | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b7848189c866481e6e97d05d95b5fb97a3d4893
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633918"
---
# <a name="how-to-clean-a-build"></a>Jak: Czyszczenie kompilacji

Podczas czyszczenia kompilacji wszystkie pliki pośrednie i wyjściowe są usuwane, pozostawiając tylko pliki projektu i składnika. Z plików projektu i składników można następnie zbudować nowe wystąpienia plików pośrednich i wyjściowych. 

## <a name="create-a-directory-for-output-items"></a>Tworzenie katalogu dla elementów wyjściowych

 Domyślnie plik *exe* tworzony podczas kompilowania projektu jest umieszczany w tym samym katalogu co pliki projektu i źródła. Zazwyczaj jednak elementy wyjściowe są tworzone w osobnym katalogu.

### <a name="to-create-a-directory-for-output-items"></a>Aby utworzyć katalog dla elementów wyjściowych

1. Użyj `Property` elementu, aby zdefiniować lokalizację i nazwę katalogu. Na przykład utwórz katalog o nazwie *BuiltApp* w katalogu zawierającym pliki projektu i źródła:

     `<builtdir>BuiltApp</builtdir>`

2. Użyj zadania [MakeDir,](../msbuild/makedir-task.md) aby utworzyć katalog, jeśli katalog nie istnieje. Przykład:

     ```xml
     <MakeDir Directories = "$(builtdir)"
      Condition = "!Exists('$(builtdir)')" />
     ```

## <a name="remove-the-output-items"></a>Usuwanie elementów wyjściowych

 Przed utworzeniem nowych wystąpień plików pośrednich i wyjściowych można wyczyścić wszystkie poprzednie wystąpienia plików pośrednich i wyjściowych. Użyj zadania [Usuńj,](../msbuild/removedir-task.md) aby usunąć katalog oraz wszystkie pliki i katalogi, które zawiera z dysku.

#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Aby usunąć katalog i wszystkie pliki zawarte w katalogu

- Użyj `RemoveDir` zadania, aby usunąć katalog. Przykład:

     `<RemoveDir Directories="$(builtdir)" />`

## <a name="example"></a>Przykład

 Poniższy przykładowy projekt kodu `Clean`zawiera nowy obiekt `RemoveDir` docelowy, który używa zadania do usunięcia katalogu i wszystkich plików i katalogów, które zawiera. Również w tym `Compile` przykładzie obiekt docelowy tworzy oddzielny katalog dla elementów wyjściowych, które są usuwane, gdy kompilacja jest czyszczona.

 `Compile`jest zdefiniowany jako domyślny cel i dlatego jest używany automatycznie, chyba że określisz inny cel lub cele. Przełącznik wiersza polecenia **-target** służy do określania innego obiektu docelowego. Przykład:

 `msbuild <file name>.proj -target:Clean`

 Przełącznik **-target** można skrócić do **-t** i można określić więcej niż jeden cel. Na przykład, aby `Clean` użyć obiektu `Compile`docelowego, a następnie cel , wpisz:

 `msbuild <file name>.proj -t:Clean;Compile`

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <!-- Set the application name as a property -->
        <name>HelloWorldCS</name>

        <!-- Set the output folder as a property -->
        <builtdir>BuiltApp</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <!-- Specify the inputs by type and file name -->
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Check whether an output folder exists and create
        one if necessary -->
        <MakeDir Directories = "$(builtdir)"
            Condition = "!Exists('$(builtdir)')" />

        <!-- Run the Visual C# compiler -->
        <CSC Sources = "@(CSFile)"
            OutputAssembly = "$(BuiltDir)\$(appname).exe">
            <Output TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>

        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>

    <Target Name = "Clean">
        <RemoveDir Directories="$(builtdir)" />
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadanie MakeDir](../msbuild/makedir-task.md)
- [RemoveDir zadanie](../msbuild/removedir-task.md)
- [Zadanie csc](../msbuild/csc-task.md)
- [Cele](../msbuild/msbuild-targets.md)
