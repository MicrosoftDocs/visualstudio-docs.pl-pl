---
title: Metadane elementu w przetwarzaniu wsadowym Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa metadanych elementu w docelowej partii, aby przeprowadzić analizę zależności na danych wejściowych i wyjściowych dla elementu docelowego kompilacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0436402aa4000841a278497af697985c3a50c812
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904602"
---
# <a name="item-metadata-in-target-batching"></a>Metadane elementu w przetwarzaniu wsadowym obiektów docelowych

Program MSBuild ma możliwość przeprowadzenia analizy zależności w danych wejściowych i wyjściowych docelowej kompilacji. Jeśli okaże się, że dane wejściowe lub wyjściowe elementu docelowego są aktualne, element docelowy zostanie pominięty i kompilacja będzie kontynuowała pracę. `Target` elementy używają `Inputs` atrybutów i, `Outputs` Aby określić elementy do sprawdzenia podczas analizy zależności.

Jeśli obiekt docelowy zawiera zadanie, które używa wsadowych elementów jako danych wejściowych lub wyjściowych, `Target` element obiektu docelowego powinien użyć operacji wsadowych w `Inputs` jego `Outputs` atrybutach lub, aby umożliwić programowi MSBuild pomijanie partii elementów, które są już aktualne.

## <a name="batch-targets"></a>Cele partii

Poniższy przykład zawiera listę elementów o nazwie `Res` , która jest podzielona na dwie partie na podstawie `Culture` metadanych elementu. Każda z tych partii jest przenoszona do `AL` zadania, które tworzy zestaw wyjściowy dla każdej partii. Przy użyciu operacji wsadowych na `Outputs` atrybucie `Target` elementu MSBuild może określić, czy każda z poszczególnych partii jest aktualna przed uruchomieniem obiektu docelowego. Bez używania tworzenia wsadowych obiektów docelowych obie partie elementów byłyby uruchamiane przez zadanie za każdym razem, gdy obiekt docelowy został wykonany.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Res Include="Strings.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Strings.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.jp.resources">
            <Culture>jp</Culture>
        </Res>
    </ItemGroup>

    <Target Name="Build"
        Inputs="@(Res)"
        Outputs="%(Culture)\MyApp.resources.dll">

        <AL Resources="@(Res)"
            TargetType="library"
            OutputAssembly="%(Culture)\MyApp.resources.dll">

    </Target>

</Project>
```

## <a name="see-also"></a>Zobacz także

- [Instrukcje: kompilowanie przyrostowe](../msbuild/how-to-build-incrementally.md)
- [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)
- [Target — element (MSBuild)](../msbuild/target-element-msbuild.md)
- [Metadane elementu w przetwarzaniu wsadowym zadań](../msbuild/item-metadata-in-task-batching.md)
