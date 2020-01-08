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
ms.openlocfilehash: 995bf368d367d51a3d38e02dbab2d6e55ff4ab13
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75575929"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Porady: rozszerzanie procesu kompilacji programu Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Procesu kompilacji jest definiowany przez szereg [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] *.targets* pliki, które są importowane w pliku projektu. Te zaimportowane pliki *Microsoft.Common.targets*, można rozszerzyć, aby możliwe było uruchamianie niestandardowych zadań w kilku miejscach w procesie kompilacji. W tym artykule opisano dwie metody, można użyć, aby rozszerzyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] procesu kompilacji:

- Zastępowanie określonych wstępnie zdefiniowanych elementów docelowych zdefiniowanych we wspólnych celach (*Microsoft. Common. targets* lub importowanych plikach).

- Zastępowanie właściwości "DependsOn" zdefiniowanych w wspólnych elementach docelowych.

## <a name="override-predefined-targets"></a>Zastąp wstępnie zdefiniowanych obiektów docelowych
Wspólne obiekty docelowe zawierają zestaw wstępnie zdefiniowanych pustych obiektów docelowych, które są wywoływane przed i po niektórych głównych elementach docelowych w procesie kompilacji. Na przykład [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wywołania `BeforeBuild` docelowej przed funkcją main `CoreBuild` docelowego i `AfterBuild` docelowe po `CoreBuild` docelowej. Domyślnie puste elementy docelowe w wspólnych elementach docelowych nie wykonują żadnych operacji, ale można przesłonić swoje domyślne zachowanie przez zdefiniowanie obiektów docelowych w pliku projektu, który importuje wspólne elementy docelowe. Zastępowanie wstępnie zdefiniowanych obiektów docelowych, należy skorzystać z [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadań daje większą kontrolę nad procesem kompilacji.

> [!NOTE]
> Projekty w stylu zestawu SDK mają niejawny import elementów docelowych *po ostatnim wierszu pliku projektu*. Oznacza to, że nie można przesłonić domyślnych obiektów docelowych, chyba że ręcznie określisz swoje Importy zgodnie z opisem w artykule [jak: Użyj zestawów SDK projektu MSBuild](how-to-use-project-sdk.md).

#### <a name="to-override-a-predefined-target"></a>Aby wstępnie zdefiniowany obiekt docelowy zastąpienia

1. Zidentyfikuj wstępnie zdefiniowany element docelowy w wspólnych celach, które chcesz przesłonić. Znajdują się w tabeli poniżej, aby uzyskać pełną listę obiektów docelowych, które można bezpiecznie zastąpić.

2. Definiowanie docelowego lub miejsc docelowych, na końcu pliku projektu bezpośrednio przed `</Project>` tagu. Na przykład:

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
|`BeforeBuild`, `AfterBuild`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomi się przed lub po wszystko inne w kompilacji. **Uwaga:** `BeforeBuild` i `AfterBuild` elementy docelowe zostały już zdefiniowane w komentarzach na końcu większość plików projektu, dzięki czemu możesz łatwo dodać zdarzenia przed i po kompilacji do pliku projektu.|
|`BeforeRebuild`, `AfterRebuild`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po podstawowe odbudować funkcji jest wywoływana. Kolejność wykonywania docelowego w *Microsoft.Common.targets* jest: `BeforeRebuild`, `Clean`, `Build`, a następnie `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po podstawowe czysta funkcja jest wywoływana.|
|`BeforePublish`, `AfterPublish`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po podstawowe publikowanie funkcji jest wywoływana.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po odwołania do zestawów są rozwiązane.|
|`BeforeResGen`, `AfterResGen`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po wygenerowaniu zasobów.|

## <a name="override-dependson-properties"></a>Zastąpienie DependsOn właściwości
Zastępowanie wstępnie zdefiniowanych obiektów docelowych to prosty sposób rozszerzyć proces kompilacji, ale, ponieważ [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sekwencyjnie, ocenia definicji elementów docelowych nie istnieje sposób, aby zapobiec innego projektu, który importuje projektu z zastępowanie cele już zostały zastąpione. Tak, na przykład ostatniego `AfterBuild` docelowej zdefiniowane w pliku projektu po inne projekty zostały zaimportowane, będzie używany podczas kompilacji.

Można chronić przed niezamierzonymi zastąpieniami docelowymi, zastępując właściwości DependsOn, które są używane w atrybutach `DependsOnTargets` w ramach wspólnych elementów docelowych. Na przykład `Build` docelowy zawiera `DependsOnTargets` wartość atrybutu `"$(BuildDependsOn)"`. Rozważ następujące kwestie:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Ten fragment kodu XML wskazuje, że przed `Build` docelowych można uruchomić, wszystkie elementy docelowe, określone w `BuildDependsOn` najpierw należy uruchomić właściwości. `BuildDependsOn` Właściwość jest zdefiniowana jako:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Wartość tej właściwości można zastąpić przez zadeklarowanie innej właściwości o nazwie `BuildDependsOn` na końcu pliku projektu. Umieszczając poprzedniego `BuildDependsOn` właściwość w nową właściwość, można dodać nowe elementy docelowe, na początku i końca listy docelowej. Na przykład:

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

2. Zdefiniuj inne wystąpienie, właściwość lub właściwości na końcu pliku projektu. Zawiera właściwości oryginalnej, na przykład `$(BuildDependsOn)`, w nowej właściwości.

3. Zdefiniuj niestandardowe elementy docelowe, przed lub po definicji właściwości.

4. Tworzenie pliku projektu.

### <a name="commonly-overridden-dependson-properties"></a>Często zastąpione DependsOn właściwości

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|`BuildDependsOn`|Właściwość, aby zastąpić, jeśli chcesz wstawić niestandardowe obiekty docelowe, przed lub po zakończeniu procesu całej kompilacji.|
|`CleanDependsOn`|Właściwość, aby zastąpić, jeśli chcesz wyczyścić dane wyjściowe z niestandardowego procesu kompilacji.|
|`CompileDependsOn`|Właściwość, aby zastąpić, jeśli chcesz wstawić niestandardowych procesów przed lub po wykonaniu kroku kompilacji.|

## <a name="see-also"></a>Zobacz także
- [Integracja z programem Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [pliki .targets](../msbuild/msbuild-dot-targets-files.md)
