---
title: Rozszerzanie procesu kompilacji
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6a465a752282f4a0dc00f3fb294ade4169bb19b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093947"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Jak: Rozszerzenie procesu kompilacji programu Visual Studio

Proces kompilacji programu Visual Studio jest definiowany przez serię plików MSBuild *.targets,* które są importowane do pliku projektu. Jeden z tych importowanych plików, *Microsoft.Common.targets,* można rozszerzyć, aby umożliwić uruchamianie zadań niestandardowych w kilku punktach procesu kompilacji. W tym artykule opisano dwie metody, których można użyć do rozszerzenia procesu kompilacji programu Visual Studio:

- Zastępowanie określonych wstępnie zdefiniowanych celów zdefiniowanych we wspólnych celach (*Microsoft.Common.targets* lub plikach importowanych).

- Zastępowanie właściwości "DependsOn" zdefiniowanych we wspólnych obiektach docelowych.

## <a name="override-predefined-targets"></a>Zastępowanie wstępnie zdefiniowanych obiektów docelowych

Wspólne obiekty docelowe zawiera zestaw wstępnie zdefiniowanych pustych obiektów docelowych, który jest wywoływany przed i po niektórych głównych obiektów docelowych w procesie kompilacji. Na przykład MSBuild `BeforeBuild` wywołuje obiekt `CoreBuild` docelowy `AfterBuild` przed głównym `CoreBuild` celem i miejsce docelowe po miejsce docelowe. Domyślnie puste obiekty docelowe we wspólnych elementach docelowych nic nie robią, ale można zastąpić ich domyślne zachowanie, definiując obiekty docelowe, które chcesz w pliku projektu, który importuje wspólne obiekty docelowe. Zastępując wstępnie zdefiniowane obiekty docelowe, można użyć zadań MSBuild, aby zapewnić większą kontrolę nad procesem kompilacji.
Wspólne obiekty docelowe zawiera zestaw wstępnie zdefiniowanych pustych obiektów docelowych, który jest wywoływany przed i po niektórych głównych obiektów docelowych w procesie kompilacji. Na przykład MSBuild `BeforeBuild` wywołuje obiekt `CoreBuild` docelowy `AfterBuild` przed głównym `CoreBuild` celem i miejsce docelowe po miejsce docelowe. Domyślnie puste obiekty docelowe we wspólnych elementach docelowych nic nie robią, ale można zastąpić ich domyślne zachowanie, definiując obiekty docelowe, które chcesz w pliku projektu, który importuje wspólne obiekty docelowe. Zastępując wstępnie zdefiniowane obiekty docelowe, można użyć zadań MSBuild, aby zapewnić większą kontrolę nad procesem kompilacji.

> [!NOTE]
> Projekty w stylu SDK mają niejawny import obiektów docelowych *po ostatnim wierszu pliku projektu*. Oznacza to, że nie można zastąpić domyślnych obiektów docelowych, chyba że importujesz je ręcznie, zgodnie z opisem w [obszarze Jak: Użyj sDK projektu MSBuild](how-to-use-project-sdk.md).

#### <a name="to-override-a-predefined-target"></a>Aby zastąpić wstępnie zdefiniowany cel

1. Zidentyfikuj wstępnie zdefiniowany obiekt docelowy we wspólnych obiektach docelowych, które chcesz zastąpić. Zobacz poniższą tabelę, aby uzyskać pełną listę obiektów docelowych, które można bezpiecznie zastąpić.

2. Zdefiniuj obiekt docelowy lub obiekty docelowe na końcu pliku projektu, bezpośrednio przed tagiem. `</Project>` Przykład:

    ```xml
    <Project>
        ...
        <Target Name="BeforeBuild">
            <!-- Insert tasks to run before build here -->
        </Target>
        <Target Name="AfterBuild">
            <!-- Insert tasks to run after build here -->
        </Target>
    </Project>
    ```

3. Tworzenie pliku projektu.

W poniższej tabeli przedstawiono wszystkie obiekty docelowe we wspólnych celach, które można bezpiecznie zastąpić.

