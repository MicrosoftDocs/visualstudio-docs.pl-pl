---
title: Metadane elementu w partii zadań | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92613b96d5d85a959e3426df86168c7110b74fed
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633658"
---
# <a name="item-metadata-in-task-batching"></a>Metadane elementu w partii zadań

MSBuild ma możliwość dzielenia list elementów na różne kategorie lub partii, na podstawie metadanych elementu i uruchamiania zadania jeden raz z każdej partii. Może to być mylące, aby zrozumieć dokładnie, jakie elementy są przekazywane z której partii. W tym temacie opisano następujące typowe scenariusze, które obejmują przetwarzanie wsadowe.

- Dzielenie listy towarów na partie

- Dzielenie kilku list towarów na partie

- Przetwarzanie wsadowe po jednym elemencie naraz

- Filtrowanie list elementów

Aby uzyskać więcej informacji na temat przetwarzania wsadowego za pomocą msbuild, zobacz [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md).

## <a name="divide-an-item-list-into-batches"></a>Dzielenie listy towarów na partie

Przetwarzanie wsadowe umożliwia dzielenie listy towarów na różne partie na podstawie metadanych elementu i przekazywanie każdej partii do zadania oddzielnie. Jest to przydatne do tworzenia zestawów satelitarnych.

W poniższym przykładzie pokazano, jak podzielić listę elementów na partie na podstawie metadanych elementu. Lista `ExampColl` elementów jest podzielona na trzy `Number` partie na podstawie metadanych elementu. Obecność `%(ExampColl.Number)`w atrybucie `Text` powiadamia MSBuild, że należy wykonać przetwarzanie wsadowe. Lista `ExampColl` elementów jest podzielona na trzy `Number` partie na podstawie metadanych, a każda partia jest przekazywana oddzielnie do zadania.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>
        <ExampColl Include="Item4">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item5">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item6">
            <Number>3</Number>
        </ExampColl>
    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Number: %(ExampColl.Number) -- Items in ExampColl: @(ExampColl)"/>
    </Target>

</Project>
```

Zadanie [Wiadomość](../msbuild/message-task.md) wyświetla następujące informacje:

`Number: 1 -- Items in ExampColl: Item1;Item4`

`Number: 2 -- Items in ExampColl: Item2;Item5`

`Number: 3 -- Items in ExampColl: Item3;Item6`

## <a name="divide-several-item-lists-into-batches"></a>Dzielenie kilku list towarów na partie

MSBuild może podzielić wiele list elementów na partie na podstawie tych samych metadanych. Ułatwia to dzielenie różnych list towarów na partie do tworzenia wielu zestawów. Na przykład może mieć listę elementów plików *.cs* podzieloną na partię aplikacji i partię zestawu oraz listę zapasów plików zasobów podzielonych na partię aplikacji i partię zestawu. Następnie można użyć przetwarzania wsadowego, aby przekazać te listy elementów do jednego zadania i skompilować zarówno aplikację, jak i zestaw.

> [!NOTE]
> Jeśli lista elementów przekazywanych do zadania nie zawiera żadnych elementów z metadanymi, do których istnieje odwołanie, każdy element na tej liście elementów jest przekazywany do każdej partii.

W poniższym przykładzie pokazano, jak podzielić listę wielu elementów na partie na podstawie metadanych elementu. Listy `ExampColl` `ExampColl2` i towary są podzielone na trzy `Number` partie na podstawie metadanych elementu. Obecność `%(Number)`w atrybucie `Text` powiadamia MSBuild, że należy wykonać przetwarzanie wsadowe. Listy `ExampColl` `ExampColl2` i towary są podzielone na trzy `Number` partie na podstawie metadanych, a każda partia jest przekazywana oddzielnie do zadania.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>

        <ExampColl2 Include="Item4">
            <Number>1</Number>
        </ExampColl2>
        <ExampColl2 Include="Item5">
            <Number>2</Number>
        </ExampColl2>
        <ExampColl2 Include="Item6">
            <Number>3</Number>
        </ExampColl2>

    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Number: %(Number) -- Items in ExampColl: @(ExampColl) ExampColl2: @(ExampColl2)"/>
    </Target>

</Project>
```

