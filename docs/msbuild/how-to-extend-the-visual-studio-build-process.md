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
ms.openlocfilehash: cca0c55951d4928347528814d043bb8a7c55be9a
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633853"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Porady: rozszerzanie procesu kompilacji programu Visual Studio

Proces kompilacji programu Visual Studio jest definiowany przez serię plików programu MSBuild *. targets* , które są importowane do pliku projektu. Jeden z tych zaimportowanych plików, *Microsoft. Common. targets*, można rozszerzyć, aby umożliwić uruchamianie niestandardowych zadań w kilku punktach procesu kompilacji. W tym artykule opisano dwie metody, których można użyć do rozbudowy procesu kompilacji programu Visual Studio:

- Zastępowanie określonych wstępnie zdefiniowanych elementów docelowych zdefiniowanych we wspólnych celach (*Microsoft. Common. targets* lub importowanych plikach).

- Zastępowanie właściwości "DependsOn" zdefiniowanych w wspólnych elementach docelowych.
## <a name="override-predefined-targets"></a>Zastąp wstępnie zdefiniowanych obiektów docelowych

## <a name="override-predefined-targets"></a>Zastąp wstępnie zdefiniowanych obiektów docelowych

Wspólne obiekty docelowe zawierają zestaw wstępnie zdefiniowanych pustych obiektów docelowych, które są wywoływane przed i po niektórych głównych elementach docelowych w procesie kompilacji. Na przykład MSBuild wywołuje `BeforeBuild` Target przed głównym elementem docelowym `CoreBuild` i elementem docelowym `AfterBuild` po elemencie docelowym `CoreBuild`. Domyślnie puste elementy docelowe w wspólnych elementach docelowych nie wykonują żadnych operacji, ale można przesłonić swoje domyślne zachowanie przez zdefiniowanie obiektów docelowych w pliku projektu, który importuje wspólne elementy docelowe. Zastępując wstępnie zdefiniowane elementy docelowe, można użyć zadań programu MSBuild, aby zapewnić większą kontrolę nad procesem kompilacji.
Wspólne obiekty docelowe zawierają zestaw wstępnie zdefiniowanych pustych obiektów docelowych, które są wywoływane przed i po niektórych głównych elementach docelowych w procesie kompilacji. Na przykład MSBuild wywołuje `BeforeBuild` Target przed głównym elementem docelowym `CoreBuild` i elementem docelowym `AfterBuild` po elemencie docelowym `CoreBuild`. Domyślnie puste elementy docelowe w wspólnych elementach docelowych nie wykonują żadnych operacji, ale można przesłonić swoje domyślne zachowanie przez zdefiniowanie obiektów docelowych w pliku projektu, który importuje wspólne elementy docelowe. Zastępując wstępnie zdefiniowane elementy docelowe, można użyć zadań programu MSBuild, aby zapewnić większą kontrolę nad procesem kompilacji.

> [!NOTE]
> Projekty w stylu zestawu SDK mają niejawny import elementów docelowych *po ostatnim wierszu pliku projektu*. Oznacza to, że nie można przesłonić domyślnych obiektów docelowych, chyba że ręcznie określisz swoje Importy zgodnie z opisem w artykule [jak: Użyj zestawów SDK projektu MSBuild](how-to-use-project-sdk.md).

#### <a name="to-override-a-predefined-target"></a>Aby wstępnie zdefiniowany obiekt docelowy zastąpienia

1. Zidentyfikuj wstępnie zdefiniowany element docelowy w wspólnych celach, które chcesz przesłonić. Znajdują się w tabeli poniżej, aby uzyskać pełną listę obiektów docelowych, które można bezpiecznie zastąpić.

2. Zdefiniuj element docelowy lub cel na końcu pliku projektu bezpośrednio przed tagiem `</Project>`. Na przykład:

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

W poniższej tabeli przedstawiono wszystkie elementy docelowe, które można bezpiecznie przesłonić.

