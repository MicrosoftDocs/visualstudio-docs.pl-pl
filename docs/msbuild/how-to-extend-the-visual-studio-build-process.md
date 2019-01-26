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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6b50dff09920f2f5dfac83136c3bd6de402d9a8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954387"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Instrukcje: Rozszerzanie procesu kompilacji programu Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Procesu kompilacji jest definiowany przez szereg [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] *.targets* pliki, które są importowane w pliku projektu. Te zaimportowane pliki *Microsoft.Common.targets*, można rozszerzyć, aby możliwe było uruchamianie niestandardowych zadań w kilku miejscach w procesie kompilacji. W tym artykule opisano dwie metody, można użyć, aby rozszerzyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] procesu kompilacji:  
  
-   Zastępowanie określonych wstępnie zdefiniowanych obiektów docelowych określonych w *Microsoft.Common.targets*.  
  
-   Zastępowanie właściwości "DependsOn" zdefiniowane w *Microsoft.Common.targets*.  
  
## <a name="override-predefined-targets"></a>Zastąp wstępnie zdefiniowanych obiektów docelowych  
 *Microsoft.Common.targets* plik zawiera zestaw wstępnie zdefiniowanych obiektów docelowych pusty, która jest wywoływana przed i po nim niektóre z najważniejszych elementów docelowych w procesie kompilacji. Na przykład [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wywołania `BeforeBuild` docelowej przed funkcją main `CoreBuild` docelowego i `AfterBuild` docelowe po `CoreBuild` docelowej. Domyślnie pustych elementów docelowych w *Microsoft.Common.targets* nic nie rób, ale ich zachowanie domyślne można przesłonić, definiując elementy docelowe mają w pliku projektu, który importuje *Microsoft.Common.targets*. Zastępowanie wstępnie zdefiniowanych obiektów docelowych, należy skorzystać z [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadań daje większą kontrolę nad procesem kompilacji.  
  
#### <a name="to-override-a-predefined-target"></a>Aby wstępnie zdefiniowany obiekt docelowy zastąpienia  
  
1.  Identyfikowanie wstępnie zdefiniowanego elementu docelowego w *Microsoft.Common.targets* , którą chcesz zastąpić. Znajdują się w tabeli poniżej, aby uzyskać pełną listę obiektów docelowych, które można bezpiecznie zastąpić.  
  
2.  Definiowanie docelowego lub miejsc docelowych, na końcu pliku projektu bezpośrednio przed `</Project>` tagu. Na przykład:  
  
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
  
3.  Tworzenie pliku projektu.  

W poniższej tabeli przedstawiono wszystkie obiekty docelowe w *Microsoft.Common.targets* można bezpiecznie zastąpić.  
  
|Nazwa obiektu docelowego|Opis|  
|-----------------|-----------------|  
|`BeforeCompile`, `AfterCompile`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po zakończeniu kompilacji core. Większość dostosowań są wykonywane tylko w jednym z następujących dwóch elementów docelowych.|  
|`BeforeBuild`, `AfterBuild`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomi się przed lub po wszystko inne w kompilacji. **Uwaga:**  `BeforeBuild` i `AfterBuild` elementy docelowe zostały już zdefiniowane w komentarzach na końcu większość plików projektu, dzięki czemu możesz łatwo dodać zdarzenia przed i po kompilacji do pliku projektu.|  
|`BeforeRebuild`, `AfterRebuild`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po podstawowe odbudować funkcji jest wywoływana. Kolejność wykonywania docelowego w *Microsoft.Common.targets* jest: `BeforeRebuild`, `Clean`, `Build`, a następnie `AfterRebuild`.|  
|`BeforeClean`, `AfterClean`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po podstawowe czysta funkcja jest wywoływana.|  
|`BeforePublish`, `AfterPublish`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po podstawowe publikowanie funkcji jest wywoływana.|  
|`BeforeResolveReference`, `AfterResolveReferences`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po odwołania do zestawów są rozwiązane.|  
|`BeforeResGen`, `AfterResGen`|Zadania, które są wstawiane w jednym z następujących elementów docelowych uruchomienia przed lub po wygenerowaniu zasobów.|  
  
## <a name="override-dependson-properties"></a>Zastąpienie DependsOn właściwości  
 Zastępowanie wstępnie zdefiniowanych obiektów docelowych to prosty sposób rozszerzyć proces kompilacji, ale, ponieważ [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sekwencyjnie, ocenia definicji elementów docelowych nie istnieje sposób, aby zapobiec innego projektu, który importuje projektu z zastępowanie cele już zostały zastąpione. Tak, na przykład ostatniego `AfterBuild` docelowej zdefiniowane w pliku projektu po inne projekty zostały zaimportowane, będzie używany podczas kompilacji.  
  
 Można zabezpieczyć się przed niezamierzonym przesłonięcia elementów docelowych, zastępowanie DependsOn właściwości, które są używane w `DependsOnTargets` atrybutów w całym *Microsoft.Common.targets* pliku. Na przykład `Build` docelowy zawiera `DependsOnTargets` wartość atrybutu `"$(BuildDependsOn)"`. Należy wziąć pod uwagę:  
  
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
  
1.  Identyfikowanie właściwością DependsOn wstępnie zdefiniowanych w *Microsoft.Common.targets* , którą chcesz zastąpić. Zobacz tabelę poniżej lista najczęściej zastąpione DependsOn właściwości.  
  
2.  Zdefiniuj inne wystąpienie, właściwość lub właściwości na końcu pliku projektu. Zawiera właściwości oryginalnej, na przykład `$(BuildDependsOn)`, w nowej właściwości.  
  
3.  Zdefiniuj niestandardowe elementy docelowe, przed lub po definicji właściwości.  
  
4.  Tworzenie pliku projektu.  
  
### <a name="commonly-overridden-dependson-properties"></a>Często zastąpione DependsOn właściwości  
  
|Nazwa właściwości|Opis|  
|-------------------|-----------------|  
|`BuildDependsOn`|Właściwość, aby zastąpić, jeśli chcesz wstawić niestandardowe obiekty docelowe, przed lub po zakończeniu procesu całej kompilacji.|  
|`CleanDependsOn`|Właściwość, aby zastąpić, jeśli chcesz wyczyścić dane wyjściowe z niestandardowego procesu kompilacji.|  
|`CompileDependsOn`|Właściwość, aby zastąpić, jeśli chcesz wstawić niestandardowych procesów przed lub po wykonaniu kroku kompilacji.|  
  
## <a name="see-also"></a>Zobacz także  
 [Integracja z programem Visual Studio](../msbuild/visual-studio-integration-msbuild.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [pliki .targets](../msbuild/msbuild-dot-targets-files.md)