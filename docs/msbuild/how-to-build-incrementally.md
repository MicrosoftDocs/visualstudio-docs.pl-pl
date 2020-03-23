---
title: 'Jak: Budować przyrostowo | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4911bb131f5c5c878b82865b3dee61fd7bedbe1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634165"
---
# <a name="how-to-build-incrementally"></a>Jak: Tworzenie przyrostowo

Podczas tworzenia dużego projektu, ważne jest, że wcześniej utworzone składniki, które są nadal aktualne nie są przebudowywane. Jeśli wszystkie obiekty docelowe są budowane za każdym razem, każda kompilacja zajmie dużo czasu. Aby włączyć kompilacje przyrostowe (kompilacje, w których tylko te obiekty docelowe, które nie zostały zbudowane przed lub cele, które są nieaktualne, są przebudowywane), aparat kompilacji firmy Microsoft (MSBuild) można porównać sygnatury czasowe plików wejściowych z sygnaturami czasowymi plików wyjściowych i określić, czy pominąć, zbudować lub częściowo odbudować obiekt docelowy. Jednak musi istnieć mapowanie jeden do jednego między wejściami i wyjściami. Można użyć przekształceń, aby włączyć obiekty docelowe do identyfikowania tego mapowania bezpośredniego. Aby uzyskać więcej informacji na temat przekształceń, zobacz [Przekształcenia](../msbuild/msbuild-transforms.md).

## <a name="specify-inputs-and-outputs"></a>Określanie wejść i wyjść

Obiekt docelowy można budować przyrostowo, jeśli dane wejściowe i wyjściowe są określone w pliku projektu.

#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Aby określić wejścia i wyjścia dla obiektu docelowego

- Użyj `Inputs` i `Outputs` atrybuty `Target` elementu. Przykład:

  ```xml
  <Target Name="Build"
      Inputs="@(CSFile)"
      Outputs="hello.exe">
  ```

MSBuild można porównać sygnatury czasowe plików wejściowych z sygnatury czasowe plików wyjściowych i określić, czy pominąć, skompilować lub częściowo odbudować miejsce docelowe. W poniższym przykładzie, jeśli `@(CSFile)` dowolny plik na liście elementów jest nowszy niż plik *hello.exe,* MSBuild uruchomi obiekt docelowy; w przeciwnym razie zostanie pominięty:

```xml
<Target Name="Build"
    Inputs="@(CSFile)"
    Outputs="hello.exe">

    <Csc
        Sources="@(CSFile)"
        OutputAssembly="hello.exe"/>
</Target>
```

Gdy wejścia i wyjścia są określone w docelowych, każde wyjście można mapować tylko do jednego wejścia lub nie może być bezpośrednie mapowanie między wyjściami i wejściami. W poprzednim [zadaniu Csc](../msbuild/csc-task.md), na przykład, wyjście, *hello.exe*, nie może być mapowane na żadne pojedyncze dane wejściowe - to zależy od wszystkich z nich.

> [!NOTE]
> Obiekt docelowy, w którym nie ma bezpośredniego mapowania między wejściami i wyjściami zawsze będzie kompilacji częściej niż miejsce docelowe, w którym każdy wynik można mapować tylko do jednego wejścia, ponieważ MSBuild nie można określić, które dane wyjściowe muszą zostać przebudowane, jeśli niektóre dane wejściowe uległy zmianie.

Zadania, w których można zidentyfikować bezpośrednie mapowanie między wyjściami i wejściami, takie jak [zadanie LC,](../msbuild/lc-task.md)są najbardziej odpowiednie dla kompilacji przyrostowych, w przeciwieństwie do zadań takich jak [Csc](../msbuild/csc-task.md) i [Vbc](../msbuild/vbc-task.md), które generują jeden zestaw wyjściowy z wielu wejść.

## <a name="example"></a>Przykład

W poniższym przykładzie użyto projektu, który tworzy pliki Pomocy dla hipotetycznego systemu Pomocy. Projekt polega na konwersji źródłowych plików *.txt* na pośrednie pliki *.content,* które następnie są łączone z plikami metadanych XML w celu uzyskania ostatecznego pliku *pomocy* używanego przez system Pomocy. W projekcie wykorzystuje się następujące hipotetyczne zadania:

- `GenerateContentFiles`: Konwertuje pliki *txt* na pliki *.content.*

- `BuildHelp`: Łączy pliki *.content* i pliki metadanych XML w celu utworzenia ostatecznego pliku *pomocy.*

Projekt używa przekształceń do utworzenia mapowania jeden do jednego między `GenerateContentFiles` wejściami i wyjściami w zadaniu. Aby uzyskać więcej informacji, zobacz [Przekształcenia](../msbuild/msbuild-transforms.md). Ponadto `Output` element jest ustawiony na automatyczne używanie wyjść `GenerateContentFiles` z zadania jako `BuildHelp` danych wejściowych dla zadania.

Ten plik projektu `Convert` zawiera `Build` zarówno obiekty docelowe, jak i obiekty docelowe. I `GenerateContentFiles` `BuildHelp` zadania są umieszczane w `Convert` i `Build` cele odpowiednio tak, że każdy cel może być zbudowany przyrostowo. Za pomocą `Output` elementu, dane wyjściowe `GenerateContentFiles` zadania są `ContentFile` umieszczane na liście elementów, gdzie `BuildHelp` mogą być używane jako dane wejściowe dla zadania. Za `Output` pomocą elementu w ten sposób automatycznie zapewnia dane wyjściowe z jednego zadania jako dane wejściowe dla innego zadania, dzięki czemu nie trzeba ręcznie listy poszczególnych elementów lub elementów list w każdym zadaniu.

> [!NOTE]
> Mimo `GenerateContentFiles` że obiekt docelowy można tworzyć przyrostowo, wszystkie dane wyjściowe z `BuildHelp` tego obiektu docelowego zawsze są wymagane jako dane wejściowe dla obiektu docelowego. MSBuild automatycznie udostępnia wszystkie dane wyjściowe z jednego obiektu docelowego `Output` jako dane wejściowe dla innego obiektu docelowego podczas korzystania z elementu.

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <ItemGroup>
        <TXTFile Include="*.txt"/>
        <XMLFiles Include="\metadata\*.xml"/>
    </ItemGroup>

    <Target Name = "Convert"
        Inputs="@(TXTFile)"
        Outputs="@(TXTFile->'%(Filename).content')">

        <GenerateContentFiles
            Sources = "@(TXTFile)">
            <Output TaskParameter = "OutputContentFiles"
                ItemName = "ContentFiles"/>
        </GenerateContentFiles>
    </Target>

    <Target Name = "Build" DependsOnTargets = "Convert"
        Inputs="@(ContentFiles);@(XMLFiles)"
        Outputs="$(MSBuildProjectName).help">

        <BuildHelp
            ContentFiles = "@(ContentFiles)"
            MetadataFiles = "@(XMLFiles)"
            OutputFileName = "$(MSBuildProjectName).help"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Cele](../msbuild/msbuild-targets.md)
- [Element docelowy (MSBuild)](../msbuild/target-element-msbuild.md)
- [Przekształcenia](../msbuild/msbuild-transforms.md)
- [Zadanie csc](../msbuild/csc-task.md)
- [Zadanie Vbc](../msbuild/vbc-task.md)