|Nazwa docelowa|Opis|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po zakończeniu kompilacji core. Większość dostosowań są wykonywane tylko w jednym z następujących dwóch elementów docelowych.|
|`BeforeBuild`, `AfterBuild`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomi się przed lub po wszystko inne w kompilacji. **Uwaga:**  Elementy docelowe `BeforeBuild` i `AfterBuild` są już zdefiniowane w komentarzach na końcu większości plików projektu, co pozwala łatwo dodawać zdarzenia przed i po kompilacji do pliku projektu.|
|`BeforeRebuild`, `AfterRebuild`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po podstawowe odbudować funkcji jest wywoływana. Kolejność wykonywania obiektów docelowych w elemencie *Microsoft. Common. targets* to: `BeforeRebuild`, `Clean`, `Build`, a następnie `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po podstawowe czysta funkcja jest wywoływana.|
|`BeforePublish`, `AfterPublish`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po podstawowe publikowanie funkcji jest wywoływana.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po odwołania do zestawów są rozwiązane.|
|`BeforeResGen`, `AfterResGen`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po wygenerowaniu zasobów.|

## <a name="override-dependson-properties"></a>Zastąpienie DependsOn właściwości

Zastępowanie wstępnie zdefiniowanych elementów docelowych jest łatwym sposobem na rozszerzenie procesu kompilacji, ale ponieważ MSBuild ocenia definicje elementów docelowych sekwencyjnie, nie ma możliwości zapobiegania innemu projektowi, który importuje projekt przed zastępowaniem już posiadanych obiektów docelowych zmienione. Tak więc na przykład ostatni element docelowy `AfterBuild` zdefiniowany w pliku projektu, po zaimportowaniu wszystkich innych projektów będzie to ten, który jest używany podczas kompilacji.

Można chronić przed niezamierzonymi zastąpieniami docelowymi, zastępując właściwości DependsOn, które są używane w atrybutach `DependsOnTargets` w ramach wspólnych elementów docelowych. Na przykład element docelowy `Build` zawiera `DependsOnTargets` wartość atrybutu `"$(BuildDependsOn)"`. Rozważ następujące kwestie:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Ten element XML wskazuje, że przed uruchomieniem `Build` celu będzie można uruchomić wszystkie elementy docelowe określone we właściwości `BuildDependsOn`. Właściwość `BuildDependsOn` jest definiowana jako:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Można zastąpić tę wartość właściwości, deklarując inną właściwość o nazwie `BuildDependsOn` na końcu pliku projektu. Uwzględniając poprzednią Właściwość `BuildDependsOn` w nowej właściwości, można dodać nowe cele na początku i na końcu listy docelowej. Na przykład:

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

Projekty, które importują plików projektu można zastąpić te właściwości, bez zastępowania dostosowania, które zostały wprowadzone.

#### <a name="to-override-a-dependson-property"></a>Aby zastąpić właściwością DependsOn

1. Zidentyfikuj wstępnie zdefiniowaną Właściwość DependsOn w wspólnych elementach docelowych, które chcesz przesłonić. Zobacz tabelę poniżej lista najczęściej zastąpione DependsOn właściwości.

2. Zdefiniuj inne wystąpienie, właściwość lub właściwości na końcu pliku projektu. Dołącz oryginalną właściwość, na przykład `$(BuildDependsOn)`, w nowej właściwości.

3. Zdefiniuj niestandardowe elementy docelowe, przed lub po definicji właściwości.

4. Tworzenie pliku projektu.

### <a name="commonly-overridden-dependson-properties"></a>Często zastąpione DependsOn właściwości

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|`BuildDependsOn`|Właściwość, aby zastąpić, jeśli chcesz wstawić niestandardowe obiekty docelowe, przed lub po zakończeniu procesu całej kompilacji.|
|`CleanDependsOn`|Właściwość, aby zastąpić, jeśli chcesz wyczyścić dane wyjściowe z niestandardowego procesu kompilacji.|
|`CompileDependsOn`|Właściwość, aby zastąpić, jeśli chcesz wstawić niestandardowych procesów przed lub po wykonaniu kroku kompilacji.|

## <a name="see-also"></a>Zobacz też

- [Integracja z programem Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [pliki. targets](../msbuild/msbuild-dot-targets-files.md)
