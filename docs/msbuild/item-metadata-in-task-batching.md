---
title: Metadane elementu w przetwarzaniu wsadowym | Microsoft Docs
description: Dowiedz się, jak program MSBuild używa metadanych elementu w przetwarzaniu wsadowym zadań do dzielenia list elementów na różne kategorie lub partie i uruchamia zadanie jeden raz z każdą partią.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1675cf43cb9632d4480265f00a377c1f5c530b51
ms.sourcegitcommit: c5f2a142ebf9f00808314f79a4508a82e6df1198
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111395361"
---
# <a name="item-metadata-in-task-batching"></a>Metadane elementu w przetwarzaniu wsadowym zadań

Program MSBuild umożliwia dzielenie list elementów na różne kategorie lub partie na podstawie metadanych elementów i uruchamianie zadania jeden raz z każdą partią. Dokładne zrozumienie elementów przekazywanych do poszczególnych partii może być mylące. W tym temacie omykamy następujące typowe scenariusze, które obejmują przetwarzanie wsadowe.

- Dzielenie listy elementów na partie

- Dzielenie kilku list elementów na partie

- Przetwarzanie wsadowe po jednym elementze na raz

- Filtrowanie list elementów

Aby uzyskać więcej informacji na temat przetwarzania wsadowego przy użyciu programu MSBuild, zobacz [Batching (Przetwarzanie wsadowe).](../msbuild/msbuild-batching.md)

## <a name="divide-an-item-list-into-batches"></a>Dzielenie listy elementów na partie

Przetwarzanie wsadowe umożliwia dzielenie listy elementów na różne partie na podstawie metadanych elementów i oddzielne przekazania każdej partii do zadania. Jest to przydatne w przypadku tworzenia zestawów satelicie.

W poniższym przykładzie pokazano, jak podzielić listę elementów na partie na podstawie metadanych elementu. Lista `ExampColl` elementów jest podzielona na trzy partie na podstawie `Number` metadanych elementu. Obecność atrybutu powiadamia program MSBuild o tym, że należy `%(ExampColl.Number)` wykonać przetwarzanie `Text` wsadowe. Lista elementów jest podzielona na trzy partie na podstawie metadanych, a każda partia jest przekazywana `ExampColl` `Number` oddzielnie do zadania.

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

Zadanie [Komunikat wyświetla](../msbuild/message-task.md) następujące informacje:

`Number: 1 -- Items in ExampColl: Item1;Item4`

`Number: 2 -- Items in ExampColl: Item2;Item5`

`Number: 3 -- Items in ExampColl: Item3;Item6`

## <a name="divide-several-item-lists-into-batches"></a>Dzielenie kilku list elementów na partie

Program MSBuild może dzielić wiele list elementów na partie na podstawie tych samych metadanych. Ułatwia to dzielenie różnych list elementów na partie w celu tworzenia wielu zestawów. Na przykład można mieć listę elementów plików *cs* podzieloną na partię aplikacji i partię zestawu oraz listę elementów z plikami zasobów podzielonymi na partię aplikacji i partię zestawu. Następnie można użyć kompilowania wsadowego, aby przekazać te listy elementów do jednego zadania i skompilować zarówno aplikację, jak i zestaw.

> [!NOTE]
> Jeśli lista elementów przekazywana do zadania nie zawiera żadnych elementów z przywoływanych metadanych, każdy element na liście elementów jest przekazywany do każdej partii.

W poniższym przykładzie pokazano, jak podzielić wiele list elementów na partie na podstawie metadanych elementów. Listy `ExampColl` elementów i są podzielone na trzy `ExampColl2` partie na podstawie `Number` metadanych elementu. Obecność atrybutu powiadamia program MSBuild o tym, że należy `%(Number)` wykonać przetwarzanie `Text` wsadowe. Listy elementów i są podzielone na trzy partie na podstawie metadanych, a każda partia jest przekazywana `ExampColl` `ExampColl2` `Number` oddzielnie do zadania.

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