|Nazwa obiektu docelowego|Opis|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Zadania, które są wstawiane w jednym z tych obiektów docelowych są uruchamiane przed lub po zakończeniu kompilacji rdzenia. Większość dostosowań odbywa się w jednym z tych dwóch obiektów docelowych.|
|`BeforeBuild`, `AfterBuild`|Zadania, które są wstawiane w jednym z tych obiektów docelowych będzie działać przed lub po wszystko inne w kompilacji. **Uwaga:**  Obiekty `BeforeBuild` `AfterBuild` docelowe i są już zdefiniowane w komentarzach na końcu większości plików projektu, co pozwala na łatwe dodawanie zdarzeń przed i po kompilacji do pliku projektu.|
|`BeforeRebuild`, `AfterRebuild`|Zadania, które są wstawiane w jednym z tych obiektów docelowych są uruchamiane przed lub po wywoływaniu funkcji przebudowy rdzenia. Kolejność wykonywania docelowych w *pliku Microsoft.Common.targets* to: `BeforeRebuild` `Clean`, , `Build`a następnie `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Zadania, które są wstawiane w jednym z tych obiektów docelowych są uruchamiane przed lub po wywołaniu podstawowych funkcji czyszczenia.|
|`BeforePublish`, `AfterPublish`|Zadania, które są wstawiane w jednym z tych obiektów docelowych są uruchamiane przed lub po wywoływaniu podstawowej funkcji publikowania.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Zadania, które są wstawiane w jednym z tych obiektów docelowych są uruchamiane przed lub po odwołań do zestawu są rozpoznawane.|
|`BeforeResGen`, `AfterResGen`|Zadania, które są wstawiane w jednym z tych obiektów docelowych są uruchamiane przed lub po generowaniu zasobów.|

## <a name="example-aftertargets-and-beforetargets"></a>Przykład: AfterTargets i BeforeTargets

W poniższym przykładzie `AfterTargets` pokazano, jak użyć atrybutu, aby dodać niestandardowy obiekt docelowy, który robi coś z plikami wyjściowymi. W takim przypadku kopiuje pliki wyjściowe do nowego folderu *CustomOutput*.  W przykładzie pokazano również, jak oczyścić pliki utworzone `CustomClean` przez operację `BeforeTargets` kompilacji niestandardowej z obiektu docelowego `CoreClean` przy użyciu atrybutu i określając, że niestandardowe czyste operacji działa przed obiektem docelowym.

```xml
<Project Sdk="Microsoft.NET.Sdk">

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
   <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
</PropertyGroup>

<Target Name="CustomAfterBuild" AfterTargets="Build">
  <ItemGroup>
    <_FilesToCopy Include="$(OutputPath)**\*"/>
  </ItemGroup>
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean" BeforeTargets="CoreClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

> [!WARNING]
> Pamiętaj, aby używać innych nazw niż wstępnie zdefiniowane obiekty docelowe wymienione w tabeli w `CustomAfterBuild`poprzedniej `AfterBuild`sekcji (na przykład nazwaliśmy tutaj niestandardowy obiekt docelowy kompilacji , nie), ponieważ te wstępnie zdefiniowane obiekty docelowe są zastępowane przez import SDK, który również je definiuje. Nie widać importu pliku docelowego, który zastępuje te obiekty docelowe, ale jest niejawnie dodawany `Sdk` na końcu pliku projektu, gdy używasz metody atrybutu odwoływania się do SDK.

## <a name="override-dependson-properties"></a>Właściwości Zastępowanie dependson

Zastępowanie wstępnie zdefiniowanych celów jest łatwym sposobem rozszerzenia procesu kompilacji, ale ponieważ MSBuild ocenia definicję celów sekwencyjnie, nie ma sposobu, aby zapobiec innemu projektowi, który importuje projekt, przed zastąpieniem już posiadanych celów, które zostały już Zastąpiona. Tak więc, na `AfterBuild` przykład ostatni cel zdefiniowany w pliku projektu, po zaimportowaniu wszystkich innych projektów, będzie tym, który jest używany podczas kompilacji.