Zadanie [Wiadomość](../msbuild/message-task.md) wyświetla następujące informacje:

`Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`

`Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`

`Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`

## <a name="batch-one-item-at-a-time"></a>Wsad po jednym elemencie naraz

Przetwarzanie wsadowe można również wykonać na dobrze znanych metadanych elementu, który jest przypisany do każdego elementu podczas tworzenia. Gwarantuje to, że każdy element w kolekcji będzie miał niektóre metadane do użycia do przetwarzania wsadowego. Wartość `Identity` metadanych jest unikatowa dla każdego elementu i jest przydatna do dzielenia każdego elementu na liście elementów na osobną partię. Aby uzyskać pełną listę dobrze znanych metadanych elementu, zobacz [Znane metadane elementu](../msbuild/msbuild-well-known-item-metadata.md).

W poniższym przykładzie pokazano, jak partii każdego towaru na liście towarów po jednym na raz. Ponieważ `Identity` wartość metadanych każdego elementu `ExampColl` jest unikatowa, lista elementów jest podzielona na sześć partii, z których każda zawiera jeden element listy elementów. Obecność `%(Identity)`w atrybucie `Text` powiadamia MSBuild, że należy wykonać przetwarzanie wsadowe.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1"/>
        <ExampColl Include="Item2"/>
        <ExampColl Include="Item3"/>
        <ExampColl Include="Item4"/>
        <ExampColl Include="Item5"/>
        <ExampColl Include="Item6"/>

    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Identity: '%(Identity)' -- Items in ExampColl: @(ExampColl)"/>
    </Target>

</Project>
```

Zadanie [Wiadomość](../msbuild/message-task.md) wyświetla następujące informacje:

```output
Identity: 'Item1' -- Items in ExampColl: Item1
Identity: 'Item2' -- Items in ExampColl: Item2
Identity: 'Item3' -- Items in ExampColl: Item3
Identity: 'Item4' -- Items in ExampColl: Item4
Identity: 'Item5' -- Items in ExampColl: Item5
Identity: 'Item6' -- Items in ExampColl: Item6
```

## <a name="filter-item-lists"></a>Listy elementów filtrowania

Przetwarzanie wsadowe może służyć do filtrowania niektórych elementów z listy elementów przed przekazaniem go do zadania. Na przykład filtrowanie `Extension` wartości metadanych dobrze znanego elementu umożliwia uruchamianie zadania tylko dla plików z określonym rozszerzeniem.

W poniższym przykładzie pokazano, jak podzielić listę elementów na partie na podstawie metadanych elementu, a następnie filtrować te partie, gdy są przekazywane do zadania. Lista `ExampColl` elementów jest podzielona na trzy `Number` partie na podstawie metadanych elementu. Atrybut `Condition` zadania określa, że do zadania będą `Number` przekazywane tylko `2` partie o wartości metadanych elementu.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>
        <ExampColl Include="Item4">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item5">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item6">
            <Number>3</Number>
        </ExampColl>

    </ItemGroup>

    <Target Name="Exec">
        <Message
            Text = "Items in ExampColl: @(ExampColl)"
            Condition="'%(Number)'=='2'"/>
    </Target>

</Project>
```

Zadanie [Wiadomość](../msbuild/message-task.md) wyświetla następujące informacje:

```
Items in ExampColl: Item2;Item5
```

## <a name="see-also"></a>Zobacz też

- [Dobrze znane metadane elementu](../msbuild/msbuild-well-known-item-metadata.md)
- [Element elementu (MSBuild)](../msbuild/item-element-msbuild.md)
- [ItemMetadata element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Tworzenie partii](../msbuild/msbuild-batching.md)
- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
