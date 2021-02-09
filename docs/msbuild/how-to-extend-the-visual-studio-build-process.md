---
title: Rozwiń proces kompilacji
description: Poznaj różne sposoby modyfikowania procesu kompilacji, aby móc kontrolować i dostosowywać sposób kompilowania projektów.
ms.custom: seodec18, SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 67b2eff1ca7c1871eacad7608b56b6916e3cc8e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914366"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Instrukcje: zwiększanie procesu kompilacji programu Visual Studio

Proces kompilacji programu Visual Studio jest definiowany przez serię plików programu MSBuild *. targets* , które są importowane do pliku projektu. Jeden z tych zaimportowanych plików, *Microsoft. Common. targets*, można rozszerzyć, aby umożliwić uruchamianie niestandardowych zadań w kilku punktach procesu kompilacji. W tym artykule opisano dwie metody, których można użyć do rozbudowy procesu kompilacji programu Visual Studio:

- Zastępowanie określonych wstępnie zdefiniowanych elementów docelowych zdefiniowanych we wspólnych celach (*Microsoft. Common. targets* lub importowanych plikach).

- Zastępowanie właściwości "DependsOn" zdefiniowanych w wspólnych elementach docelowych.

## <a name="override-predefined-targets"></a>Przesłoń wstępnie zdefiniowane elementy docelowe

Wspólne obiekty docelowe zawierają zestaw wstępnie zdefiniowanych pustych obiektów docelowych, które są wywoływane przed i po niektórych głównych elementach docelowych w procesie kompilacji. Na przykład program MSBuild wywołuje `BeforeBuild` element docelowy przed głównym `CoreBuild` elementem docelowym i `AfterBuild` elementem docelowym po `CoreBuild` elemencie docelowym. Domyślnie puste elementy docelowe w wspólnych elementach docelowych nie wykonują żadnych operacji, ale można przesłonić swoje domyślne zachowanie przez zdefiniowanie obiektów docelowych w pliku projektu, który importuje wspólne elementy docelowe. Zastępując wstępnie zdefiniowane elementy docelowe, można użyć zadań programu MSBuild, aby zapewnić większą kontrolę nad procesem kompilacji.

> [!NOTE]
> Projekty w stylu zestawu SDK mają niejawny import elementów docelowych *po ostatnim wierszu pliku projektu*. Oznacza to, że nie można przesłonić domyślnych obiektów docelowych, chyba że ręcznie określisz swoje Importy zgodnie z opisem w artykule [jak: Użyj zestawów SDK projektu MSBuild](how-to-use-project-sdk.md).

#### <a name="to-override-a-predefined-target"></a>Aby zastąpić wstępnie zdefiniowany element docelowy

1. Zidentyfikuj wstępnie zdefiniowany element docelowy w wspólnych celach, które chcesz przesłonić. Zapoznaj się z poniższą tabelą, aby uzyskać pełną listę obiektów docelowych, które można bezpiecznie przesłonić.

2. Zdefiniuj element docelowy lub docelowy na końcu pliku projektu bezpośrednio przed `</Project>` tagiem. Na przykład:

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

3. Kompiluj plik projektu.

W poniższej tabeli przedstawiono wszystkie elementy docelowe, które można bezpiecznie przesłonić.

|Nazwa elementu docelowego|Opis|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Zadania, które są wstawiane w jednym z tych obiektów docelowych, są wykonywane przed lub po kompilacji podstawowej. Większość dostosowań odbywa się w jednym z tych dwóch celów.|
|`BeforeBuild`, `AfterBuild`|Zadania, które są wstawiane w jednym z tych elementów docelowych, zostaną uruchomione przed lub po wszystkich innych w kompilacji. **Uwaga:**  `BeforeBuild` Elementy i `AfterBuild` są już zdefiniowane w komentarzach na końcu większości plików projektu, co pozwala łatwo dodawać zdarzenia przed i po kompilacji do pliku projektu.|
|`BeforeRebuild`, `AfterRebuild`|Zadania, które są wstawiane w jednym z tych celów, są uruchamiane przed wywołaniem podstawowej funkcji odbudowywania lub po niej. Kolejność wykonywania obiektów docelowych w elemencie *Microsoft. Common. targets* to: `BeforeRebuild` , `Clean` , `Build` , i `AfterRebuild` .|
|`BeforeClean`, `AfterClean`|Zadania, które są wstawiane w jednym z tych celów, są uruchamiane przed wywołaniem lub po wywołaniu podstawowych funkcji czystych.|
|`BeforePublish`, `AfterPublish`|Zadania, które są wstawiane w jednym z tych celów, są uruchamiane przed wywołaniem podstawowej funkcji publikowania lub po niej.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Zadania, które są wstawiane w jednym z tych celów, są uruchamiane przed lub po rozwiązaniu odwołań do zestawów.|
|`BeforeResGen`, `AfterResGen`|Zadania, które są wstawiane w jednym z tych celów, są uruchamiane przed wygenerowaniem zasobów lub po nich.|

## <a name="example-aftertargets-and-beforetargets"></a>Przykład: AfterTargets i BeforeTargets

