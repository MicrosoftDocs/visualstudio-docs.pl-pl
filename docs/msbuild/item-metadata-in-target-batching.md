---
title: Metadane elementu w przetwarzaniu wsadowym Microsoft Docs
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
ms.openlocfilehash: 013cf211fe9fdfb8fef07c5ac757fa5f4b35a521
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75577281"
---
# <a name="item-metadata-in-target-batching"></a>Metadane elementu w partii docelowej
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ma możliwość przeprowadzenia analizy zależności w danych wejściowych i wyjściowych docelowej kompilacji. Jeśli okaże się, że dane wejściowe lub wyjściowe elementu docelowego są aktualne, element docelowy zostanie pominięty i kompilacja będzie kontynuowała pracę. `Target` elementy używają atrybutów `Inputs` i `Outputs`, aby określić elementy do sprawdzenia podczas analizy zależności.

Jeśli obiekt docelowy zawiera zadanie, które używa wsadowych elementów jako danych wejściowych lub wyjściowych, element `Target` obiektu docelowego powinien użyć operacji wsadowych w `Inputs` lub `Outputs` atrybutów, aby umożliwić [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pomijanie partii elementów, które są już aktualne.

## <a name="batch-targets"></a>Cele partii
Poniższy przykład zawiera listę elementów o nazwie `Res`, która jest podzielona na dwie partie na podstawie metadanych elementu `Culture`. Każda z tych partii jest przenoszona do zadania `AL`, które tworzy zestaw wyjściowy dla każdej partii. Za pomocą tworzenia pakietów wsadowych w atrybucie `Outputs` elementu `Target`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] może określić, czy każda z poszczególnych partii jest aktualna przed uruchomieniem obiektu docelowego. Bez używania tworzenia wsadowych obiektów docelowych obie partie elementów byłyby uruchamiane przez zadanie za każdym razem, gdy obiekt docelowy został wykonany.

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
