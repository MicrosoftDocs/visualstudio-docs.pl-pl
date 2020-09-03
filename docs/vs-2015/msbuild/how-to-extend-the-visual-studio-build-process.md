---
title: 'Instrukcje: zwiększanie procesu kompilacji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 789c60da5be841721ab3a999120e2fe560ffd588
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156613"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Porady: rozszerzanie procesu kompilacji programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Proces kompilacji jest definiowany przez serię [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] plików. targets, które są importowane do pliku projektu. Jeden z tych zaimportowanych plików, Microsoft. Common. targets, można rozszerzyć, aby umożliwić uruchamianie niestandardowych zadań w kilku punktach procesu kompilacji. W tym temacie objaśniono dwie metody, których można użyć do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozbudowy procesu kompilacji:

- Zastępowanie określonych wstępnie zdefiniowanych elementów docelowych zdefiniowanych w Microsoft. Common. targets.

- Zastępowanie właściwości "DependsOn" zdefiniowanych w Microsoft. Common. targets.

## <a name="overriding-predefined-targets"></a>Zastępowanie wstępnie zdefiniowanych elementów docelowych
 Plik Microsoft. Common. targets zawiera zestaw wstępnie zdefiniowanych pustych obiektów docelowych, które są wywoływane przed i po niektórych głównych elementach docelowych w procesie kompilacji. Na przykład [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] wywołuje `BeforeBuild` obiekt docelowy przed głównym `CoreBuild` elementem docelowym i `AfterBuild` elementem docelowym po `CoreBuild` elemencie docelowym. Domyślnie puste elementy docelowe w programie Microsoft. Common. targets nie wykonują żadnych operacji, ale można przesłonić swoje domyślne zachowanie, definiując żądane obiekty docelowe w pliku projektu, który importuje element Microsoft. Common. targets. Dzięki temu można użyć [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zadań, aby zapewnić większą kontrolę nad procesem kompilacji.

#### <a name="to-override-a-predefined-target"></a>Aby zastąpić wstępnie zdefiniowany element docelowy

1. Zidentyfikuj wstępnie zdefiniowany element docelowy w programie Microsoft. Common. targets, który chcesz przesłonić. Zapoznaj się z poniższą tabelą, aby uzyskać pełną listę obiektów docelowych, które można bezpiecznie przesłonić.

2. Zdefiniuj element docelowy lub docelowy na końcu pliku projektu bezpośrednio przed `</Project>` tagiem. Na przykład:

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

3. Kompiluj plik projektu.

   W poniższej tabeli przedstawiono wszystkie elementy docelowe w Microsoft. Common. targets, które można bezpiecznie przesłonić.

|Nazwa obiektu docelowego|Opis|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Zadania wstawione w jednym z tych celów są uruchamiane przed kompilacją podstawową lub po niej. Większość dostosowań odbywa się w jednym z tych dwóch celów.|
|`BeforeBuild`, `AfterBuild`|Zadania wstawione w jednym z tych elementów docelowych zostaną uruchomione przed wszystkimi innymi w kompilacji. **Uwaga:**  `BeforeBuild` Elementy i `AfterBuild` są już zdefiniowane w komentarzach na końcu większości plików projektu. Dzięki temu można łatwo dodawać zdarzenia przed i po kompilacji do pliku projektu.|
|`BeforeRebuild`, `AfterRebuild`|Zadania wstawione w jednym z tych celów są uruchamiane przed wywołaniem podstawowej funkcji odbudowywania lub po niej. Kolejność wykonywania obiektów docelowych w elemencie Microsoft. Common. targets to: `BeforeRebuild` , `Clean` , `Build` , i `AfterRebuild` .|
|`BeforeClean`, `AfterClean`|Zadania wstawione w jednym z tych obiektów docelowych są uruchamiane przed wywołaniem lub po wywołaniu podstawowych funkcji czystych.|
|`BeforePublish`, `AfterPublish`|Zadania wstawione w jednym z tych obiektów docelowych są uruchamiane przed wywołaniem podstawowej funkcji publikowania lub po niej.|
|`BeforeResolveReference`, `AfterResolveReferences`|Zadania wstawione w jednym z tych obiektów docelowych są uruchamiane przed rozwiązanymi odwołaniami do zestawów lub po nich.|
|`BeforeResGen`, `AfterResGen`|Zadania wstawione w jednym z tych celów są uruchamiane przed wygenerowaniem zasobów lub po nich.|

## <a name="overriding-dependson-properties"></a>Zastępowanie właściwości "DependsOn"
 Zastępowanie wstępnie zdefiniowanych elementów docelowych jest łatwym sposobem na rozszerzenie procesu kompilacji, ale, ponieważ program [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] oblicza definicję elementów docelowych sekwencyjnie, nie ma żadnego sposobu, aby uniemożliwić inny projekt, który importuje projekt z zastępowania obiektów docelowych, które zostały już zastąpione. Na przykład ostatni `AfterBuild` element docelowy zdefiniowany w pliku projektu, po zaimportowaniu wszystkich innych projektów, będzie używany podczas kompilacji.

 Można chronić przed niezamierzonymi zastąpieniami docelowymi, zastępując właściwości "DependsOn", które są używane w `DependsOnTargets` atrybutach w pliku Microsoft. Common. targets. Na przykład `Build` element docelowy zawiera `DependsOnTargets` wartość atrybutu `"$(BuildDependsOn)"` . Rozważ następujące kwestie:

```
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

 Ten fragment XML wskazuje, że przed `Build` uruchomieniem elementu docelowego wszystkie elementy docelowe określone we `BuildDependsOn` właściwości muszą zostać uruchomione jako pierwsze. `BuildDependsOn`Właściwość jest definiowana jako:

```
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

 Można zastąpić tę wartość właściwości, deklarując inną właściwość o nazwie `BuildDependsOn` na końcu pliku projektu. Dołączając poprzednią `BuildDependsOn` Właściwość w nowej właściwości, można dodać nowe cele na początku i na końcu listy docelowej. Na przykład:

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

 Projekty, które importują pliki projektu, mogą przesłaniać te właściwości bez zastępowania wprowadzonych dostosowań.

#### <a name="to-override-a-dependson-property"></a>Aby przesłonić Właściwość "DependsOn"

1. Zidentyfikuj wstępnie zdefiniowaną Właściwość "DependsOn" w elemencie Microsoft. Common. targets, która ma zostać przesłonięta. W poniższej tabeli znajduje się lista typowych właściwości "DependsOn".

2. Zdefiniuj inne wystąpienie właściwości lub właściwości na końcu pliku projektu. Dołącz oryginalną właściwość, na przykład `$(BuildDependsOn)` w nowej właściwości.

3. Zdefiniuj niestandardowe elementy docelowe przed definicją właściwości lub po niej.

4. Kompiluj plik projektu.

### <a name="commonly-overridden-dependson-properties"></a>Często zastępowane właściwości "DependsOn"

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|`BuildDependsOn`|Właściwość, która ma zostać zastąpiona, jeśli chcesz wstawić niestandardowe elementy docelowe przed lub po całym procesie kompilacji.|
|`CleanDependsOn`|Właściwość do zastąpienia, jeśli chcesz wyczyścić dane wyjściowe z niestandardowego procesu kompilacji.|
|`CompileDependsOn`|Właściwość do zastąpienia, jeśli chcesz wstawić niestandardowe procesy przed lub po kroku kompilacji.|

## <a name="see-also"></a>Zobacz też
 Pojęcia dotyczące [programu Visual Studio Integration](../msbuild/visual-studio-integration-msbuild.md) [MSBuild](../msbuild/msbuild-concepts.md) [. Pliki docelowe](../msbuild/msbuild-dot-targets-files.md)
