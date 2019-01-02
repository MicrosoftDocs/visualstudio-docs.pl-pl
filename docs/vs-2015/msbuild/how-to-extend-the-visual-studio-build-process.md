---
title: 'Instrukcje: Rozszerzanie procesu kompilacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3a530f74e1cf90012f9724d68493b1602b0e6dc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53938724"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Instrukcje: Rozszerzanie procesu kompilacji programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Procesu kompilacji jest definiowany przez szereg [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] plików .targets, które są importowane do pliku projektu. Jeden z tych plików zaimportowanych Microsoft.Common.targets, można rozszerzyć do umożliwiają uruchamianie niestandardowych zadań w kilku miejscach w procesie kompilacji. W tym temacie opisano dwie metody, można użyć, aby rozszerzyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] procesu kompilacji:

-   Zastępowanie określonych wstępnie zdefiniowanych obiektów docelowych określonych w Microsoft.Common.targets.

-   Zastępowanie właściwości "DependsOn" określonych w Microsoft.Common.targets.

## <a name="overriding-predefined-targets"></a>Zastępowanie wstępnie zdefiniowanych obiektów docelowych
 Plik Microsoft.Common.targets zawiera zestaw wstępnie zdefiniowanych pusty obiektów docelowych, które są wywoływane przed i po nim niektóre z najważniejszych elementów docelowych w procesie kompilacji. Na przykład [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] wywołania `BeforeBuild` docelowej przed funkcją main `CoreBuild` docelowego i `AfterBuild` docelowe po `CoreBuild` docelowej. Domyślnie puste elementy docelowe w Microsoft.Common.targets nic nie rób, ale ich zachowanie domyślne można przesłonić, definiując elementy docelowe, które mają w pliku projektu, który importuje Microsoft.Common.targets. Dzięki temu można użyć [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zadań daje większą kontrolę nad procesem kompilacji.

#### <a name="to-override-a-predefined-target"></a>Aby wstępnie zdefiniowany obiekt docelowy zastąpienia

1. Określ cel wstępnie zdefiniowanych w Microsoft.Common.targets, który chcesz zastąpić. Znajdują się w tabeli poniżej, aby uzyskać pełną listę obiektów docelowych, które można bezpiecznie zastąpić.

2. Definiowanie docelowego lub miejsc docelowych, na końcu pliku projektu bezpośrednio przed `</Project>` tagu. Na przykład:

   ```
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

   W poniższej tabeli przedstawiono wszystkie obiekty docelowe w Microsoft.Common.targets, który można bezpiecznie zastąpić.

|Nazwa obiektu docelowego|Opis|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Wstawione w jednym z następujących elementów docelowych uruchomienia przed lub po zakończeniu kompilacji podstawowe zadania. Większość dostosowań są wykonywane tylko w jednym z następujących dwóch elementów docelowych.|
|`BeforeBuild`, `AfterBuild`|Zadania wstawione w jednym z następujących elementów docelowych uruchomi się przed lub po wszystko inne w kompilacji. **Uwaga:**  `BeforeBuild` i `AfterBuild` elementy docelowe zostały już zdefiniowane w komentarzach na końcu większości plików projektów. Dzięki temu można w prosty sposób dodać zdarzenia przed i po kompilacji do pliku projektu.|
|`BeforeRebuild`, `AfterRebuild`|Zadania wstawione w jednym z następujących elementów docelowych uruchomienia przed lub po podstawowe odbudować funkcji jest wywoływana. Kolejność wykonanie docelowego w Microsoft.Common.targets ma: `BeforeRebuild`, `Clean`, `Build`, a następnie `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Zadania wstawione w jednym z następujących elementów docelowych uruchomienia przed lub po podstawowe czysta funkcja jest wywoływana.|
|`BeforePublish`, `AfterPublish`|Zadania wstawione w jednym z następujących elementów docelowych uruchomienia przed lub po podstawowe publikowanie funkcji jest wywoływana.|
|`BeforeResolveReference`, `AfterResolveReferences`|Zadania wstawione w jednym z następujących elementów docelowych są uruchamiane przed lub po odwołania do zestawów są rozwiązane.|
|`BeforeResGen`, `AfterResGen`|Zadania wstawione w jednym z następujących elementów docelowych są uruchamiane przed lub po wygenerowaniu zasobów.|

## <a name="overriding-dependson-properties"></a>Zastępowanie właściwości "DependsOn"
 Zastępowanie wstępnie zdefiniowanych obiektów docelowych to prosty sposób rozszerzyć proces kompilacji, ale, ponieważ [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] sekwencyjnie, ocenia definicji elementów docelowych nie istnieje sposób, aby zapobiec innego projektu, który importuje projektu z zastępowanie cele już zostały zastąpione. Tak, na przykład ostatniego `AfterBuild` docelowej zdefiniowane w pliku projektu po inne projekty zostały zaimportowane, będzie używany podczas kompilacji.

 Można zabezpieczyć się przed niezamierzonym przesłonięcia elementów docelowych przez zastąpienie właściwości "DependsOn", które są używane w `DependsOnTargets` atrybutów w całym pliku Microsoft.Common.targets. Na przykład `Build` docelowy zawiera `DependsOnTargets` wartość atrybutu `"$(BuildDependsOn)"`. Należy wziąć pod uwagę:

```
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

 Ten fragment kodu XML wskazuje, że przed `Build` docelowych można uruchomić, wszystkie elementy docelowe, określone w `BuildDependsOn` najpierw należy uruchomić właściwości. `BuildDependsOn` Właściwość jest zdefiniowana jako:

```
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

 Wartość tej właściwości można zastąpić przez zadeklarowanie innej właściwości o nazwie `BuildDependsOn` na końcu pliku projektu. Umieszczając poprzedniego `BuildDependsOn` właściwość w nową właściwość, można dodać nowe elementy docelowe, na początku i końca listy docelowej. Na przykład:

```
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

#### <a name="to-override-a-dependson-property"></a>Aby zastąpić właściwość "DependsOn"

1.  Określ wstępnie zdefiniowaną właściwość "DependsOn" w Microsoft.Common.targets, który chcesz zastąpić. Znajdują się w tabeli poniżej, aby uzyskać listę właściwości często zastąpione "DependsOn".

2.  Zdefiniuj inne wystąpienie, właściwość lub właściwości na końcu pliku projektu. Zawiera właściwości oryginalnej, na przykład `$(BuildDependsOn)`, w nowej właściwości.

3.  Zdefiniuj niestandardowe elementy docelowe, przed lub po definicji właściwości.

4.  Tworzenie pliku projektu.

### <a name="commonly-overridden-dependson-properties"></a>Powszechnie zastępowane właściwości "DependsOn"

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|`BuildDependsOn`|Właściwość, aby zastąpić, jeśli chcesz wstawić niestandardowe obiekty docelowe, przed lub po zakończeniu procesu całej kompilacji.|
|`CleanDependsOn`|Właściwość, aby zastąpić, jeśli chcesz wyczyścić dane wyjściowe z niestandardowego procesu kompilacji.|
|`CompileDependsOn`|Właściwość, aby zastąpić, jeśli chcesz wstawić niestandardowych procesów przed lub po wykonaniu kroku kompilacji.|

## <a name="see-also"></a>Zobacz też
 [Integracja z programem Visual Studio](../msbuild/visual-studio-integration-msbuild.md) [pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md) [. Pliki elementów docelowych](../msbuild/msbuild-dot-targets-files.md)
