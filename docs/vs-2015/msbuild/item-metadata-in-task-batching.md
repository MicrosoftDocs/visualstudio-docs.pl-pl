---
title: Element metadanych w przetwarzaniu wsadowym zadań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c83f499560bf747843fe74ede4d2187a544bee8b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769170"
---
# <a name="item-metadata-in-task-batching"></a>Metadane elementu w przetwarzaniu wsadowym zadań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ma możliwość podzielić listy elementów na różnych kategorii lub serii, na podstawie metadanych elementu i uruchomić zadanie jeden raz z każdej partii. Może być mylące zrozumieć, dokładnie jakie elementy są przekazywany przy użyciu której usługi batch. W tym temacie omówiono następujące typowe scenariusze, które obejmują przetwarzanie wsadowe.  
  
- Podział listy elementów w partie  
  
- Dzielenie kilka list elementów na partie  
  
- Przetwarzanie wsadowe jeden element w czasie  
  
- Filtrowanie listy elementów  
  
  Więcej informacji na temat przetwarzania wsadowego za pomocą [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], zobacz [przetwarzania wsadowego](../msbuild/msbuild-batching.md).  
  
## <a name="dividing-an-item-list-into-batches"></a>Podział listy elementów w partie  
 Przetwarzanie wsadowe umożliwia podzielić listy elementów na różnych partii na podstawie metadanych elementu i przekazać każdej partii w zadanie oddzielnie. Jest to przydatne do tworzenia zestawów satelickich.  
  
 Poniższy przykład pokazuje, jak podzielić listy elementów na partie na podstawie metadanych elementu. `ExampColl` Listy elementów jest podzielony na trzy partie na podstawie `Number` metadanych elementu. Obecność `%(ExampColl.Number)`w `Text` powiadamia atrybutu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , należy wykonać przetwarzanie wsadowe. `ExampColl` Listy elementów jest podzielony na trzy partie na podstawie `Number` metadanych i każdej partii jest przekazywana oddzielnie do zadania.  
  
```  
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
  
 [Komunikat — zadanie](../msbuild/message-task.md) zadania są wyświetlane następujące informacje:  
  
 `Number: 1 -- Items in ExampColl: Item1;Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2;Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3;Item6`  
  
## <a name="dividing-several-item-lists-into-batches"></a>Podzielenie kilka elementów listy w partie  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] można podzielić wiele list elementów na partie na podstawie tych samych metadanych. Dzięki temu można łatwo podzielić listy różnych elementów partii do tworzenia wielu zestawów. Na przykład można mieć listy elementów pliku .cs podzielony na aplikacji i usługi batch i batch zestawu, listy elementów plików zasobów, które dzielą aplikacji usługi batch i batch zestawu. Przetwarzanie wsadowe można następnie użyć do przekazać te listy elementów do jednego zadania i tworzenie aplikacji i zestawu.  
  
> [!NOTE]
>  Jeśli lista elementów, które są przekazywane do zadania nie zawiera elementów przy użyciu metadanych, której dotyczy odwołanie, każdy element na tej liście elementów jest przekazywany do każdej partii.  
  
 Poniższy przykład pokazuje, jak podzielić wielu listy elementów na partie na podstawie metadanych elementu. `ExampColl` i `ExampColl2` listy elementów każdego dzielą się na trzy partie na podstawie `Number` metadanych elementu. Obecność `%(Number)`w `Text` powiadamia atrybutu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , należy wykonać przetwarzanie wsadowe. `ExampColl` i `ExampColl2` listy elementów są podzielone na trzy partie na podstawie `Number` metadanych i każdej partii jest przekazywana oddzielnie do zadania.  
  
```  
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
  
 [Komunikat — zadanie](../msbuild/message-task.md) zadania są wyświetlane następujące informacje:  
  
 `Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`  
  
## <a name="batching-one-item-at-a-time"></a>Przetwarzanie wsadowe jeden element w czasie  
 Przetwarzanie wsadowe można także wykonać na metadane dobrze znanego elementu, który jest przypisany do każdego elementu przy utworzeniu. Gwarantuje to, że każdy element w kolekcji mają niektóre metadane na potrzeby przetwarzania wsadowego. `Identity` Wartości metadanych jest unikatowy dla każdego elementu i jest przydatne w przypadku dzielenia każdy element na liście elementów do oddzielnej partii. Aby uzyskać pełną listę metadane dobrze znanego elementu, zobacz [metadane dobrze znanego elementu](../msbuild/msbuild-well-known-item-metadata.md).  
  
 Poniższy przykład pokazuje, jak partii każdego elementu na liście elementów, jeden na raz. Ponieważ `Identity` wartość metadanych każdy element jest unikatowa, `ExampColl` listy elementów jest podzielony na partie sześć partie zawierające jeden element listy elementów. Obecność `%(Identity)`w `Text` powiadamia atrybutu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , należy wykonać przetwarzanie wsadowe.  
  
```  
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
            Text = "Identity: "%(Identity)" -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 [Komunikat — zadanie](../msbuild/message-task.md) zadania są wyświetlane następujące informacje:  
  
```  
Identity: "Item1" -- Items in ExampColl: Item1  
Identity: "Item2" -- Items in ExampColl: Item2  
Identity: "Item3" -- Items in ExampColl: Item3  
Identity: "Item4" -- Items in ExampColl: Item4  
Identity: "Item5" -- Items in ExampColl: Item5  
Identity: "Item6" -- Items in ExampColl: Item6  
```  
  
## <a name="filtering-item-lists"></a>Wyświetla listę elementów filtrowania  
 Przetwarzanie wsadowe może służyć do filtrowania niektórych elementów z listy elementów przed przekazaniem go do zadania. Na przykład filtrowanie `Extension` wartość metadane dobrze znanego elementu pozwala na uruchamianie zadania tylko plików z określonym rozszerzeniem.  
  
 Poniższy przykład pokazuje, jak podzielić listy elementów na podstawie metadanych elementu partii, a następnie filtrować te partie, gdy są przekazywane do zadania. `ExampColl` Listy elementów jest podzielony na trzy partie na podstawie `Number` metadanych elementu. `Condition` Atrybut zadanie określa, który tylko partii z `Number` wartość metadanych z elementu `2` zostanie przekazany do zadania  
  
```  
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
  
 [Komunikat — zadanie](../msbuild/message-task.md) zadania są wyświetlane następujące informacje:  
  
```  
Items in ExampColl: Item2;Item5  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Metadane dobrze znanego elementu](../msbuild/msbuild-well-known-item-metadata.md)   
 [Item — Element (MSBuild)](../msbuild/item-element-msbuild.md)   
 [Itemmetadata — Element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)