Można chronić przed niezamierzone zastąpienia obiektów docelowych przez zastąpienie DependsOn właściwości, które są używane w atrybutach w `DependsOnTargets` całej wspólnych obiektów docelowych. Na przykład `Build` obiekt docelowy zawiera wartość `DependsOnTargets` atrybutu `"$(BuildDependsOn)"`. Rozważ następujące kwestie:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Ten fragment XML wskazuje, `Build` że przed docelowym można uruchomić, wszystkie cele określone we `BuildDependsOn` właściwości musi działać jako pierwsze. Właściwość `BuildDependsOn` jest zdefiniowana jako:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Tę wartość właściwości można zastąpić, deklarując `BuildDependsOn` inną właściwość o nazwie na końcu pliku projektu. Dołączając poprzednią `BuildDependsOn` właściwość w nowej właściwości, można dodać nowe obiekty docelowe na początku i na końcu listy docelowej. Przykład:

```xml
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

Projekty importując pliki projektu można zastąpić te właściwości bez zastępowania dostosowań, które zostały wprowadzone.

#### <a name="to-override-a-dependson-property"></a>Aby zastąpić właściwość DependsOn

1. Zidentyfikuj wstępnie zdefiniowaną właściwość DependsOn we wspólnych obiektach docelowych, które chcesz zastąpić. Zobacz poniższą tabelę, aby uzyskać listę często zastępowane właściwości DependsOn.

2. Zdefiniuj inne wystąpienie właściwości lub właściwości na końcu pliku projektu. Dołącz oryginalną właściwość, na przykład `$(BuildDependsOn)`w nowej właściwości.

3. Zdefiniuj niestandardowe obiekty docelowe przed lub po definicji właściwości.

4. Tworzenie pliku projektu.

### <a name="commonly-overridden-dependson-properties"></a>Często zastępowane właściwości DependsOn

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|`BuildDependsOn`|Właściwość do zastąpienia, jeśli chcesz wstawić niestandardowe obiekty docelowe przed lub po całym procesie kompilacji.|
|`CleanDependsOn`|Właściwość do zastąpienia, jeśli chcesz oczyścić dane wyjściowe z niestandardowego procesu kompilacji.|
|`CompileDependsOn`|Właściwość do zastąpienia, jeśli chcesz wstawić procesy niestandardowe przed lub po kroku kompilacji.|

## <a name="example-builddependson-and-cleandependson"></a>Przykład: BuildDependsOn i CleanDependsOn

Poniższy przykład jest `BeforeTargets` podobny `AfterTargets` do i przykład, ale pokazuje, jak osiągnąć podobną funkcjonalność. Rozszerza kompilację za `BuildDependsOn` pomocą dodawania `CustomAfterBuild` własnego zadania, które kopiuje pliki wyjściowe `CustomClean` po `CleanDependsOn`kompilacji, a także dodaje odpowiednie zadanie za pomocą programu .  

W tym przykładzie jest to projekt w stylu SDK. Jak wspomniano w uwadze o projektach w stylu SDK wcześniej w tym artykule, należy użyć metody ręcznego importu zamiast atrybutu, `Sdk` który używa programu Visual Studio podczas generowania plików projektu.

```xml
<Project>
<Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>

<Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <BuildDependsOn>
      $(BuildDependsOn);CustomAfterBuild
    </BuildDependsOn>

    <CleanDependsOn>
      $(CleanDependsOn);CustomClean
    </CleanDependsOn>

    <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
  </PropertyGroup>

<Target Name="CustomAfterBuild">
  <ItemGroup>
    <_FilesToCopy Include="$(OutputPath)**\*"/>
  </ItemGroup>
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

Kolejność elementów jest ważna. Elementy `BuildDependsOn` `CleanDependsOn` i muszą pojawić się po zaimportowaniu standardowego pliku docelowego SDK.

## <a name="see-also"></a>Zobacz też

- [Integracja z programem Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
- [Pliki .targets](../msbuild/msbuild-dot-targets-files.md)