Zadanie [Komunikat wyświetla](../msbuild/message-task.md) następujące informacje:

`Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`

`Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`

`Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`

## <a name="batch-one-item-at-a-time"></a>Wsadowe po jednym elementze na raz

Przetwarzanie wsadowe można również wykonywać na dobrze znanych metadanych elementów, które są przypisywane do każdego elementu podczas tworzenia. Gwarantuje to, że każdy element w kolekcji będzie miał pewne metadane do użycia na użytek przetwarzania wsadowego. Wartość `Identity` metadanych jest przydatna do dzielenia każdego elementu na liście elementów na oddzielną partię. Aby uzyskać pełną listę metadanych dobrze znanych elementów, zobacz Metadane dobrze [znanego elementu](../msbuild/msbuild-well-known-item-metadata.md).

W poniższym przykładzie pokazano, jak wsadować poszczególne elementy na liście elementów po jednym na raz. Lista elementów jest podzielona na sześć partii, z których każda zawiera jeden element `ExampColl` listy elementów. Obecność atrybutu powiadamia program MSBuild o tym, że należy `%(Identity)` wykonać przetwarzanie `Text` wsadowe.

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

Zadanie [Komunikat wyświetla](../msbuild/message-task.md) następujące informacje:

```output
Identity: 'Item1' -- Items in ExampColl: Item1
Identity: 'Item2' -- Items in ExampColl: Item2
Identity: 'Item3' -- Items in ExampColl: Item3
Identity: 'Item4' -- Items in ExampColl: Item4
Identity: 'Item5' -- Items in ExampColl: Item5
Identity: 'Item6' -- Items in ExampColl: Item6
```

Nie ma `Identity` jednak gwarancji, że będzie unikatowa; jego wartość jest szacowaną końcową wartością `Include` atrybutu. W związku z `Include` tym, jeśli jakiekolwiek atrybuty są używane wielokrotnie, są one grupowane razem. Jak pokazano w poniższym przykładzie, ta technika wymaga, aby atrybuty są `Include` unikatowe dla każdego elementu w grupie. Aby zilustrować ten punkt, rozważ następujący kod:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Item Include="1">
      <M>1</M>
    </Item>
    <Item Include="1">
      <M>2</M>
    </Item>
    <Item Include="2">
      <M>3</M>
    </Item>
  </ItemGroup>

  <Target Name="Batching">
    <Warning Text="@(Item->'%(Identity): %(M)')" Condition=" '%(Identity)' != '' "/>
  </Target>
</Project>
```

Dane wyjściowe pokazują, że pierwsze dwa elementy znajdują się w tej samej partii, ponieważ atrybut jest dla nich `Include` taki sam:

```output
test.proj(15,5): warning : 1: 1;1: 2
test.proj(15,5): warning : 2: 3
```

## <a name="filter-item-lists"></a>Filtrowanie list elementów

Przetwarzanie wsadowe może służyć do odfiltrowania niektórych elementów z listy elementów przed przekazaniem ich do zadania. Na przykład filtrowanie wartości metadanych dobrze znanego elementu umożliwia uruchamianie zadania tylko dla plików `Extension` o określonym rozszerzeniu.

W poniższym przykładzie pokazano, jak podzielić listę elementów na partie na podstawie metadanych elementów, a następnie filtrować te partie, gdy zostaną przekazane do zadania. Lista `ExampColl` elementów jest podzielona na trzy partie na podstawie `Number` metadanych elementu. Atrybut zadania określa, że tylko partie z wartością metadanych `Condition` elementu będą przekazywane do `Number` `2` zadania

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

Zadanie [Komunikat wyświetla](../msbuild/message-task.md) następujące informacje:

```
Items in ExampColl: Item2;Item5
```

## <a name="see-also"></a>Zobacz też

- [Metadane dobrze znanego elementu](../msbuild/msbuild-well-known-item-metadata.md)
- [Item, element (MSBuild)](../msbuild/item-element-msbuild.md)
- [ItemMetadata, element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