Poniższy przykład pokazuje, jak używać atrybutu, `AfterTargets` Aby dodać niestandardowy obiekt docelowy, który wykonuje coś w przypadku plików wyjściowych. W takim przypadku program kopiuje pliki wyjściowe do nowego folderu *CustomOutput*.  W przykładzie pokazano również, jak wyczyścić pliki utworzone przez niestandardową operację kompilacji z `CustomClean` elementem docelowym przy użyciu `BeforeTargets` atrybutu i określając, że niestandardowa operacja czyszczenia jest uruchamiana przed `CoreClean` elementem docelowym.

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
> Upewnij się, że używasz innych nazw niż wstępnie zdefiniowane elementy docelowe wymienione w tabeli w poprzedniej sekcji (na przykład w tym miejscu nazywamy niestandardową docelową kompilacją `CustomAfterBuild` `AfterBuild` ), ponieważ te wstępnie zdefiniowane elementy docelowe są zastępowane przez import zestawu SDK, który również definiuje. Nie widzisz importu pliku docelowego, który zastępuje te elementy docelowe, ale jest on niejawnie dodany na końcu pliku projektu, gdy używasz `Sdk` metody atrybutu odwołania do zestawu SDK.

## <a name="override-dependson-properties"></a>Zastąp właściwości DependsOn

Zastępowanie wstępnie zdefiniowanych elementów docelowych jest łatwym sposobem na rozbudowanie procesu kompilacji, ale ponieważ MSBuild ocenia definicje elementów docelowych sekwencyjnie, nie ma żadnego sposobu, aby uniemożliwić inny projekt, który importuje projekt z przesłania obiektów docelowych, które zostały już zastąpione. Na przykład ostatni `AfterBuild` element docelowy zdefiniowany w pliku projektu, po zaimportowaniu wszystkich innych projektów, będzie używany podczas kompilacji.

Można zabezpieczyć przed niezamierzonymi zastąpieniami elementów docelowych, zastępując właściwości DependsOn, które są używane w `DependsOnTargets` atrybutach we wspólnych elementach docelowych. Na przykład `Build` element docelowy zawiera `DependsOnTargets` wartość atrybutu `"$(BuildDependsOn)"` . Rozważ następujące kwestie:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Ten fragment XML wskazuje, że przed `Build` uruchomieniem elementu docelowego wszystkie elementy docelowe określone we `BuildDependsOn` właściwości muszą zostać uruchomione jako pierwsze. `BuildDependsOn`Właściwość jest definiowana jako:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Można zastąpić tę wartość właściwości, deklarując inną właściwość o nazwie `BuildDependsOn` na końcu pliku projektu. Dołączając poprzednią `BuildDependsOn` Właściwość w nowej właściwości, można dodać nowe cele na początku i na końcu listy docelowej. Na przykład:

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

Projekty, które importują pliki projektu, mogą przesłaniać te właściwości bez zastępowania wprowadzonych dostosowań.

#### <a name="to-override-a-dependson-property"></a>Aby przesłonić Właściwość DependsOn

1. Zidentyfikuj wstępnie zdefiniowaną Właściwość DependsOn w wspólnych elementach docelowych, które chcesz przesłonić. Lista najczęściej zasłoniętych właściwości DependsOn znajduje się w poniższej tabeli.

2. Zdefiniuj inne wystąpienie właściwości lub właściwości na końcu pliku projektu. Dołącz oryginalną właściwość, na przykład `$(BuildDependsOn)` w nowej właściwości.

3. Zdefiniuj niestandardowe elementy docelowe przed definicją właściwości lub po niej.

4. Kompiluj plik projektu.

### <a name="commonly-overridden-dependson-properties"></a>Często zastąpione właściwości DependsOn

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|`BuildDependsOn`|Właściwość, która ma zostać zastąpiona, jeśli chcesz wstawić niestandardowe elementy docelowe przed lub po całym procesie kompilacji.|
|`CleanDependsOn`|Właściwość do zastąpienia, jeśli chcesz wyczyścić dane wyjściowe z niestandardowego procesu kompilacji.|
|`CompileDependsOn`|Właściwość do zastąpienia, jeśli chcesz wstawić niestandardowe procesy przed lub po kroku kompilacji.|

## <a name="example-builddependson-and-cleandependson"></a>Przykład: BuildDependsOn i CleanDependsOn

Poniższy przykład jest podobny do poniższego `BeforeTargets` `AfterTargets` przykładu, ale pokazuje, jak osiągnąć podobną funkcjonalność. Rozszerza kompilację za pomocą programu, `BuildDependsOn` dodając własne zadanie `CustomAfterBuild` , które kopiuje pliki wyjściowe po kompilacji, a także dodaje odpowiednie zadanie przy `CustomClean` użyciu `CleanDependsOn` .  

W tym przykładzie jest to projekt w stylu zestawu SDK. Jak wspomniano w uwagi na temat projektów w stylu zestawu SDK wcześniej w tym artykule, należy użyć metody Import ręczny zamiast `Sdk` atrybutu, który jest używany przez program Visual Studio podczas generowania plików projektu.

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

Kolejność elementów jest ważna. `BuildDependsOn`Elementy i `CleanDependsOn` muszą występować po zaimportowaniu standardowego pliku obiektów docelowych zestawu SDK.

## <a name="see-also"></a>Zobacz też

- [integracja z programem Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [pliki. targets](../msbuild/msbuild-dot-targets-files.md)
