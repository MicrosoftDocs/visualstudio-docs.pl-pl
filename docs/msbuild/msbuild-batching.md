---
title: MSBuild Wsadowanie | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78aeef8ea651aac1fe2a780207474399f4bbcf09
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633437"
---
# <a name="msbuild-batching"></a>Wsadowanie MSBuild

MSBuild ma możliwość dzielenia list elementów na różne kategorie lub partii, na podstawie metadanych elementu i uruchamiania obiektu docelowego lub zadania jeden raz z każdej partii.

## <a name="task-batching"></a>Przetwarzanie zadań

Przetwarzanie zadań umożliwia uproszczenie plików projektu, zapewniając sposób dzielenia list towarów na różne partie i przekazywania każdej z tych partii do zadania oddzielnie. Oznacza to, że plik projektu musi mieć tylko zadanie i jego atrybuty zadeklarowane raz, nawet jeśli można go uruchomić kilka razy.

Można określić, że program MSBuild ma wykonywać przetwarzanie\<wsadowe z zadaniem przy użyciu notacji %( ItemMetaDataName>) w jednym z atrybutów zadania. Poniższy przykład dzieli `Example` listę towarów na partie `Color` na podstawie wartości metadanych elementu i `MyTask` przekazuje każdą z partii do zadania oddzielnie.

> [!NOTE]
> Jeśli lista elementów nie odwołuje się do niej gdzie indziej w atrybutach zadań lub nazwa\<metadanych może być niejednoznaczna, można użyć notacji %( ItemCollection.ItemMetaDataName>), aby w pełni zakwalifikować wartość metadanych elementu do użycia w przypadku przetwarzania wsadowego.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Aby uzyskać bardziej szczegółowe przykłady przetwarzania wsadowego, zobacz [Metadane elementu w wsadowaniu zadań](../msbuild/item-metadata-in-task-batching.md).

## <a name="target-batching"></a>Wsadowanie docelowe

MSBuild sprawdza, czy dane wejściowe i wyjściowe obiektu docelowego są aktualne przed uruchomieniu obiektu docelowego. Jeśli zarówno dane wejściowe, jak i wyjściowe są aktualne, obiekt docelowy jest pomijany. Jeśli zadanie wewnątrz obiektu docelowego używa przetwarzania wsadowego, MSBuild musi określić, czy dane wejściowe i wyjściowe dla każdej partii towarów jest aktualny. W przeciwnym razie cel jest wykonywany za każdym razem, gdy zostanie trafiony.

W poniższym `Target` przykładzie pokazano `Outputs` element zawierający\<atrybut z notacją %( ItemMetaDataName>). MSBuild podzieli `Example` listę elementów na `Color` partie na podstawie metadanych elementu i analizować sygnatury czasowe plików wyjściowych dla każdej partii. Jeśli dane wyjściowe z partii nie są aktualne, obiekt docelowy jest uruchamiany. W przeciwnym razie obiekt docelowy zostanie pominięty.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask"
        Inputs="@(Example)"
        Outputs="%(Color)\MyFile.txt">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Inny przykład wsadowania docelowego można znaleźć [w dokumencie dozowania docelowego.](../msbuild/item-metadata-in-target-batching.md)

## <a name="property-functions-using-metadata"></a>Funkcje właściwości przy użyciu metadanych

Przetwarzanie wsadowe może być kontrolowane przez funkcje właściwości, które zawierają metadane. Na przykład:

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

służy <xref:System.IO.Path.Combine%2A> do łączenia ścieżki folderu głównego ze ścieżką elementu kompilacji.

Funkcje właściwości mogą nie być wyświetlane w obrębie wartości metadanych. Na przykład:

`%(Compile.FullPath.Substring(0,3))`

jest niedozwolona.

Aby uzyskać więcej informacji na temat funkcji właściwości, zobacz [Funkcje właściwości](../msbuild/property-functions.md).

## <a name="see-also"></a>Zobacz też

- [ItemMetadata element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
