---
title: 'Instrukcje: kompilowanie przyrostowe | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d2bf2f8a45618e8b1f7540479a02c1a5f91b9bf
ms.sourcegitcommit: b04c603ce73b993d042ebdf7f3722cf4fe2ef7f4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74316480"
---
# <a name="how-to-build-incrementally"></a>Instrukcje: kompilowanie przyrostowe
Podczas kompilowania dużego projektu ważne jest, aby wcześniej skompilowane składniki, które są nadal aktualne, nie zostały odbudowane. Jeśli wszystkie elementy docelowe są tworzone za każdym razem, ukończenie każdej kompilacji potrwa dużo czasu. Aby włączyć Kompilacje przyrostowe (kompilacje, w których tylko te elementy docelowe, które nie zostały skompilowane przed lub celem, które są nieaktualne, są ponownie kompilowane), [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) mogą porównać sygnatury czasowe plików wejściowych z sygnaturami czasowymi plików wyjściowych i określić, czy pominąć, skompilować lub częściowo ponownie skompilować element docelowy. Jednak musi istnieć mapowanie jeden do jednego między danymi wejściowymi i wyjściowymi. Można użyć transformacji, aby umożliwić obiektom docelowym zidentyfikowanie tego bezpośredniego mapowania. Aby uzyskać więcej informacji na temat transformacji, zobacz [transformacje](../msbuild/msbuild-transforms.md).

## <a name="specify-inputs-and-outputs"></a>Określanie danych wejściowych i wyjściowych
Element docelowy można skompilować przyrostowo, jeśli dane wejściowe i wyjściowe są określone w pliku projektu.

#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Aby określić dane wejściowe i wyjściowe dla elementu docelowego

- Użyj `Inputs` i `Outputs` atrybutów elementu `Target`. Na przykład:

  ```xml
  <Target Name="Build"
      Inputs="@(CSFile)"
      Outputs="hello.exe">
  ```

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] można porównać sygnatury czasowe plików wejściowych z sygnaturami czasowymi plików wyjściowych i określić, czy pominąć, skompilować lub częściowo ponownie skompilować element docelowy. W poniższym przykładzie, jeśli dowolny plik na liście elementów `@(CSFile)` jest nowszy niż plik *Hello. exe* , [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] uruchomi obiekt docelowy; w przeciwnym razie zostanie pominięty:

```xml
<Target Name="Build"
    Inputs="@(CSFile)"
    Outputs="hello.exe">

    <Csc
        Sources="@(CSFile)"
        OutputAssembly="hello.exe"/>
</Target>
```

Gdy dane wejściowe i wyjściowe są określone w elemencie docelowym, wszystkie dane wyjściowe można mapować tylko na jedną wartość wejściową lub nie może istnieć bezpośrednie mapowanie między wyjściem i danymi wejściowymi. W poprzednim [zadaniu CSC](../msbuild/csc-task.md), na przykład danych wyjściowych, *Hello. exe*, nie można zamapować na żadne pojedyncze dane wejściowe — zależy to od wszystkich z nich.

> [!NOTE]
> Obiekt docelowy, w którym nie istnieje bezpośrednie mapowanie między danymi wejściowymi i wyjściowymi, zawsze kompiluje się częściej niż obiekt docelowy, w którym każde dane wyjściowe można mapować tylko na jedno wejście, ponieważ [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nie może określić, które wyjścia muszą zostać odbudowane, jeśli niektóre dane wejściowe uległy zmianie.

Zadania, w których można zidentyfikować bezpośrednie mapowanie między wynikami i danymi wejściowymi, takie jak [zadanie LC](../msbuild/lc-task.md), są najbardziej odpowiednie dla kompilacji przyrostowych, w przeciwieństwie do zadań, takich jak [CSC](../msbuild/csc-task.md) i [VBC](../msbuild/vbc-task.md), które tworzą jeden zestaw wyjściowy z wielu danych wejściowych.

## <a name="example"></a>Przykład
W poniższym przykładzie używa się projektu, który kompiluje pliki pomocy dla hipotetycznego systemu pomocy. Projekt działa przez konwertowanie źródłowych plików *txt* na pośrednie pliki *zawartości* , które następnie są łączone z plikami metadanych XML w celu utworzenia końcowego pliku *pomocy* używanego przez system pomocy. Projekt używa następujących hipotetycznych zadań:

- `GenerateContentFiles`: konwertuje pliki *txt* na pliki *. Content* .

- `BuildHelp`: łączy pliki *zawartości* i pliki metadanych XML, aby skompilować końcowy plik *pomocy* .

Projekt używa transformacji, aby utworzyć mapowanie jeden do jednego między danymi wejściowymi i wyjściowymi w ramach zadania `GenerateContentFiles`. Aby uzyskać więcej informacji, zobacz [transformacje](../msbuild/msbuild-transforms.md). Ponadto element `Output` jest ustawiony tak, aby automatycznie używał danych wyjściowych z zadania `GenerateContentFiles` jako dane wejściowe dla zadania `BuildHelp`.

Ten plik projektu zawiera zarówno elementy docelowe `Convert`, jak i `Build`. `GenerateContentFiles` i `BuildHelp` zadania są umieszczane odpowiednio w `Convert` i `Build` elementów docelowych, dzięki czemu każdy obiekt docelowy może być zbudowany przyrostowo. Za pomocą elementu `Output` dane wyjściowe zadania `GenerateContentFiles` są umieszczane na liście `ContentFile` elementów, gdzie mogą być używane jako dane wejściowe dla zadania `BuildHelp`. Użycie elementu `Output` w ten sposób automatycznie udostępnia dane wyjściowe z jednego zadania jako dane wejściowe dla innego zadania, dzięki czemu nie trzeba ręcznie wyświetlać poszczególnych elementów lub list elementów w każdym zadaniu.

> [!NOTE]
> Chociaż element docelowy `GenerateContentFiles` może kompilować przyrostowo, wszystkie dane wyjściowe z tego obiektu docelowego zawsze są wymagane jako wejścia dla elementu docelowego `BuildHelp`. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] automatycznie udostępnia wszystkie dane wyjściowe z jednego obiektu docelowego jako dane wejściowe dla innego obiektu docelowego przy użyciu elementu `Output`.

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

## <a name="see-also"></a>Zobacz także
- [Docelowe elementy](../msbuild/msbuild-targets.md)
- [Target — element (MSBuild)](../msbuild/target-element-msbuild.md)
- [Przekształcenia](../msbuild/msbuild-transforms.md)
- [CSC — zadanie](../msbuild/csc-task.md)
- [VBC, zadanie](../msbuild/vbc-task.md)
