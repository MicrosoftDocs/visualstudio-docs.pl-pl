---
title: Tworzenie wsadowe MSBuild | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633437"
---
# <a name="msbuild-batching"></a>Tworzenie wsadowe programu MSBuild

Program MSBuild ma możliwość dzielenia list elementów na różne kategorie lub partie, na podstawie metadanych elementów i uruchamiania obiektu docelowego lub zadania jednokrotnie przy każdej partii.

## <a name="task-batching"></a>Tworzenie partii zadań

Tworzenie wsadowe zadań pozwala uprościć pliki projektu, zapewniając sposób dzielenia list elementów na różne partie i przekazywanie poszczególnych partii do zadania oddzielnie. Oznacza to, że plik projektu musi mieć tylko jedno zadanie i jego atrybuty, nawet jeśli można wykonać kilka razy.

Należy określić, że program MSBuild ma wykonywać przetwarzanie wsadowe za pomocą zadania przy użyciu notacji%(\<ItemMetaDataName >) w jednym z atrybutów zadania. Poniższy przykład dzieli listę elementów `Example` na partie na podstawie wartości metadanych `Color` elementów i przekazuje poszczególne partie do zadania `MyTask` oddzielnie.

> [!NOTE]
> Jeśli nie odwołujesz się do listy elementów w innym miejscu atrybutów zadania lub nazwa metadanych może być niejednoznaczna, można użyć notacji%(\<obiekt ItemCollection. ItemMetaDataName >), aby w pełni zakwalifikować wartość metadanych elementu do użycia na potrzeby przetwarzania wsadowego.

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

Aby zapoznać się z bardziej szczegółowymi przykładami wsadowymi, zobacz [metadane elementu w partii zadań](../msbuild/item-metadata-in-task-batching.md).

## <a name="target-batching"></a>Przetwarzanie wsadowe docelowe

Program MSBuild sprawdza, czy dane wejściowe i wyjściowe elementu docelowego są aktualne przed uruchomieniem obiektu docelowego. Jeśli dane wejściowe i wyjściowe są aktualne, element docelowy jest pomijany. Jeśli zadanie wewnątrz elementu docelowego używa operacji wsadowych, program MSBuild musi określić, czy dane wejściowe i wyjściowe dla każdej partii elementów są aktualne. W przeciwnym razie obiekt docelowy jest wykonywany za każdym razem, gdy zostanie osiągnięty.

Poniższy przykład pokazuje `Target` element, który zawiera atrybut `Outputs` z notacją%(\<ItemMetaDataName >). Program MSBuild będzie dzielić listę elementów `Example` na partie na podstawie metadanych elementu `Color` i analizować sygnatury czasowe plików wyjściowych dla każdej partii. Jeśli dane wyjściowe z partii nie są aktualne, obiekt docelowy jest uruchamiany. W przeciwnym razie element docelowy zostanie pominięty.

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

Aby uzyskać inny przykład tworzenia wsadowych obiektów docelowych, zobacz [metadane elementu w przetwarzaniu wsadowym](../msbuild/item-metadata-in-target-batching.md).

## <a name="property-functions-using-metadata"></a>Funkcje właściwości korzystające z metadanych

Przetwarzanie wsadowe może być kontrolowane przez funkcje właściwości, które obejmują metadane. Na przykład:

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

używa <xref:System.IO.Path.Combine%2A> do łączenia ścieżki folderu głównego z ścieżką kompilowania elementu.

Funkcje właściwości mogą nie występować w obrębie wartości metadanych. Na przykład:

`%(Compile.FullPath.Substring(0,3))`

nie jest dozwolone.

Aby uzyskać więcej informacji na temat funkcji właściwości, zobacz [funkcje właściwości](../msbuild/property-functions.md).

## <a name="see-also"></a>Zobacz też

- [ItemMetadata —, element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
