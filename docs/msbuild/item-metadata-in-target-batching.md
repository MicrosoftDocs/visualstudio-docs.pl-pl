---
title: Metadane elementu w docelowym wsadowaniu | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 83a5d0c9dec280633d0a39573581c083e6ddd4d8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633671"
---
# <a name="item-metadata-in-target-batching"></a>Metadane elementu w docelowym wsadowaniu

MSBuild ma możliwość wykonywania analizy zależności na dane wejściowe i wyjściowe obiektu docelowego kompilacji. Jeśli zostanie ustalone, że dane wejściowe lub wyjściowe obiektu docelowego są aktualne, obiekt docelowy zostanie pominięty i kompilacja będzie kontynuowana. `Target`elementy używają `Inputs` `Outputs` i atrybuty, aby określić elementy do inspekcji podczas analizy zależności.

Jeśli obiekt docelowy zawiera zadanie, które używa wsadowych `Target` towarów jako dane wejściowe lub `Inputs` `Outputs` wyjściowe, element obiektu docelowego należy użyć przetwarzania wsadowego w jego lub atrybutów, aby umożliwić MSBuild pominąć partie elementów, które są już aktualne.

## <a name="batch-targets"></a>Obiekty docelowe partii

Poniższy przykład zawiera listę `Res` elementów o nazwie, która `Culture` jest podzielona na dwie partie na podstawie metadanych elementu. Każda z tych partii jest `AL` przekazywana do zadania, co tworzy zestaw wyjściowy dla każdej partii. Za pomocą przetwarzania `Outputs` wsadowego `Target` na atrybut elementu, MSBuild można określić, czy każda z poszczególnych partii jest aktualna przed uruchomieniem obiektu docelowego. Bez użycia docelowego wsadowania obie partie towarów będą uruchamiane przez zadanie za każdym razem, gdy obiekt docelowy został wykonany.

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

## <a name="see-also"></a>Zobacz też

- [Jak: Tworzenie przyrostowo](../msbuild/how-to-build-incrementally.md)
- [Tworzenie partii](../msbuild/msbuild-batching.md)
- [Element docelowy (MSBuild)](../msbuild/target-element-msbuild.md)
- [Metadane elementu w partii zadań](../msbuild/item-metadata-in-task-batching.md)
